---
title: "Omówienie środowiska dla administratorów | Microsoft Docs"
description: "Używanie i tworzenie środowisk w usłudze Microsoft Flow oraz zarządzanie nimi"
services: 
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/27/2016
ms.author: sunayv
ms.openlocfilehash: f1c50e5d16d5b9fbbd3e6db3128947b0554e9a85
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="using-environments-within-microsoft-flow"></a>Używanie środowisk za pomocą usługi Microsoft Flow
## <a name="benefits"></a>Korzyści
Środowiska to nowa funkcja w usłudze Microsoft Flow. Korzystanie z nich daje następujące korzyści: 

* **Lokalizacja danych**: środowiska można tworzyć w różnych regionach, z którymi są one później powiązane. Po utworzeniu przepływu w środowisku jest on kierowany do wszystkich centrów danych w tej lokalizacji geograficznej. Zapewnia to również korzyści wynikające ze wzrostu wydajności. 
  
    Jeśli użytkownicy znajdują się w Europie, środowisko, z którego będą oni korzystali, należy utworzyć w regionie Europa. Jeśli użytkownicy znajdują się w Stanach Zjednoczonych, środowisko, z którego będą oni korzystali, należy utworzyć w regionie Stany Zjednoczone. 
  
    Jeśli usuniesz środowisko, wszystkie przepływy w tym środowisku zostaną także usunięte. To dotyczy wszelkich elementów utworzonych w środowisku, w tym połączeń, bram, aplikacji PowerApps i innych.
* **Ochrona przed utratą danych**: dla administratora nie są pożądane przepływy, które pobierają dane z lokalizacji wewnętrznych (takich jak usługa *OneDrive dla Firm*), a następnie publikują je publicznie (na przykład w usłudze *Twitter*). Korzystając z zasad ochrony przed utratą danych, można kontrolować usługi, które mogą być używane w ramach zasad wymagających używania tylko danych biznesowych. 
  
    Na przykład można dodać usługi *SharePoint* i *OneDrive dla Firm* do zasad wymagających używania tylko danych biznesowych. Wszystkie przepływy utworzone w tym środowisku mogą używać tych usług *SharePoint* i *OneDrive dla Firm*. Dostępne są tylko usługi dodane przez użytkownika. 
  
  > [!NOTE]
  > Zasady ochrony przed utratą danych są dostępne w przypadku niektórych jednostek SKU licencji, w tym licencji P2. 
  > 
  > 
* **Granica izolacji dla wszystkich zasobów**: wszystkie przepływy, bramy, połączenia, łączniki niestandardowe itd. znajdują się w tym konkretnym środowisku. Nie istnieją one w innych środowiskach. 
* **Usługa Common Data Service**: istnieje potrzeba utworzenia przepływu, który wstawia gdzieś dane. Dostępne możliwości to:
  
  * Wstawienie danych do pliku programu Excel i zapisanie tego pliku w ramach konta magazynu w chmurze, takiego jak usługa OneDrive.
  * Utwórz własną usługę SQL Database i zapisz w niej dane.
  * Użycie usługi Common Data Service do przechowywania danych.
    
    Każde środowisko na potrzeby przepływów może mieć jeden magazyn bazy danych w usłudze Common Data Service lub nie mieć żadnego. Dostęp do usługi Common Data Service zależy od zakupionej licencji. Nie jest on dołączony do licencji bezpłatnej.

## <a name="limitations"></a>Ograniczenia
Mimo że środowiska zapewniają wiele korzyści, z ich używaniem wiążą się również nowe ograniczenia. Fakt, że środowiska znajdują się w granicach izolacji, oznacza, że nigdy nie mogą istnieć zasoby odwołujące się do innych zasobów *między* środowiskami. Nie można na przykład utworzyć łącznika niestandardowego w jednym środowisku i utworzyć przepływu, który używa zarówno tego łącznika niestandardowego, jak i bramy w innym środowisku.

W związku z tym ważne jest, aby środowiska były tworzone tylko wtedy, gdy są potrzebne. Tworzenie zbyt wielu środowisk spowoduje, że udostępnianie zasobów przez użytkowników w organizacji stanie się bardzo trudne.

