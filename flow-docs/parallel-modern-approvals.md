---
title: "Tworzenie nowoczesnego przepływu pracy zatwierdzania równoległego | Microsoft Docs"
description: "Tworzenie nowoczesnego przepływu pracy zatwierdzania równoległego"
services: 
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/24/2017
ms.author: deonhe
ms.openlocfilehash: b4d11da19db97ce94df3e3d5237f6c90b3514269
ms.sourcegitcommit: 01325305b9d2cf964acac9feb6cca0af66db7440
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2017
---
# <a name="create-parallel-approval-workflows-with-microsoft-flow"></a>Tworzenie przepływów pracy zatwierdzania równoległego za pomocą usługi Microsoft Flow
W przepływie pracy zatwierdzania równoległego elementy takie jak faktury, zamówienia, wnioski urlopowe itp. muszą być zatwierdzone przez wiele osób. Zatwierdzenie przez każdą osobę jest niezależne od innych osób zatwierdzających.

W tym przewodniku za pomocą usługi Microsoft Flow zostanie utworzony przepływ, który automatyzuje przepływ pracy zatwierdzania równoległego. Ten przepływ automatyzuje proces zatwierdzania wniosku urlopowego pracownika, który wymaga zatwierdzenia przez wszystkie osoby (lub zespoły), które pracownik regularnie obsługuje. Pracownicy przesyłają wnioski urlopowe przy użyciu [listy programu SharePoint](https://support.office.com/article/Introduction-to-lists-0a1c3ace-def0-44af-b225-cfa8d92c52d7). Wniosek urlopowy musi zostać zatwierdzony przez bezpośredniego menedżera pracownika, zespół sprzedaży i zespół działu kadr. Każdy wniosek urlopowy jest kierowany do każdej osoby zatwierdzającej w celu uzyskania decyzji. Przepływ wysyła wiadomość e-mail ze zmianami stanu, a następnie aktualizuje program SharePoint o decyzje.

## <a name="prerequisites"></a>Wymagania wstępne
[!INCLUDE [prerequisites-for-modern-approvals](includes/prerequisites-for-modern-approvals.md)]

Na utworzonej liście usługi SharePoint Online muszą znajdować się następujące kolumny:

   ![Kolumny listy programu SharePoint](./media/parallel-modern-approvals/sharepoint-columns.png)

Zanotuj nazwę i adres URL listy usługi SharePoint Online. Te informacje będą potrzebne później podczas konfigurowania wyzwalacza **SharePoint — Po utworzeniu nowego elementu**.

## <a name="create-your-flow-from-the-blank-template"></a>Tworzenie przepływu na podstawie pustego szablonu
[!INCLUDE [sign-in-and-create-flow-from-blank-template](includes/sign-in-and-create-flow-from-blank-template.md)]

## <a name="add-a-trigger"></a>Dodawanie wyzwalacza
[!INCLUDE [add-trigger-when-sharepoint-item-created](includes/add-trigger-when-sharepoint-item-created.md)]

   ![Informacje programu SharePoint](includes/media/parallel-modern-approvals/select-sharepoint-site-info.png)

## <a name="get-the-manager-for-the-person-who-created-the-vacation-request"></a>Pobieranie menedżera osoby, która utworzyła wniosek urlopowy
[!INCLUDE [add-get-manager-action](includes/add-get-manager-action.md)]

## <a name="name-and-save-your-flow"></a>Nadawanie nazwy przepływowi i zapisywanie go
1. Nadaj nazwę przepływowi, a następnie wybierz pozycję **Utwórz przepływ**, aby zapisać wyniki dotychczasowej pracy.
   
   ![zapisywanie przepływu](./media/parallel-modern-approvals/save.png)

> [!NOTE]
> Co jakiś czas wybierz pozycję **Aktualizuj przepływ** znajdującą się u góry ekranu, aby zapisać zmiany w przepływie.
> 
> 

   ![wybieranie akcji aktualizacji](./media/parallel-modern-approvals/update.png)

Aby kontynuować wprowadzanie zmian po zapisaniu lub zaktualizowaniu przepływu, wybierz pozycję **Edytuj przepływ** u góry ekranu, a następnie kontynuuj wprowadzanie zmian.

## <a name="add-an-approval-action-for-immediate-manager"></a>Dodawanie akcji zatwierdzenia dla bezpośredniego menedżera
[!INCLUDE [add-an-approval-action](includes/add-an-approval-action.md)]

> [!IMPORTANT]
> Ta akcja spowoduje wysłanie wniosku urlopowego na adres e-mail podany w polu **Przypisano do**, a więc należy wstawić token **Adres e-mail** z listy **Pobierz menedżera**.
> 
> 

## <a name="insert-a-parallel-branch-approval-action-for-the-sales-team"></a>Wstawianie akcji zatwierdzenia gałęzi równoległej dla zespołu sprzedaży
1. Wybierz strzałkę w dół znajdującą się między kartą **Pobierz menedżera** a kartą **Rozpocznij zatwierdzenie**.
2. Wybierz znak plus wyświetlany na strzałce w dół po jej wybraniu.
3. Wybierz pozycję **Dodaj gałąź równoległą**.
4. Wybierz pozycję **Dodaj akcję**.
   
    ![konfiguracja pobierania menedżera](./media/parallel-modern-approvals/add-parallel-branch.png)
5. Wyszukaj, wybierz, a następnie skonfiguruj akcję **Rozpocznij zatwierdzenie**, która spowoduje wysłanie wniosku urlopowego do zespołu sprzedaży. Jeśli nie masz pewności, jak dodać akcję **Rozpocznij zatwierdzenie**, zobacz [kroki używane do dodawania akcji zatwierdzenia dla bezpośredniego menedżera](parallel-modern-approvals.md#add-an-approval-action-for-immediate-manager).

> [!IMPORTANT]
> Należy użyć adresu e-mail zespołu sprzedaży w polu **Przypisano do** akcji **Rozpocznij zatwierdzenie**.
> 
> 

## <a name="insert-a-parallel-branch-approval-action-for-the-human-resources-team"></a>Wstawianie akcji zatwierdzenia gałęzi równoległej dla zespołu działu kadr
1. Powtórz kroki [wstawiania gałęzi równoległej dla zespołu sprzedaży](parallel-modern-approvals.md#insert-a-parallel-branch-approval-action-for-the-sales-team), aby dodać, a następnie skonfigurować akcję **Rozpocznij zatwierdzenie** do wysyłania wniosków urlopowych do działu kadr.

> [!IMPORTANT]
> Należy użyć adresu e-mail zespołu działu kadr w polu **Przypisano do** akcji **Rozpocznij zatwierdzenie**.
> 
> 

Po wykonaniu tych czynności przepływ powinien wyglądać podobnie jak w tym przykładzie:

   ![przepływ z gałęziami równoległymi](./media/parallel-modern-approvals/flow-with-parallel-branches.png)

## <a name="options-after-adding-parallel-branches"></a>Opcje po dodaniu gałęzi równoległych
Po dodaniu akcji do gałęzi równoległych dostępne są dwie opcje na potrzeby dodawania kolejnych kroków do przepływu:

* Mały przycisk **Wstaw nowy krok** (okrągły przycisk ze znakiem plus wyświetlany po wybraniu dowolnego białego obszaru w gałęzi lub obszarze bezpośrednio poniżej gałęzi). Ten przycisk służy do dodawania kroku do tej **konkretnej gałęzi**. Kroki dodane za pomocą tego przycisku będą uruchamiane po ukończeniu tej konkretnej gałęzi.
* Większy przycisk **Nowy krok** znajdujący się u dołu całego przepływu pracy. Ten przycisk służy do dodawania akcji uruchamianej po ukończeniu **wszystkich gałęzi**. Kroki dodane za pomocą tego przycisku będą uruchamiane po ukończeniu wszystkich gałęzi.

W poniższych sekcjach użyjemy małego przycisku **Wstaw nowy krok** w celu wykonania następujących kroków w każdej gałęzi:

* Dodanie warunku sprawdzającego, czy wniosek urlopowy został zatwierdzony lub odrzucony.
* Wysłanie do pracownika wiadomości e-mail z informacją o decyzji.
* Zaktualizowanie wniosku urlopowego w programie SharePoint przy użyciu decyzji o zatwierdzeniu.

Następnie użyjemy większego przycisku **Nowy krok**, aby wysłać wiadomość e-mail zawierającą podsumowanie wszystkich decyzji wydanych w sprawie wniosku urlopowego.

Kontynuujmy:

## <a name="add-a-condition-to-each-branch"></a>Dodawanie warunku do każdej gałęzi
1. Wybierz dowolny biały obszar w gałęzi **Rozpocznij zatwierdzenie**.
2. Wybierz mały przycisk **Wstaw nowy krok** (okrągły przycisk ze znakiem plus, który pojawia się po wybraniu białego obszaru w gałęzi w poprzednim kroku).
3. Z wyświetlonego menu wybierz pozycję **Dodaj warunek**.
4. Wybierz pierwsze pole na karcie **Warunek**, a następnie wybierz token **Odpowiedź** z kategorii **Rozpocznij zatwierdzenie** na liście zawartości dynamicznej.
   
    ![warunek przepływu z gałęziami równoległymi](./media/parallel-modern-approvals/configure-approval-condition.png)
5. Upewnij się, że lista (na środku karty **Warunek**) ma ustawioną wartość **jest równe**.
6. Wprowadź tekst **Zatwierdź** w ostatnim polu (w tym tekście jest uwzględniana wielkość liter).
7. Karta warunku powinna teraz wyglądać podobnie do przedstawionej w tym przykładzie:
   
    ![warunek przepływu z gałęziami równoległymi](includes/media/parallel-modern-approvals/condition-card.png)
   
   > [!NOTE]
   > Ten warunek sprawdza odpowiedź z akcji **Rozpocznij zatwierdzenie**, która jest przesyłana do menedżera pracownika.
   > 
   > 
8. Powtórz te czynności w gałęziach **Rozpocznij zatwierdzenie 2** (żądanie zatwierdzenia do zespołu sprzedaży) i **Rozpocznij zatwierdzenie 3** (żądanie zatwierdzenia do działu kadr).

## <a name="add-email-actions-to-each-branch"></a>Dodawanie akcji poczty e-mail do każdej gałęzi
Wykonaj następujące kroki po stronie **JEŚLI TAK, NIC NIE RÓB** gałęzi **Warunek**.

   Uwaga: przepływ używa tych kroków do wysyłania wiadomości e-mail, gdy wniosek zostanie zatwierdzony:

[!INCLUDE [add-action-to-send-email-when-vacation-approved](includes/add-action-to-send-email-when-vacation-approved.md)]

   ![konfigurowanie szablonu wiadomości e-mail informującej o wstępnym zatwierdzeniu](includes/media/parallel-modern-approvals/yes-email-config.png)

Aby wysyłać wiadomość e-mail, gdy wniosek zostanie odrzucony, należy użyć strony **JEŚLI NIE, NIC NIE RÓB** gałęzi **Warunek**, a następnie powtórzyć poprzednie kroki w celu dodania szablonu dla wiadomości e-mail z informacją o odrzuceniu.

Powtórz te czynności w gałęziach **Rozpocznij zatwierdzenie 2** (żądanie zatwierdzenia do zespołu sprzedaży) i **Rozpocznij zatwierdzenie 3** (żądanie zatwierdzenia do działu kadr).

## <a name="update-the-vacation-request-with-the-decision"></a>Aktualizowanie wniosku urlopowego przy użyciu decyzji
Wykonaj następujące kroki, aby zaktualizować program SharePoint po wydaniu decyzji.

   Uwaga: te kroki należy wykonać po stronach **JEŚLI TAK** i **JEŚLI NIE** gałęzi.

[!INCLUDE [add-action-to-update-sharepoint-with-approval](includes/add-action-to-update-sharepoint-with-approval.md)]

   ![konfigurowanie aktualizacji elementu](./media/parallel-modern-approvals/configure-update-item.png)

Powtórz poprzednie kroki w gałęziach **Rozpocznij zatwierdzenie 2** i **Rozpocznij zatwierdzenie 3**.

## <a name="complete-the-flow"></a>Kończenie przepływu
1. Wybierz kolejno pozycje **Nowy krok** > **Dodaj akcję**.
   
    ![konfigurowanie aktualizacji elementu](includes/media/parallel-modern-approvals/add-an-action-2-step.png)
2. Wykonaj podane wcześniej kroki, aby wysłać wiadomość e-mail z podsumowaniem wyników każdego zatwierdzenia. Wyślij tę wiadomość e-mail do pracownika, który wnioskował o urlop. Karta może wyglądać podobnie do przedstawionej w tym przykładzie:
   
   ![konfigurowanie aktualizacji elementu](./media/parallel-modern-approvals/final-email-card.png)

## <a name="learn-more-about-modern-approvals"></a>Dowiedz się więcej o nowoczesnych zatwierdzeniach
[Wprowadzenie do nowoczesnych zatwierdzeń](modern-approvals.md)

