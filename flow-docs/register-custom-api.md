---
title: "Rejestrowanie i używanie łączników niestandardowych | Microsoft Docs"
description: "Rejestrowanie i używanie łączników niestandardowych w usłudze Microsoft Flow za pomocą pliku OpenAPI i narzędzia Postman."
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/09/2017
ms.author: sunayv
ms.openlocfilehash: 94d46b2948f03316162e1c1d45860ae94feb897c
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="register-and-use-custom-connectors-in-microsoft-flow"></a>Rejestrowanie i używanie łączników niestandardowych w usłudze Microsoft Flow
Usługa Microsoft Flow umożliwia tworzenie przepływów pracy bez pisania kodu. Jednak w niektórych przypadkach potrzebujesz rozszerzyć możliwości usługi Microsoft Flow, a usługi sieci Web to naturalne rozwiązanie. Twój przepływ może połączyć się z usługą, wykonać operacje i pobrać zwrócone dane. Jeśli masz usługę sieci Web, którą chcesz połączyć z usługą Microsoft Flow, należy zarejestrować usługę jako łącznik niestandardowy. Ten proces umożliwia usłudze Microsoft Flow poznanie charakterystyki Twojego interfejsu API sieci Web, w tym wymaganego uwierzytelniania, obsługiwanych operacji oraz parametrów i danych wyjściowych dla każdej z tych operacji.

