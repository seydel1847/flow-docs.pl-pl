---
title: "Używanie elementów webhook z usługą Microsoft Flow | Microsoft Docs"
description: "Informacje o sposobie tworzenia przepływów, które współdziałają z elementami webhook w usłudze Microsoft Flow"
services: 
suite: flow
documentationcenter: 
author: msftman
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/08/2017
ms.author: deonhe
ms.openlocfilehash: cf899063ed6244e85d7eb0759efc9421cbdaa327
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2018
---
# <a name="use-webhooks-with-microsoft-flow"></a>Używanie elementów webhook z usługą Microsoft Flow
[Elementy webhook](http://www.webhooks.org/) to proste wywołania zwrotne HTTP używane do udostępniania powiadomień o zdarzeniach.  Usługa Microsoft Flow umożliwia wyzwalanie przepływów przy użyciu elementów webhook.  W tym samouczku pokazano, jak utworzyć przepływ wyzwalany przez element webhook.

> [!NOTE]
> Jako przykładowej usługi umożliwiającej wysyłanie powiadomień za pośrednictwem elementów webhook użyjemy usługi GitHub, ale techniki przedstawione w tym artykule mogą obejmować dowolną usługę korzystającą z elementów webhook.
> 
> 

## <a name="prerequisites"></a>Wymagania wstępne
W celu wykonania kroków tego samouczka niezbędne jest spełnienie następujących wymagań:

* Podstawowa wiedza na temat [elementów webhook](http://www.webhooks.org/).
* Podstawowa wiedza na temat [specyfikacji OpenAPI](http://swagger.io/specification/) (struktury Swagger).
* Konto usługi [GitHub](https://www.github.com).
* [Przykładowy plik JSON w standardzie OpenAPI](https://pwrappssamples.blob.core.windows.net/samples/githubWebhookSample.json) używany w tym samouczku.
* Możesz także użyć [interfejsu użytkownika](customapi-webhooks.md#creating-webhook-triggers-from-the-ui) w celu zdefiniowania wyzwalaczy elementu webhook, jeśli nie chcesz ręcznie tworzyć pliku OpenAPI.

## <a name="the-openapi-file"></a>Plik OpenAPI
Elementy webhook są implementowane w usłudze Microsoft Flow jako typ [łącznika niestandardowego](register-custom-api.md), dlatego w celu określenia postaci elementu webhook należy udostępnić plik JSON w standardzie OpenAPI.  Plik OpenAPI zawiera trzy definicje, które mają kluczowe znaczenie dla działania elementu webhook:

1. Tworzenie elementu webhook
2. Definiowanie żądania punktu zaczepienia przychodzącego z interfejsu API (w tym przypadku usługi GitHub)
3. Usuwanie elementu webhook

### <a name="creating-the-webhook"></a>Tworzenie elementu webhook
Po stronie usługi GitHub element webhook jest tworzony przez żądanie POST protokołu HTTP wysyłane na adres `/repos/{owner}/{repo}/hooks`.  W przypadku utworzenia nowego przepływu przy użyciu wyzwalacza zdefiniowanego w pliku OpenAPI lub przy każdej modyfikacji wyzwalacza usługa Microsoft Flow musi wykonać operację POST za pomocą tego adresu URL.  W poniższym przykładzie właściwość `post` zawiera schemat żądania, które zostanie opublikowane w usłudze GitHub.

```json
"/repos/{owner}/{repo}/hooks": {
    "x-ms-notification-content": {
    "description": "Details for Webhook",
    "schema": {
        "$ref": "#/definitions/WebhookPushResponse"
    }
    },
    "post": {
    "description": "Creates a Github webhook",
    "summary": "Triggers when a PUSH event occurs",
    "operationId": "webhook-trigger",
    "x-ms-trigger": "single",
    "parameters": [
        {
        "name": "owner",
        "in": "path",
        "description": "Name of the owner of targetted repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "repo",
        "in": "path",
        "description": "Name of the repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "Request body of webhook",
        "in": "body",
        "description": "This is the request body of the Webhook",
        "schema": {
            "$ref": "#/definitions/WebhookRequestBody"
        }
        }
    ],
    "responses": {
        "201": {
        "description": "Created",
        "schema": {
            "$ref": "#/definitions/WebhookCreationResponse"
        }
        }
    }
    }
},
```

> [!IMPORTANT]
> Należy dołączyć właściwość `"x-ms-trigger": "single"`, która jest rozszerzeniem schematu nakazującym usłudze Microsoft Flow wyświetlenie tego elementu webhook na liście dostępnych wyzwalaczy w projektancie przepływu.
> 
> 

### <a name="defining-the-incoming-hook-request-from-the-api"></a>Definiowanie żądania punktu zaczepienia przychodzącego z interfejsu API
Postać przychodzącego żądania punktu zaczepienia (powiadomienia wysyłanego z usługi GitHub do usługi Microsoft Flow) została zdefiniowana we właściwości niestandardowej `x-ms-notification-content`, jak pokazano w powyższym przykładzie.  Nie musi on zawierać całego żądania, a tylko te części, które mają być używane w przepływach.

### <a name="deleting-the-webhook"></a>Usuwanie elementu webhook
Bardzo ważne jest dołączenie do pliku OpenAPI definicji zawierającej instrukcję usuwania elementu webhook przez usługę Microsoft Flow.  Usługa Microsoft Flow podejmie próbę usunięcia elementu webhook przy każdej aktualizacji wyzwalacza w przepływie lub po usunięciu przepływu.

```json
"/repos/{owner}/{repo}/hooks/{hook_Id}": {
    "delete": {
    "description": "Deletes a Github webhook",
    "operationId": "DeleteTrigger",
    "parameters": [
        {
        "name": "owner",
        "in": "path",
        "description": "Name of the owner of targetted repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "repo",
        "in": "path",
        "description": "Name of the repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "hook_Id",
        "in": "path",
        "description": "ID of the Hook being deleted",
        "required": true,
        "type": "string"
        }
    ]
    }
},
```

> [!IMPORTANT]
> Aby usługa Microsoft Flow mogła usunąć element webhook, podczas jego tworzenia interfejs API **musi** dołączyć nagłówek HTTP `Location` do odpowiedzi 201.  Nagłówek `Location` powinien zawierać ścieżkę do elementu webhook używanego przez żądanie DELETE protokołu HTTP.  Na przykład nagłówek `Location` dołączony do odpowiedzi usługi GitHub ma następujący format: `https://api.github.com/repos/<user name>/<repo name>/hooks/<hook ID>`.
> 
> 

## <a name="authentication"></a>Uwierzytelnianie
Interfejs API, który wysyła żądanie elementu webhook do usługi Microsoft Flow, zazwyczaj obejmuje jakąś formę uwierzytelniania, a usługa GitHub nie jest wyjątkiem pod tym względem.  Obsługiwanych jest kilka typów uwierzytelniania.  W tym samouczku zostaną użyte osobiste tokeny dostępu usługi GitHub.

1. Przejdź do [usługi GitHub](https://www.github.com) i zaloguj się, jeśli jeszcze tego nie zrobiono.
2. W prawym górnym rogu kliknij swój **obraz profilu**, a następnie kliknij pozycję **Settings** (Ustawienia) w menu.
   
    ![Ustawienia](./media/customapi-webhooks/github-settings.png)
3. W menu po lewej stronie w obszarze **Developer settings** (Ustawienia dewelopera) kliknij pozycję **Personal access tokens** (Osobiste tokeny dostępu).
   
    ![Osobiste tokeny dostępu](./media/customapi-webhooks/personal-access-tokens.png)
4. Kliknij przycisk **Generate new token** (Wygeneruj nowy token).
   
    ![Generowanie nowego tokenu](./media/customapi-webhooks/generate-new-token.png)
5. W polu **Token description** (Opis tokenu) wprowadź opis tokenu.
6. Zaznacz pole wyboru **admin:repo_hook**.
   
    ![admin:repo_hook](./media/customapi-webhooks/repo-hook.png)
7. Kliknij przycisk **Generate token** (Wygeneruj token).
8. Zanotuj wygenerowany token.
   
    ![Nowy token](./media/customapi-webhooks/new-token.png)
   
   > [!IMPORTANT]
   > Nie można ponownie uzyskać dostępu do tego tokenu. Należy go skopiować i wkleić np. do Notatnika na potrzeby użycia w kolejnych krokach tego samouczka.
   > 
   > 

## <a name="adding-the-webhook-to-microsoft-flow"></a>Dodawanie elementu webhook do usługi Microsoft Flow
Wykonanie powyższych czynności umożliwi nam dodanie elementu webhook do usługi Microsoft Flow jako łącznika niestandardowego.

1. Przejdź do [portalu usługi Microsoft Flow w sieci Web](https://flow.microsoft.com) i zaloguj się, jeśli jeszcze tego nie zrobiono.
2. Kliknij ikonę **ustawień**, a następnie kliknij pozycję **Łączniki niestandardowe**.
   
    ![łączniki niestandardowe](./media/customapi-webhooks/custom-apis.png)
3. Kliknij przycisk **Utwórz łącznik niestandardowy**.
4. Kliknij ikonę folderu plików w polu **Importuj plik OpenAPI**, a następnie wybierz przykładowy plik OpenAPI.
5. Kliknij **ikonę przekazywania** w sekcji **Informacje ogólne**, a następnie wybierz plik obrazu, który będzie używany jako ikona.
6. Kliknij pozycję **Kontynuuj**.
   
    ![Importowanie pliku OpenAPI](./media/customapi-webhooks/import-swagger.png)
7. Na następnym ekranie zostaną skonfigurowane ustawienia zabezpieczeń.  W obszarze **Typ uwierzytelniania** wybierz pozycję **Uwierzytelnianie podstawowe**.
8. W sekcji **Uwierzytelnianie podstawowe** wprowadź tekst **Nazwa użytkownika** i **Hasło** w polach etykiet.  Zwróć uwagę na to, że te etykiety będą wyświetlane tylko w przypadku użycia wyzwalacza w przepływie.
   
    ![Uwierzytelnianie podstawowe](./media/customapi-webhooks/basic-auth.png)
9. Nazwij przepływ w górnej części strony i kliknij pozycję **Utwórz łącznik**.
   
    ![Tworzenie interfejsu API](./media/customapi-webhooks/create-api.png)

Nowy łącznik niestandardowy powinien teraz pojawić się na liście na stronie łączników niestandardowych.

## <a name="creating-webhook-triggers-from-the-ui"></a>Tworzenie wyzwalaczy elementu webhook z poziomu interfejsu użytkownika
1. Po przekazaniu lub utworzeniu pliku bazowego OpenAPI przejdź do karty **Definicja** w kreatorze łącznika niestandardowego.
2. W okienku po lewej stronie kliknij pozycję **+ Nowy wyzwalacz** i podaj opis wyzwalacza. W tym przykładzie tworzymy wyzwalacz, który jest wyzwalany po wykonaniu żądania ściągnięcia względem repozytorium.
   
    ![Tworzenie wyzwalacza 1](./media/customapi-webhooks/create-new-trigger-1.png)
3. Następnie zdefiniuj żądanie utworzenia wyzwalacza elementu webhook. Możesz to zrobić, importując przykładowe żądanie *utworzenia wyzwalacza elementu webhook*. Informacje na temat tworzenia elementu webhook zawiera [dokumentacja interfejsu API usługi GitHub](https://developer.github.com/v3/repos/hooks/#create-a-hook). 
4. Usługa Microsoft Flow automatycznie dodaje standardowe nagłówki ```content-type``` i zabezpieczeń, więc nie trzeba ich definiować podczas importowania przykładu. 
   
    ![Tworzenie wyzwalacza 2](./media/customapi-webhooks/create-new-trigger-2.png)
5. Po zaimportowaniu żądania utworzenia elementu webhook zdefiniujemy odpowiedź elementu webhook, importując z przykładowej odpowiedzi. Informacje na temat zdarzenia żądania ściągnięcia zawiera [dokumentacja interfejsu API usługi GitHub](https://developer.github.com/v3/activity/events/types/#pullrequestevent). 
   
    **Uwaga**: nie musisz wklejać pełnej odpowiedzi. Należy zdefiniować tylko potrzebne pola.
   W tym przykładzie wyodrębniamy tylko adres URL żądania ściągnięcia i informacje o użytkowniku, który wykonał to żądanie.
   
    ![Tworzenie wyzwalacza 3](./media/customapi-webhooks/create-new-trigger-3.png)
6. Ostatnim krokiem jest wybranie parametru w żądaniu utworzenia elementu webhook. Jako jego wartość usługa Microsoft Flow powinna określić adres URL wywołania zwrotnego, który ma wypełnić usługa GitHub. Dla nas jest to właściwość url obiektu ```config```.
   
    ![Tworzenie wyzwalacza 4](./media/customapi-webhooks/create-new-trigger-4.png)

## <a name="using-the-webhook-as-a-trigger"></a>Używanie elementu webhook jako wyzwalacza
Po skonfigurowaniu wszystkich elementów możemy użyć elementu webhook w przepływie.  Utworzymy przepływ, który przy każdym odebraniu wypchnięcia narzędzia Git przez repozytorium GitHub będzie wysyłał powiadomienie wypychane do aplikacji mobilnej usługi Microsoft Flow.

1. W [portalu usługi Microsoft Flow w sieci Web](https://flow.microsoft.com) w górnej części strony kliknij pozycję **Moje przepływy**.
2. Kliknij pozycję **Utwórz z pustego**.
3. W projektancie usługi Microsoft Flow wyszukaj łącznik niestandardowy zarejestrowany wcześniej.
   
    ![Nowy wyzwalacz](./media/customapi-webhooks/new-trigger.png)
   
    Kliknij element listy, który będzie używany jako wyzwalacz.
4. Ponieważ jest to pierwsze użycie łącznika niestandardowego, należy nawiązać z nim połączenie.  W polu **Nazwa połączenia** wpisz opisową nazwę połączenia.  W polu **Nazwa użytkownika** wpisz swoją nazwę użytkownika usługi GitHub.  W polu **Hasło** wpisz wcześniej utworzony **osobisty token dostępu**.
   
    ![Nowe połączenie](./media/customapi-webhooks/new-connection.png)
   
    Kliknij przycisk **Utwórz**.
5. Teraz należy udostępnić usłudze Microsoft Flow informacje o repozytorium, które ma być monitorowane.  Zwróć uwagę na znane pola obiektu **WebhookRequestBody** z pliku OpenAPI.  W polach **właściciel** i **repozytorium** wprowadź nazwę właściciela i repozytorium GitHub, które chcesz monitorować.
   
    ![Informacje o repozytorium](./media/customapi-webhooks/repo-info.png)
   
   > [!IMPORTANT]
   > W tym przykładzie jest używane repozytorium [Visual Studio Code](https://code.visualstudio.com). Twoje konto musi mieć uprawnienia do monitorowanego repozytorium.  Najprościej jest użyć własnego repozytorium.
   > 
   > 
6. Kliknij opcję **+ Nowy krok**, a następnie kliknij przycisk **Dodaj akcję**.
7. Wyszukaj akcję **Powiadomienie wypychane** i wybierz ją.
   
    ![Powiadomienie wypychane](./media/customapi-webhooks/push-notification.png)
8. Wprowadź tekst w polu **Tekst**.  Zwróć uwagę na to, że obiekt **WebhookPushResponse** w pliku OpenAPI definiuje listę parametrów do użycia.
   
    ![Szczegóły powiadomienia wypychanego](./media/customapi-webhooks/push-details.png)
9. Nazwij przepływ w górnej części strony i kliknij pozycję **Utwórz przepływ**.
   
    ![Nazwa przepływu](./media/customapi-webhooks/flow-name.png)

## <a name="verification-and-troubleshooting"></a>Weryfikacja i rozwiązywanie problemów
Aby sprawdzić, czy wszystko jest prawidłowo skonfigurowane, kliknij pozycję **Moje przepływy**, a następnie kliknij **ikonę informacji** znajdującą się obok nowego przepływu w celu wyświetlenia historii przebiegu.  Powinien być widoczny co najmniej jeden przebieg „Zakończone powodzeniem” odpowiadający utworzeniu elementu webhook.  Oznacza to, że po stronie usługi GitHub pomyślnie utworzono element webhook.  W przypadku przebiegu zakończonego niepowodzeniem dostępne są szczegóły umożliwiające sprawdzenie przyczyny takiej sytuacji.  Jeśli przyczyną niepowodzenia jest odpowiedź „404 Nie znaleziono”, prawdopodobnie konto GitHub nie ma odpowiednich uprawnień do utworzenia elementu webhook w używanym repozytorium.

## <a name="summary"></a>Podsumowanie
Jeśli wszystko zostało poprawnie skonfigurowane, przy każdym wystąpieniu wypchnięcia narzędzia Git w wybranym repozytorium GitHub aplikacja mobilna usługi Flow otrzyma powiadomienie wypychane.  Powyższy proces umożliwia użycie dowolnej usługi z obsługą elementów webhook jako wyzwalacza we własnych przepływach.

## <a name="next-steps"></a>Następne kroki
* [Rejestrowanie łącznika niestandardowego](register-custom-api.md).
* [Używanie interfejsu API sieci Web platformy ASP.NET](customapi-web-api-tutorial.md).
* [Rejestrowanie interfejsu API usługi Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

