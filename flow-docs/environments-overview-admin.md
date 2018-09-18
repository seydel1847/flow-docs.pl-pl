---
title: Omówienie środowiska dla administratorów | Microsoft Docs
description: Używanie i tworzenie środowisk w usłudze Microsoft Flow oraz zarządzanie nimi
services: ''
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2017
ms.author: sunayv
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: b9dd1fd2f3c00870b0a713f50cc567d5d79385d8
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690634"
---
# <a name="using-environments-within-microsoft-flow"></a>Używanie środowisk za pomocą usługi Microsoft Flow

## <a name="benefits"></a>Korzyści

Środowiska oferują następujące korzyści:

* **Lokalizacja danych**: środowiska można tworzyć w różnych regionach, z którymi są one później powiązane. Po utworzeniu przepływu w środowisku jest on kierowany do wszystkich centrów danych w tej lokalizacji geograficznej. Zapewnia to również korzyści wynikające ze wzrostu wydajności.

    Jeśli użytkownicy znajdują się w Europie, środowisko należy utworzyć i korzystać z niego w regionie Europa. Jeśli użytkownicy znajdują się w Stanach Zjednoczonych, środowisko należy utworzyć i korzystać z niego w regionie Stany Zjednoczone. 

    > [!IMPORTANT]
    > Jeśli usuniesz środowisko, wszystkie przepływy w tym środowisku zostaną także usunięte. To dotyczy wszelkich elementów utworzonych w środowisku, w tym połączeń, bram, aplikacji PowerApps i innych.
* **Ochrona przed utratą danych**: dla administratora nie są pożądane przepływy, które pobierają dane z lokalizacji wewnętrznych (takich jak usługa *OneDrive dla Firm* lub lista programu SharePoint zawierająca informacje o wynagrodzeniach), a następnie publikują je publicznie (na przykład w serwisie *Twitter*). Ochrona przed utratą danych umożliwia kontrolowanie usług, które mogą udostępniać dane w ramach wdrożenia usługi Microsoft Flow.

    Można na przykład dodać usługi *SharePoint* i *OneDrive dla Firm* do zasad wymagających używania tylko danych biznesowych. Wszystkie przepływy utworzone w tym środowisku mogą używać usług *SharePoint* i *OneDrive dla Firm*. Nie będą one mogły jednak udostępniać danych innym usługom nieuwzględnionym przez zasady wymagające używania tylko danych biznesowych.

  > [!NOTE]
  > Zasady ochrony przed utratą danych są dostępne w przypadku niektórych jednostek SKU licencji, w tym licencji P2.

* **Granica izolacji dla wszystkich zasobów**: wszystkie przepływy, bramy, połączenia, łączniki niestandardowe itd. znajdują się w tym konkretnym środowisku. Nie istnieją one w innych środowiskach.
* **Common Data Service**: oto opcje tworzenia przepływu wstawiającego dane do usługi:

  * Wstawienie danych do pliku programu Excel i zapisanie tego pliku w ramach konta magazynu w chmurze, takiego jak usługa OneDrive.
  * Utworzenie bazy danych SQL Database i przechowywanie w niej danych.
  * Użycie usługi Common Data Service do przechowywania danych.

    Każde środowisko może mieć maksymalnie jedną bazę danych przepływów w usłudze Common Data Service. Dostęp do usługi Common Data Service zależy od zakupionej licencji; usługa Common Data Service nie jest dołączana do bezpłatnej licencji.

## <a name="limitations"></a>Ograniczenia

Mimo że środowiska oferują wiele korzyści, z ich używaniem wiążą się również nowe ograniczenia. Fakt, że środowiska znajdują się w granicach izolacji, oznacza, że nigdy nie mogą istnieć zasoby odwołujące się do zasobów *między* środowiskami. Nie można na przykład utworzyć łącznika niestandardowego w jednym środowisku i utworzyć przepływu używającego tego łącznika niestandardowego w innym środowisku.

## <a name="use-the-default-environment"></a>Użycie środowiska domyślnego

Środowisko **domyślne** jest udostępniane wszystkim użytkownikom, a każdy użytkownik może tworzyć przepływy w środowisku **domyślnym**.

> [!TIP]
> Jeśli jesteś użytkownikiem wersji zapoznawczej, wszystkie istniejące przepływy znajdują się w środowisku domyślnym. *Użytkownik wersji zapoznawczej* to osoba, która używała usługi Microsoft Flow przed jej ogólnym udostępnieniem.

## <a name="the-admin-center"></a>Centrum administratora