## <a name="use-the-default-environment"></a>Użycie środowiska domyślnego
Środowisko **domyślne** jest dostępne dla każdego użytkownika i jest współużytkowane przez wszystkich użytkowników. Każdy użytkownik może tworzyć przepływy w tym środowisku.

> [!TIP]
> Jeśli jesteś użytkownikiem wersji zapoznawczej, wszystkie istniejące przepływy znajdują się w środowisku domyślnym. *Użytkownik wersji zapoznawczej* to osoba, która używała usługi Microsoft Flow przed jej ogólnym udostępnieniem. 
> 
> 

## <a name="use-the-administrator-center"></a>Używanie centrum administratora
Administratorzy za pomocą centrum administratora mogą tworzyć środowiska, dodawać użytkowników do tych środowisk, a także wykonywać inne podobne zadania. Centrum administratora można otworzyć na dwa sposoby:

#### <a name="option-1-select-settings"></a>Opcja 1. Wybranie pozycji Ustawienia
1. Zaloguj się do witryny [flow.microsoft.com](https://flow.microsoft.com).
2. Wybierz pozycję Ustawienia (koło zębate), a następnie z listy wybierz pozycję **Centrum administratora**:  
   ![Ustawienia i Portal administratora](./media/environments-overview-admin/settings.png)
3. Zostanie otwarte centrum administratora.

#### <a name="option-2-open-adminflowmicrosoftcom"></a>Opcja 2. Otwarcie witryny admin.flow.microsoft.com
Przejdź do witryny [admin.flow.microsoft.com](https://admin.flow.microsoft.com) i zaloguj się przy użyciu konta służbowego. Zostanie otwarte centrum administratora.

## <a name="create-an-environment"></a>Tworzenie środowiska
1. W [centrum administratora usługi Microsoft Flow](https://admin.flow.microsoft.com) wybierz pozycję **Środowiska**. Wszystkie istniejące środowiska zostaną wyświetlone:  
   ![](./media/environments-overview-admin/environments-list.png)
2. Wybierz pozycję **Nowe środowisko**. Podaj następujące informacje:
   
   | Właściwość | Opis |
   | --- | --- |
   | Nazwa środowiska |Podaj nazwę środowiska, taką jak `Human Resources` lub `Europe flows`. |
   | Region |Wybierz lokalizację na potrzeby hostowania środowiska. W celu uzyskania najwyższej wydajności należy użyć regionu, który jest najbliżej użytkowników. Na przykład jeśli użytkownicy przepływu znajdują się w Londynie, wybierz region Europa. Jeśli użytkownicy przepływu znajdują się w Nowym Jorku, wybierz region Stany Zjednoczone. |
3. Wybierz pozycję **Utwórz środowisko**. Twoje nowe środowisko zostanie wyświetlone. 

Następnie dodaj użytkowników do środowiska.

## <a name="manage-your-existing-environments"></a>Zarządzanie istniejącymi środowiskami
1. W [centrum administratora usługi Microsoft Flow](https://admin.flow.microsoft.com) wybierz pozycję **Środowiska**:  
   ![](./media/environments-overview-admin/select-environments.png)  
2. Wybierz środowisko, aby otworzyć jego właściwości. 
3. Pozycja **Szczegóły** zawiera dodatkowe informacje o środowisku, w tym jego twórcę, lokalizację geograficzną i inne właściwości.  
   ![](./media/environments-overview-admin/open-environment.png)
4. Wybierz pozycję **Zabezpieczenia**. W ramach **ról środowiska** są dostępne dwie opcje: **Administrator** i **Twórca**:  
   
    ![](./media/environments-overview-admin/environment-roles.png)
   
    **Twórca** może tworzyć nowe zasoby w środowisku, takie jak przepływy, połączenia danych i bramy. 
   
   > [!NOTE]
   > Użytkownik nie musi być **Twórcą**, aby *edytować* zasoby w środowisku, ale musi nim być, aby tworzyć *nowe zasoby netto*. Twórca każdego zasobu może określić, kto może edytować ten zasób, a także może przyznać uprawnienia do edycji użytkownikom, którzy nie są twórcami w środowisku.
   > 
   > 
   
    **Administrator** może tworzyć zasady ochrony przed utratą danych, a także wypełniać zadania administracyjne, takie jak tworzenie środowisk, dodawanie użytkowników do środowisk i przypisywanie uprawnień administratora/twórcy.  
   
   1. Wybierz pozycję **Twórca środowiska** dla roli, a następnie wybierz pozycję **Użytkownicy**:  
      ![](./media/environments-overview-admin/add-environment-maker.png)
   2. Podaj nazwę, adres e-mail lub grupę użytkowników, której chcesz przypisać rolę Twórca. Gdy zaczniesz pisać, funkcja IntelliSense rozpocznie wyświetlanie listy użytkowników/grup pasujących do wpisanego tekstu. 
   3. Wybierz polecenie **Zapisz**, aby ukończyć dodawanie użytkowników. 
5. W obszarze **Zabezpieczenia** wybierz pozycję **Role użytkownika**:  
    ![](./media/environments-overview-admin/security-user-roles.png)
   
    Wyświetlone zostaną wszystkie istniejące role wraz z opcjami ich edycji lub usunięcia. 
   
    Wybierz pozycję **Nowa rola**, aby utworzyć nową rolę. 
6. W obszarze **Zabezpieczenia** wybierz pozycję **Zestawy uprawnień**:  
    ![](./media/environments-overview-admin/security-permission-set.png)
   
    Wyświetlone zostaną wszystkie zestawy uprawnień wraz z opcjami edycji lub usunięcia roli. 
   
    Wybierz pozycję **Nowy zestaw uprawnień**, aby utworzyć nowy zestaw uprawnień. 
7. W bloku **Baza danych** możesz wybrać utworzenie bazy danych do przechowywania danych. Ta baza danych jest częścią usługi Common Data Service.

## <a name="commonly-asked-questions"></a>Często zadawane pytania
##### <a name="can-i-migrate-a-microsoft-flow-in-my-us-environment-to-a-europe-environment"></a>Czy mogę przeprowadzić migrację usługi Microsoft Flow ze środowiska USA do środowiska Europa?
Nie, nie można przenosić przepływów między środowiskami. Należy utworzyć przepływ ponownie w innym środowisku.

##### <a name="which-license-includes-the-common-data-service"></a>Która licencja obejmuje usługę Common Data Service?
Tylko licencja Plan 2 usługi Microsoft PowerApps zawiera prawa do tworzenia baz danych za pomocą usługi Common Data Service. Jednak wszystkie plany płatne (Plan 1 i Plan 2 usługi Microsoft Flow oraz Plan 1 i Plan 2 aplikacji Microsoft PowerApps) mają prawa do używania usługi Common Data Service.

[Cennik usługi Flow](https://flow.microsoft.com/pricing/) może pomóc wybrać odpowiedni plan.  

[Pytania dotyczące rozliczeń](billing-questions.md) zawierają niektóre z często zadawanych nam pytań, które warto przejrzeć. 

##### <a name="can-the-common-data-service-be-used-outside-of-an-environment"></a>Czy można użyć usługi Common Data Service poza środowiskiem?
Nie. Usługa Common Data Service wymaga środowiska. [Dowiedz się więcej](common-data-model-intro.md) na ten temat.

##### <a name="what-regions-include-microsoft-flow"></a>Które regiony obejmują usługę Microsoft Flow?
Usługa Microsoft Flow obsługuje większość regionów obsługiwanych przez usługę Office 365. Aby uzyskać więcej szczegółów, zobacz [przegląd regionów](regions-overview.md).

##### <a name="what-is-needed-to-create-my-own-custom-environment"></a>Co jest potrzebne do utworzenia własnego środowiska niestandardowego?
Wszyscy użytkownicy licencji Plan 2 usługi Microsoft Flow mogą tworzyć własne środowiska jako dodatek do środowiska domyślnego. Wszyscy użytkownicy usługi Microsoft Flow, w tym użytkownicy usługi Office 365 i wersji bezpłatnej, mogą używać środowisk utworzonych przez administratorów licencji Plan 2, ale nie mogą tworzyć własnych środowisk. 

