---
title: "Tworzenie łącznika niestandardowego dla interfejsu API sieci Web | Microsoft Docs"
description: "Informacje o sposobie tworzenia interfejsu API sieci Web platformy ASP.NET z uwierzytelnianiem za pomocą usługi Azure Active Directory w usłudze Microsoft Flow."
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
ms.date: 12/06/2016
ms.author: sunayv
ms.openlocfilehash: fef904b02d4b0f028edba236b73e19155b6f4919
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2018
---
# <a name="build-a-custom-connector-for-a-web-api-in-microsoft-flow"></a>Tworzenie łącznika niestandardowego dla interfejsu API sieci Web w usłudze Microsoft Flow
W tym samouczku pokazano, jak rozpocząć tworzenie interfejsu API sieci Web platformy ASP.NET, hostować go w usłudze Azure Web Apps, włączyć uwierzytelnianie za pomocą usługi Azure Active Directory, a następnie zarejestrować interfejs API sieci Web platformy ASP.NET w usłudze Microsoft Flow. Po zarejestrowaniu interfejsu API można połączyć się z nim i wywołać go z przepływu. 

## <a name="prerequisites"></a>Wymagania wstępne
* [Subskrypcja Azure](https://azure.microsoft.com/free/).
* [Konto PowerApps](https://powerapps.microsoft.com).
* Program [Visual Studio](https://www.visualstudio.com/vs/) 2013 lub nowszy.

## <a name="create-an-aspnet-web-api-and-deploy-it-to-azure"></a>Tworzenie interfejsu API sieci Web platformy ASP.NET i wdrażanie go na platformie Azure
1. W programie Visual Studio kliknij opcje **Plik** > **Nowy projekt**, aby utworzyć nową aplikację sieci Web w języku C# na platformie ASP.NET.
   
    ![Nowa aplikacja sieci Web](./media/customapi-web-api-tutorial/newwebapp.png)
2. Wybierz szablon **Interfejs API sieci Web**.  Pozostaw zaznaczoną opcję **Hostuj w chmurze**.  Kliknij przycisk **Zmień uwierzytelnianie**.
   
    ![Nowy szablon projektu sieci Web](./media/customapi-web-api-tutorial/new-web-api.png)
3. Wybierz opcję **Bez uwierzytelniania**, a następnie kliknij przycisk **OK**.
   
    ![Bez uwierzytelniania](./media/customapi-web-api-tutorial/noauth.png)
4. Kliknij przycisk **OK** w oknie dialogowym **Nowy projekt ASP.NET**.  Zostanie wyświetlone okno dialogowe Konfigurowanie aplikacji sieci Web platformy Microsoft Azure.
   
    ![Konfigurowanie aplikacji sieci Web platformy Microsoft Azure](./media/customapi-web-api-tutorial/azure-publishing.png)]
   
    Wybierz konto platformy Azure, wpisz **nazwę aplikacji sieci Web** (lub pozostaw wartość domyślną) i wybierz **subskrypcję** Azure.  Wybierz lub utwórz **Plan usługi App Service** (zbiór aplikacji sieci Web w ramach subskrypcji).  Wybierz lub utwórz **grupę zasobów** (grupę zasobów platformy Azure w ramach subskrypcji).  Wybierz region, w którym należy wdrożyć aplikację sieci Web.  Jeśli jest to wymagane dla interfejsu API sieci Web, wybierz lub utwórz **serwer bazy danych** platformy Azure.  Na koniec kliknij przycisk **OK**.
5. Utwórz interfejs API sieci Web.
   
   > [!NOTE]
   > Jeśli Twój kod dla internetowego interfejsu API nie jest jeszcze gotowy, wypróbuj samouczek [Getting Started with ASP.NET Web API 2 (C#) (Wprowadzenie do składnika Web API 2 platformy ASP.NET [C#])](https://www.asp.net/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api).
   > 
   > 
6. Aby połączyć interfejs API sieci Web z usługą PowerApps, będziemy potrzebować pliku struktury [Swagger](http://swagger.io/), który opisuje jego operacje.  Plik w standardzie OpenAPI można napisać samodzielnie przy użyciu [edytora online](http://editor.swagger.io/), ale w tym samouczku użyjemy narzędzia open source o nazwie [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle/blob/master/README.md).  Zainstaluj pakiet Nuget Swashbuckle w projekcie programu Visual Studio. W tym celu kliknij kolejno pozycje **Narzędzia** > **Menedżer pakietów NuGet** > **Konsola Menedżera pakietów**, a następnie wpisz polecenie `Install-Package Swashbuckle` w konsoli Menedżera pakietów.
   
    ![Polecenie Install-Package Swashbuckle](./media/customapi-web-api-tutorial/swashbuckle-console.png)
   
   > [!TIP]
   > Gdy uruchomisz aplikację internetowego interfejsu API po zainstalowaniu pakietu Swashbuckle, zostanie wygenerowany plik w standardzie OpenAPI pod adresem URL `http://<your root URL>/swagger/docs/v1`.  Wygenerowany interfejs użytkownika będzie również dostępny pod adresem `http://<your root URL>/swagger`.
   > 
   > 
7. Gdy interfejs API sieci Web jest gotowy, należy go opublikować na platformie Azure. Aby opublikować z programu Visual Studio, kliknij prawym przyciskiem myszy projekt sieci Web w Eksploratorze rozwiązań, kliknij pozycję **Publikuj...**, a następnie postępuj zgodnie z poleceniami w oknie dialogowym publikowania.
8. Przejdź do strony `https://<azure-webapp-url>/swagger/docs/v1`, aby pobrać plik OpenAPI w formacie JSON.  Zapisz zwartość jako plik JSON.  W zależności od przeglądarki może być konieczne skopiowanie i wklejenie tekstu do pustego pliku tekstowego.   
   
   > [!IMPORTANT]
   > Dokument w standardzie OpenAPI ze zduplikowanymi identyfikatorami operacji jest nieprawidłowy. Jeśli używasz przykładowego szablonu w języku C#, identyfikator operacji `Values_Get` powtarza się dwukrotnie. Możesz rozwiązać ten problem przez zmianę jednego wystąpienia na `Value_Get` i ponowne opublikowanie.
   > 
   > Możesz również pobrać [przykładowy plik OpenAPI](https://pwrappssamples.blob.core.windows.net/samples/webAPI.json) z tego samouczka. Przed jej użyciem koniecznie usuń komentarze (zaczynające się od znaków `//`).
   > 
   > 

## <a name="set-up-azure-active-directory-authentication"></a>Konfigurowanie uwierzytelniania w usłudze Azure Active Directory
Teraz utworzysz dwie aplikacje usługi Azure Active Directory (AAD) na platformie Azure.  Aby dowiedzieć się, jak to zrobić, zobacz przykłady w [samouczku dotyczącym usługi Azure Resource Manager](customapi-azure-resource-manager-tutorial.md#enable-authentication-in-azure-active-directory).

> [!IMPORTANT]
> Obie aplikacje muszą znajdować się w tym samym katalogu.
> 
> 

### <a name="first-aad-application-securing-the-web-api"></a>Pierwsza aplikacja usługi AAD: zabezpieczanie interfejsu API sieci Web
Pierwsza aplikacja usługi AAD służy do zabezpieczania interfejsu API sieci Web. Nazwij ją **webAPI**.  Wykonaj kroki wspomnianego powyżej samouczka (tylko część zatytułowaną „Włączanie uwierzytelniania w usłudze Azure Active Directory”), podając następujące wartości:

* Adres URL logowania: `https://login.windows.net`
* Adres URL odpowiedzi: `https://<your-root-url>/.auth/login/aad/callback`
* Klucz klienta nie jest wymagany.
* Nie trzeba delegować żadnych uprawnień.
* **Ważne!** Zanotuj identyfikator aplikacji.  Będzie potrzebny później.

### <a name="second-aad-application-securing-the-custom-connector-and-delegated-access"></a>Druga aplikacja usługi AAD: zabezpieczanie łącznika niestandardowego i dostępu delegowanego
Druga aplikacja usługi AAD służy do zabezpieczania rejestracji łącznika niestandardowego i uzyskania delegowanego dostępu do interfejsu API sieci Web chronionego przez pierwszą aplikację. Nazwij ją **webAPI-customAPI** .

* Adres URL logowania: `https://login.windows.net`
* Adres URL odpowiedzi: `https://msmanaged-na.consent.azure-apim.net/redirect`
* Dodaj uprawnienia, aby delegować dostęp do interfejsu API sieci Web.
* Identyfikator tej aplikacji również będzie potrzebny później, więc go zanotuj.
* Wygeneruj klucz klienta i zapisz go w bezpiecznym miejscu. Ten klucz będzie potrzebny później.

## <a name="add-authentication-to-your-azure-web-app"></a>Dodawanie uwierzytelniania do aplikacji sieci Web platformy Azure
1. Zaloguj się do witryny [Azure Portal](https://portal.azure.com), a następnie znajdź aplikację sieci Web, która została wdrożona w pierwszej części.
2. Kliknij przycisk **Ustawienia**, a następnie wybierz pozycję **Uwierzytelnianie/autoryzacja**.
3. Włącz opcję **Uwierzytelnianie usługi App Service**, a następnie wybierz pozycję **Azure Active Directory**.  W następnym bloku wybierz pozycję **Ekspresowo**.  
4. Kliknij pozycję **Wybierz istniejącą aplikację usługi AD** i wybierz utworzoną wcześniej aplikację usługi AAD o nazwie **webAPI**.

Teraz powinno być możliwe używanie usługi AAD do uwierzytelniania aplikacji sieci Web.

## <a name="add-the-custom-connector-to-microsoft-flow"></a>Dodawanie łącznika niestandardowego do usługi Microsoft Flow
1. Zmodyfikuj plik OpenAPI, aby dodać obiekt `securityDefintions` i uwierzytelnianie w usłudze AAD używane w aplikacji sieci Web. Sekcja pliku OpenAPI z właściwością **host** powinna wyglądać następująco:

```javascript
// File header should be above here...

"host": "<your-root-url>",
"schemes": [
    "https"         //Make sure this is https!
],
"securityDefinitions": {
    "AAD": {
        "type": "oauth2",
        "flow": "accessCode",
        "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
        "tokenUrl" : "https://login.windows.net/common/oauth2/token",
        "scopes": {}
    }
},

// The rest of the OpenAPI follows...
```

1. Przejdź do usługi [Microsoft Flow](https://flow.powerapps.com) i dodaj łącznik niestandardowy zgodnie z opisem w sekcji [Register and use custom connectors in Microsoft Flow](register-custom-api.md) (Rejestrowanie i używanie łączników niestandardowych w usłudze Microsoft Flow).
2. Po przesłaniu pliku OpenAPI kreator automatycznie wykryje, że używasz uwierzytelniania w usłudze AAD w interfejsie API sieci Web.
3. Skonfiguruj uwierzytelnianie w usłudze AAD dla łącznika niestandardowego.  
   
   * **Identyfikator klienta**: *identyfikator klienta aplikacji webAPI-CustomAPI*
   * **Klucz tajny**: *klucz klienta aplikacji webAPI-CustomAPI*
   * **Adres URL logowania**: `https://login.windows.net`
   * **ResourceUri**: *identyfikator klienta aplikacji webAPI*
4. Kliknij polecenie **Utwórz**, aby utworzyć połączenie z łącznikiem niestandardowym.

## <a name="next-steps"></a>Następne kroki
Przejrzyj [samouczek dotyczący łącznika niestandardowego usługi Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