W tym temacie zapoznamy się z krokami wymaganymi do zarejestrowania i używania łącznika niestandardowego oraz użyjemy [interfejsu API analizy tekstu](https://www.microsoft.com/cognitive-services/text-analytics-api) usługi Azure Cognitive Services. Ten interfejs API umożliwia identyfikowanie języka, opinii i kluczowych fraz w przekazanym do niego tekście.

## <a name="prerequisites"></a>Wymagania wstępne
* [Konto usługi Microsoft Flow](https://flow.microsoft.com).
* Plik JSON w standardzie OpenAPI 2.0 (wcześniej znanym jako struktura Swagger), adres URL definicji OpenAPI lub kolekcja Postman Collection dla interfejsu API. Jeśli nie masz żadnego z tych elementów, udostępnimy Ci wskazówki.
* Obraz używany jako ikona łącznika niestandardowego (opcjonalnie).

## <a name="steps-in-the-custom-connector-process"></a>Kroki procesu łącznika niestandardowego
Proces łącznika niestandardowego składa się z kilku kroków w skrócie opisanych poniżej. W tym artykule przyjęto, że masz już interfejs API RESTful z uwierzytelnianym dostępem, więc w pozostałej części artykułu skoncentrujemy się na krokach 3–6. Przykład wykonania kroków 1 i 2 zawiera sekcja [Tworzenie niestandardowego interfejsu API sieci Web dla usługi Microsoft Flow](customapi-web-api-tutorial.md).

1. **Utwórz interfejs API RESTful** w wybranym języku i na wybranej platformie. W przypadku technologii firmy Microsoft zalecamy następujące platformy (lecz można użyć dowolnych):
   
   * Azure Functions
   * Azure Web Apps
   * Azure API Apps
2. **Zabezpiecz interfejs API** za pomocą jednego z następujących mechanizmów uwierzytelniania. Możesz zezwolić na nieuwierzytelniony dostęp do swoich łączników, lecz nie zalecamy tego.
   
   * Azure Active Directory. Aby uzyskać więcej informacji, zobacz [Użycie usługi Azure Active Directory z łącznikiem niestandardowym w usłudze Microsoft Flow](customapi-azure-resource-manager-tutorial.md).
   * Uwierzytelnianie OAuth 2.0 dla określonych usług, takich jak Dropbox, Facebook i SalesForce
   * Ogólne uwierzytelnianie OAuth 2.0
   * Klucz interfejsu API
   * Uwierzytelnianie podstawowe
3. **Opisz interfejs API**, korzystając z jednego z dwóch standardów branżowych, aby usługa Microsoft Flow mogła się z nim połączyć.
   
   * Plik OpenAPI
   * Kolekcja Postman Collection
     
     Możesz także utworzyć plik OpenAPI w kroku 4 w ramach procesu rejestracji.
4. **Zarejestruj łącznik niestandardowy** przy użyciu kreatora w usłudze Microsoft Flow, gdzie można określić opis interfejsu API, szczegóły zabezpieczeń i inne informacje.
5. **Użyj łącznika niestandardowego** w aplikacji. Utwórz połączenie z łącznikiem w aplikacji i wywołuj dowolne operacje udostępniane przez interfejs API — tak jak w przypadku wywoływania standardowych połączeń w usłudze Microsoft Flow.
6. **Udostępnij łącznik niestandardowy** tak jak inne zasoby w usłudze Microsoft Flow. Ten krok jest opcjonalny, ale często warto udostępnić łączniki niestandardowe wielu twórcom aplikacji.

## <a name="describe-your-api"></a>Opisywanie interfejsu API
Zakładając, że masz interfejs API z uwierzytelnianym dostępem, potrzebujesz sposobu na opisanie interfejsu API, aby usługa Microsoft Flow mogła się z nim połączyć. W tym celu należy utworzyć plik OpenAPI lub kolekcję Postman Collection. Można to zrobić z *dowolnego* punktu końcowego interfejsu API REST, a takie punkty końcowe to:

* Publicznie dostępne łączniki. Np. [Spotify](https://developer.spotify.com/), [Uber](https://developer.uber.com/), [Slack](https://api.slack.com/), [Rackspace](http://docs.rackspace.com/) itd.
* Interfejs API, który można utworzyć i wdrożyć w ramach dowolnego dostawcy obsługującego chmurę, m.in. Azure, Amazon Web Services (AWS), Heroku, Google Cloud itd.
* Niestandardowy biznesowy interfejs API wdrożony w sieci, pod warunkiem że zostanie on uwidoczniony w publicznej sieci internetowej.

Pliki OpenAPI 2.0 (wcześniej znane jako struktury Swagger) i kolekcje Postman Collection używają różnych formatów, lecz jedne i drugie są niezależnymi od języka dokumentami czytelnymi dla komputera, które opisują operacje i parametry interfejsu API:

* Możesz wygenerować te dokumenty przy użyciu różnych narzędzi w zależności od języka i platformy stanowiących podstawę interfejsu API. Przykład pliku OpenAPI znajduje się w [dokumentacji interfejsu API analizy tekstu](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/export?DocumentFormat=Swagger&ApiName=Azure).
* Jeśli nie masz jeszcze pliku OpenAPI dla interfejsu API i nie chcesz go tworzyć, w dalszym ciągu możesz łatwo utworzyć łącznik niestandardowy przy użyciu kolekcji Postman Collection. Więcej informacji zawiera sekcja [Tworzenie kolekcji Postman Collection](postman-collection.md).
* Usługa Microsoft Flow ostatecznie używa w tle standardu OpenAPI — kolekcja Postman Collection zostanie przeanalizowana i przekształcona w plik definicji OpenAPI.

**Uwaga**: rozmiar pliku musi być mniejszy niż 1 MB.

### <a name="getting-started-with-openapi-and-postman"></a>Wprowadzenie do standardu OpenAPI i narzędzia Postman
* Jeśli nie znasz standardu OpenAPI, zobacz stronę [Getting Started with OpenAPI](http://swagger.io/getting-started/) (Wprowadzenie do standardu OpenAPI) w witrynie swagger.io.
* Jeśli nie znasz narzędzia Postman, zainstaluj [aplikację Postman](https://www.getpostman.com/apps) z jej witryny.
* Jeśli Twój interfejs API został utworzony za pomocą usługi Azure API Apps lub Azure Functions, zobacz [Exporting an Azure hosted API to PowerApps and Microsoft Flow](https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow) (Eksportowanie interfejsu API hostowanego na platformie Azure do usług PowerApps i Microsoft Flow), aby uzyskać więcej informacji.

## <a name="register-your-custom-connector"></a>Rejestrowanie łącznika niestandardowego
Teraz użyjesz pliku OpenAPI lub kolekcji Postman Collection, aby zarejestrować łącznik niestandardowy w usłudze Microsoft Flow.

1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) na górnym pasku wybierz koło zębate, aby otworzyć menu ustawień. Wybierz opcję **Łączniki niestandardowe**.
   
    ![Tworzenie łącznika niestandardowego](./media/register-custom-api/managecustomapi.png)  
2. Wybierz pozycję **Utwórz łącznik niestandardowy**.
   
    ![Właściwości łącznika niestandardowego](./media/register-custom-api/newcustomapi.png)
3. Na karcie **Ogólne** wybierz sposób utworzenia łącznika niestandardowego.
   
   * Przekazanie pliku OpenAPI
   * Wklejenie adresu URL pliku OpenAPI
   * Przekazanie kolekcji Postman Collection w wersji 1
     
     ![Jak utworzyć łącznik niestandardowy](./media/register-custom-api/choosehowtocreate.png)
     
     Przekaż ikonę łącznika niestandardowego. Pola Opis, Host i Podstawowy adres URL są zazwyczaj wypełniane automatycznie za pomocą danych z pliku OpenAPI. Jeśli pola nie zostaną wypełnione automatycznie, możesz je wypełnić. Wybierz przycisk **Kontynuuj**.
4. Na karcie **Zabezpieczenia** podaj właściwości uwierzytelniania.
   
    ![Typy uwierzytelniania](./media/register-custom-api/authenticationtypes.png)
   
   * Typ uwierzytelniania jest wypełniany automatycznie na podstawie obiektu `securityDefinitions` w pliku OpenAPI. Poniżej znajduje się przykład uwierzytelniania OAuth2.0.
     
       ```
       "securityDefinitions": {
           "AAD": {
           "type": "oauth2",
           "flow": "accessCode",
           "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
           "tokenUrl": "https://login.windows.net/common/oauth2/token"
           "scopes": {}
           }
       },
       ```
   * Jeśli plik OpenAPI nie używa obiektu `securityDefintions`, żadne dodatkowe wartości nie są potrzebne.
   * Jeśli jest używana kolekcja Postman Collection, typ uwierzytelniania jest wypełniany automatycznie tylko wtedy, gdy jest używany obsługiwany typ uwierzytelniania, na przykład OAuth 2.0 lub Podstawowe.
   * Przykład konfigurowania uwierzytelniania usługi Azure Active Directory (AAD) zawiera sekcja [Tworzenie niestandardowego interfejsu API sieci Web dla usługi Microsoft Flow](customapi-web-api-tutorial.md#set-up-azure-active-directory-authentication).
5. Na karcie **Definicje** są automatycznie wypełniane wszystkie operacje zdefiniowane w pliku OpenAPI lub kolekcji Postman Collection razem z wartościami żądania i odpowiedzi. Jeśli wszystkie wymagane operacje są zdefiniowane, możesz przejść do kroku 6 procesu rejestracji bez wprowadzania zmian na tym ekranie.
   
    ![Karta Definicja](./media/register-custom-api/definitiontab.png)
   
    Jeśli chcesz zmodyfikować istniejące akcje lub dodać nowe akcje do łącznika niestandardowego, kontynuuj czytanie.
   
   1. Jeśli chcesz dodać nową akcję, której nie ma w pliku OpenAPI ani w kolekcji Postman Collection, wybierz pozycję **Nowa akcja** w lewym okienku i wypełnij sekcję **Ogólne**, podając nazwę, opis i widoczność operacji.
   2. W sekcji **Żądanie** wybierz polecenie **Importuj z próbki** w prawym górnym rogu. W formularzu po prawej stronie wklej przykładowe żądanie. Przykładowe żądania są zazwyczaj dostępne w dokumentacji interfejsu API, gdzie znajdują się informacje dotyczące wypełniania pól **Czasownik**, **Adres URL żądania**, **Nagłówki** i **Treść**. Przykład znajduje się w [dokumentacji interfejsu API analizy tekstu](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/operations/56f30ceeeda5650db055a3c6).
      
      > [!IMPORTANT]
      > Pamiętaj, aby usunąć nagłówek `Content-type` z akcji, ponieważ zostanie on automatycznie dodany przez usługę Microsoft Flow. Nagłówki uwierzytelniania zdefiniowane w sekcji **Zabezpieczenia** także powinny zostać usunięte z akcji i wyzwalaczy. 
      > 
      > 
      
      ![Importowanie z przykładu](./media/register-custom-api/importfromsample.png)
   3. Wybierz polecenie **Importuj**, aby zakończyć definiowanie żądania. Zdefiniuj odpowiedź w podobny sposób.
6. Po zdefiniowaniu wszystkich operacji wybierz polecenie **Utwórz**, aby utworzyć łącznik niestandardowy.
7. Po utworzeniu łącznika niestandardowego przejdź do karty **Test**, aby przetestować operacje zdefiniowane w interfejsie API. Wybierz połączenie i podaj parametry wejściowe, aby przetestować operację.
   
    ![Testowanie łącznika niestandardowego](./media/register-custom-api/testcustomapi.png)
   
    Jeśli wywołanie powiedzie się, otrzymasz prawidłową odpowiedź.
   
    ![Testowanie odpowiedzi łącznika](./media/register-custom-api/testapiresponse.png)

### <a name="quota-and-throttling"></a>Przydział i ograniczanie przepustowości
* Strona [cennika usługi Microsoft Flow](https://flow.microsoft.com/pricing/) zawiera szczegóły na temat limitów przydziału dla tworzenia łączników niestandardowych. Łączniki niestandardowe, które zostały udostępnione dla Ciebie, nie są uwzględniane w limicie przydziału.
* Dla każdego połączenia utworzonego w ramach łącznika niestandardowego użytkownicy mogą wprowadzić do 500 żądań na minutę.

## <a name="share-your-custom-connector"></a>Udostępnianie łącznika niestandardowego
Teraz, gdy masz łącznik niestandardowy, możesz udostępnić go innym użytkownikom w organizacji. Pamiętaj, że po udostępnieniu łącznika niestandardowego inne osoby mogą stać się od niego zależne i usunięcie łącznika niestandardowego spowoduje usunięcie wszystkich połączeń z łącznikiem. Jeśli chcesz udostępnić łącznik dla użytkowników spoza organizacji, zobacz [Overview of certifying custom connectors in Microsoft Flow](api-connector-overview.md) (Omówienie certyfikacji łączników niestandardowych w usłudze Microsoft Flow).

1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) na górnym pasku wybierz koło zębate, aby otworzyć menu ustawień. Wybierz opcję **Łączniki niestandardowe**.
   
    ![Nowe połączenie](./media/register-custom-api/managecustomapi.png)
2. Wybierz przycisk wielokropka (**...**) dla łącznika, a następnie wybierz polecenie **Wyświetl właściwości**.  
   
    ![Wyświetlanie właściwości łącznika](./media/register-custom-api/view-properties.png)
3. Wybierz pozycję **Udostępnij**, a następnie podaj użytkowników lub grupy, którym chcesz udzielić dostępu do łącznika.  
   
    ![Udostępnianie łącznika niestandardowego](./media/register-custom-api/sharecustomapi.png)
4. Wybierz pozycję **Zapisz**.

## <a name="next-steps"></a>Następne kroki
[Dowiedz się, jak utworzyć kolekcję Postman Collection](postman-collection.md)

[Informacje na temat niestandardowych rozszerzeń w standardzie OpenAPI](customapi-how-to-swagger.md).

[Używanie interfejsu API sieci Web platformy ASP.NET](customapi-web-api-tutorial.md).

[Rejestrowanie interfejsu API usługi Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