Administratorzy mogą używać centrum administratora do tworzenia środowisk i zarządzania nimi. Centrum administratora można otworzyć na dwa sposoby:

### <a name="option-1-select-settings"></a>Opcja 1. Wybranie pozycji Ustawienia

1. Zaloguj się do witryny [flow.microsoft.com](https://flow.microsoft.com).
1. Wybierz pozycję Ustawienia (koło zębate), a następnie z listy wybierz pozycję **Centrum administratora**:

   ![Ustawienia i Portal administratora](./media/environments-overview-admin/settings.png)
1. Zostanie otwarte centrum administratora.

### <a name="option-2-open-adminflowmicrosoftcom"></a>Opcja 2. Otwarcie witryny admin.flow.microsoft.com

Przejdź do witryny [admin.flow.microsoft.com](https://admin.flow.microsoft.com) i zaloguj się przy użyciu konta służbowego.

## <a name="create-an-environment"></a>Tworzenie środowiska

1. W [centrum administratora usługi Microsoft Flow](https://admin.flow.microsoft.com) wybierz pozycję **Środowiska**. Zobaczysz wszystkie istniejące środowiska: ![Środowiska](./media/environments-overview-admin/environments-list.png)
2. Wybierz pozycję **Nowe środowisko**, a następnie podaj wymagane informacje:


   |     Właściwość     |                                                 Opis                                                 |
   |------------------|-------------------------------------------------------------------------------------------------------------|
   | Nazwa środowiska |              Podaj nazwę środowiska, taką jak `Human Resources` lub `Europe flows`.              |
   |      Region      | Wybierz lokalizację na potrzeby hostowania środowiska. W celu uzyskania najwyższej wydajności należy użyć regionu, który jest najbliżej użytkowników. |
   | Typ środowiska |                  Wybierz typ środowiska zgodnie ze swoją licencją: Produkcja lub Wersja próbna.                   |

     ![ustawienia środowiska](./media/environments-overview-admin/new-environment-dialog.png)
3. Kliknij pozycję **Utwórz środowisko**.
4. Masz teraz dostępne następujące opcje: **Utwórz bazę danych** lub **Pomiń**.
5. Jeśli wybierz opcję **utworzenia bazy danych**, pojawi się monit o określenie **waluty** i **języka** bazy danych. Ponadto możesz wybrać opcję wdrożenia przykładowych aplikacji i danych.

   ![ustawienia konfiguracji bazy danych](./media/environments-overview-admin/create-database-dialog2.png)


Teraz możesz dodać użytkowników do środowiska.

## <a name="manage-your-existing-environments"></a>Zarządzanie istniejącymi środowiskami

1. W [centrum administratora usługi Microsoft Flow](https://admin.flow.microsoft.com) wybierz pozycję **Środowiska**:

   ![element menu środowisk](./media/environments-overview-admin/select-environments.png)
1. Wybierz środowisko, aby otworzyć jego właściwości.
1. Użyj pozycji **Szczegóły**, aby wyświetlić dodatkowe informacje o środowisku, w tym jego twórcę, lokalizację geograficzną i inne właściwości:

   ![karta szczegółów](./media/environments-overview-admin/open-environment.png)
1. Wybierz pozycję **Zabezpieczenia**.

    Jeśli w poprzednich krokach nie wybrano pozycji **Utwórz bazę danych**, w obszarze **Role środowiska** dostępne są dwie opcje: **Administrator środowiska** i **Twórca środowiska** :

    ![role administratora](./media/environments-overview-admin/environment-roles.png)

    **Twórca** może tworzyć nowe zasoby, takie jak przepływy, połączenia danych i bramy, w środowisku.

   > [!NOTE]
   > Użytkownik nie musi być **twórcą**, aby *edytować* zasoby w środowisku. Każdy twórca określa, kto może edytować jego zasoby, przyznając uprawnienia użytkownikom niebędącym twórcami środowisk.
   > 
   > 

    **Administrator** może tworzyć zasady ochrony przed utratą danych, a także wykonywać inne zadania administracyjne, takie jak tworzenie środowisk, dodawanie użytkowników do środowisk i przypisywanie uprawnień administratora/twórcy.

   1. Wybierz rolę **Twórca środowiska**, a następnie wybierz pozycję **Użytkownicy**: ![rola twórcy](./media/environments-overview-admin/add-environment-maker.png)
   1. Wprowadź nazwę, adres e-mail lub grupę użytkowników, do której chcesz przypisać rolę **Twórca**.
   1. Wybierz pozycję **Zapisz**.

1. W obszarze **Zabezpieczenia** wybierz pozycję **Role użytkownika**:

    ![role użytkowników](./media/environments-overview-admin/security-user-roles.png)

    Wyświetlone zostaną wszystkie istniejące role wraz z opcjami ich edycji lub usunięcia.

    Wybierz pozycję **Nowa rola**, aby utworzyć nową rolę.
1. W obszarze **Zabezpieczenia** wybierz pozycję **Zestawy uprawnień**:

    ![ustawienie uprawnienia](./media/environments-overview-admin/security-permission-set.png)

    Zostaną wyświetlone wszystkie istniejące zestawy uprawnień i opcje edytowania lub usuwania ról.

    Wybierz pozycję **Nowy zestaw uprawnień**, aby utworzyć nowy zestaw uprawnień.
1. W przypadku wybrania pozycji **Utwórz bazę danych** w celu przechowywania danych ta baza danych jest częścią usługi Common Data Service. Po kliknięciu karty **Zabezpieczenia** pojawi się monit o przejście do **Centrum zarządzania wystąpieniem usługi Dynamics 365**, w którym można stosować zabezpieczenia oparte na rolach.
![ustawienia zabezpieczeń usługi dynamics](./media/environments-overview-admin/Security-Link-D365.png)

1. Wybierz użytkownika z listy użytkowników w środowisku/wystąpieniu.
  ![ustawienia zabezpieczeń usługi dynamics](./media/environments-overview-admin/D365-Select-User.png)

1. Przypisz rolę do użytkownika.

   ![przypisywanie roli do użytkownika](./media/environments-overview-admin/D365-Assign-Role.png)

> [!NOTE]
> Użytkownicy lub grupy przypisane do ról w środowisku nie mają automatycznie przyznawanego dostępu do bazy danych środowiska (jeśli istnieje) — te prawa dostępu musi oddzielnie przyznać właściciel bazy danych. 
>
>

### <a name="database-security"></a>Zabezpieczenia bazy danych
Możliwość tworzenia i modyfikowania schematu bazy danych oraz łączenia z danymi przechowywanymi w bazie danych aprowizowanej w środowisku jest kontrolowana przez zestawy uprawnień i role użytkownika bazy danych. Rolami użytkowników i zestawami ustawień bazy danych środowiska można zarządzać w sekcjach **Role użytkownika** i **Zestawy uprawnień** karty **Zabezpieczenia**. 

   ![przypisywanie roli do użytkownika](./media/environments-overview-admin/D365-Assign-Role.png)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="can-i-move-a-flow-between-environments"></a>Czy mogę przenieść przepływ między środowiskami?

Tak, przepływy można wyeksportować z jednego środowiska i zaimportować do innego środowiska.

### <a name="which-license-includes-the-common-data-service"></a>Która licencja obejmuje usługę Common Data Service?

Tylko licencja Plan 2 usługi Microsoft PowerApps zawiera prawa do tworzenia baz danych za pomocą usługi Common Data Service. Jednak wszystkie plany płatne (Plan 1 i Plan 2 usługi Microsoft Flow oraz Plan 1 i Plan 2 aplikacji Microsoft PowerApps) mają prawa do używania usługi Common Data Service.

Wybierz odpowiadający Ci plan, odwiedzając stronę [cennika usługi Microsoft Flow](https://flow.microsoft.com/pricing/).

Odpowiedzi na często zadawane pytania dotyczące rozliczeń można znaleźć w dokumencie [Pytania dotyczące rozliczeń](billing-questions.md).

### <a name="can-the-common-data-service-be-used-outside-of-an-environment"></a>Czy można użyć usługi Common Data Service poza środowiskiem?

Nie. Usługa Common Data Service wymaga środowiska. [Dowiedz się więcej](common-data-model-intro.md) na ten temat.

### <a name="what-regions-include-microsoft-flow"></a>Które regiony obejmują usługę Microsoft Flow?

Usługa Microsoft Flow obsługuje większość regionów obsługiwanych przez usługę Office 365. Aby uzyskać więcej szczegółów, zobacz [omówienie regionów](regions-overview.md).

### <a name="whats-needed-to-create-my-own-custom-environment"></a>Co jest potrzebne do utworzenia własnego środowiska niestandardowego?

Wszyscy użytkownicy licencji Plan 2 usługi Microsoft Flow mogą tworzyć własne środowiska. Wszyscy użytkownicy usługi Microsoft Flow mogą używać środowisk utworzonych przez administratorów licencji Plan 2, ale nie mogą tworzyć własnych środowisk.
