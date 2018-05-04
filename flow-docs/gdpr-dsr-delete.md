---
title: 'Microsoft Flow: RODO — żądania podmiotów danych dotyczące usuwania | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych RODO dotyczące usuwania przy użyciu usługi Microsoft Flow.
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/17/2018
ms.author: keweare
ms.openlocfilehash: d750ee2bc672d08bff940341349663b4721f9a57
ms.sourcegitcommit: 12fbfe22fedd780d42ef1d2febfd7a0769b4902e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="responding-to-gdpr-data-subject-delete-requests-for-microsoft-flow"></a>Reagowanie na żądania podmiotów danych RODO dotyczące usuwania przy użyciu usługi Microsoft Flow

„Prawo do bycia zapomnianym” przez usunięcie danych osobowych z danych klientów organizacji to kluczowa metoda ochrony stosowana w rozporządzeniu RODO. Usunięcie danych osobowych obejmuje usunięcie wszystkich danych oraz dzienników generowanych przez system, z wyjątkiem informacji z dzienników inspekcji.

Usługa Microsoft Flow pozwala użytkownikom na tworzenie przepływów pracy automatyzacji, które są krytyczną częścią typowych codziennych operacji organizacji. Gdy użytkownik opuszcza organizację, administrator musi ręcznie przejrzeć dane i zasoby utworzone przez użytkownika, a następnie zdecydować, czy należy usunąć niektóre z nich. Pewne dane osobowe są automatycznie usuwane po usunięciu konta użytkownika z usługi Azure Active Directory.

W poniższej tabeli przedstawiono automatycznie usuwane dane osobowe i dane, które wymagają ręcznego przejrzenia i usunięcia przez administratora:

|Wymagane ręczne przejrzenie i usunięcie|Automatyczne usunięcie po usunięciu użytkownika z usługi Azure Active Directory|
|------|------|
|Środowisko*|Dzienniki generowane przez system|
|Uprawnienia środowiska**|Historia uruchamiania|
|Przepływy|Zadania użytkownika|
|Uprawnienia przepływu|Brama |
|Szczegóły użytkownika|Uprawnienia do bramy |
|Połączenia*||
|Uprawnienia do połączenia||
|Łącznik niestandardowy*||
|Uprawnienia łącznika niestandardowego||

* Każdy z tych zasobów zawiera rekordy „Utworzony przez” i „Zmodyfikowany przez”, które zawierają dane osobowe. Ze względów bezpieczeństwa te rekordy zostaną zachowane aż do usunięcia zasobu.

* W przypadku środowisk zawierających bazę danych Common Data Service for Apps uprawnienia środowiska (czyli użytkownicy przypisani do ról Twórca środowiska i Administrator) są przechowywane jako rekordy w bazie danych usługi Common Data Service. Zobacz [Executing DSRs against Common Data Service Customer Data](https://go.microsoft.com/fwlink/?linkid=872251) (Wykonywanie żądań podmiotów danych dotyczących danych klientów usługi Common Data Service), aby uzyskać wskazówki dotyczące sposobu reagowania na żądania podmiotów danych w przypadku użytkowników usługi Common Data Service.

W przypadku danych i zasobów, które wymagają przeglądania ręcznego, usługa Microsoft Flow oferuje poniższe środowiska umożliwiające wyszukiwanie lub zmienianie danych osobowych określonego użytkownika:

* **Dostęp do witryny internetowej:** zaloguj się do [Centrum administracyjnego usługi PowerApps](https://admin.powerapps.com/) lub [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com/)

* **Dostęp do programu PowerShell:** [Polecenia cmdlet programu PowerShell w usłudze PowerApps dla administratorów](https://go.microsoft.com/fwlink/?linkid=871804) 

Poniżej przedstawiono podział środowisk dostępnych dla administratora, w których może on usuwać poszczególne typy danych osobowych w obrębie każdego typu zasobu:

|Zasoby zawierające dane osobowe|Dostęp do witryny internetowej|Dostęp do programu PowerShell|Zautomatyzowane usuwanie|
|-----|----|----|----|
|Dzienniki generowane przez system|[Portal zaufania usługi Office 365](https://servicetrust.microsoft.com/)|||
|Środowisko|Centrum administracyjne usługi Microsoft Flow|Polecenia cmdlet usługi PowerApps||
|Uprawnienia środowiska*|Centrum administracyjne usługi Microsoft Flow|Polecenia cmdlet usługi PowerApps||
|Historia uruchamiania||| Usuwanie na podstawie zasad przechowywania przez 28 dni|
|Źródło działań ||Polecenia cmdlet usługi PowerApps||
|Zadania użytkownika|| ||
|Przepływy|Portal twórców w usłudze Microsoft**|||
|Uprawnienia przepływu|Portal twórców w usłudze Microsoft Flow|||
|Szczegóły użytkownika|| ||
|Połączenia|Portal twórców w usłudze Microsoft Flow| ||
|Uprawnienia do połączenia|Portal twórców w usłudze Microsoft Flow| ||
|Łącznik niestandardowy|Portal twórców w usłudze Microsoft Flow| ||
|Uprawnienia łącznika niestandardowego|Portal twórców w usłudze Microsoft Flow| ||
|Historia zatwierdzania|Portal twórców w usłudze Microsoft PowerApps*|||

* Jeśli po wprowadzeniu usługi Common Data Service for Apps baza danych jest tworzona w środowisku, uprawnienia środowiska i oparte na modelu uprawnienia aplikacji są przechowywane jako rekordy w wystąpieniu bazy danych usługi Common Data Service for Apps. Zobacz [Executing DSRs against Common Data Service Customer Data](https://go.microsoft.com/fwlink/?linkid=872251) (Wykonywanie żądań podmiotów danych dotyczących danych klientów usługi Common Data Service), aby uzyskać wskazówki dotyczące sposobu reagowania na żądania podmiotów danych w przypadku użytkowników usługi Common Data Service.

** Administrator będzie mógł uzyskiwać dostęp do tych zasobów z portalu twórców w usłudze Microsoft Flow tylko w sytuacji, gdy ma prawa dostępu przypisane w Centrum administracyjnym usługi Microsoft Flow.

## <a name="manage-delete-requests"></a>Zarządzanie żądaniami usunięcia

Poniższe kroki opisują, jak istniejące funkcje administracyjne obsługują żądania usunięcia dla rozporządzenia RODO.

> [!IMPORTANT]
> Aby uniknąć uszkodzenia danych, wykonaj poniższe kroki w podanej kolejności.
>
>

## <a name="list-and-re-assign-flows"></a>Tworzenie listy przepływów i ich ponowne przypisywanie

Te kroki mają na celu skopiowanie istniejących przepływów odchodzącego użytkownika. Po przypisaniu nowego prawa własności do kopii przepływy mogą nadal obsługiwać istniejące procesy biznesowe. Skopiowanie tych przepływów jest ważne w przypadku usuwania połączeń identyfikatorów osobistych z odchodzącym użytkownikiem. Należy ustanowić nowe połączenia w celu połączenia przepływu z innymi interfejsami API i aplikacjami SaaS.

1. Zaloguj się do [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com/), a następnie wybierz środowisko, które zawiera przepływy należące do usuwanego użytkownika.

    ![Wyświetlanie środowisk](./media/gdpr-dsr-delete/view-environments.png)

1. Wybierz kolejno pozycje **Zasoby** > **Przepływy**, a następnie wybierz tytuł przepływu, który chcesz ponownie przypisać.

    ![Wyświetlanie przepływów](./media/gdpr-dsr-delete/admin-view-flows.png)

1. Wybierz pozycję **Zarządzaj udostępnianiem**.

    ![Zarządzanie udostępnianiem](./media/gdpr-dsr-delete/admin-manage-sharing.png)

1. W panelu **Udostępnianie** wyświetlonym przy prawej krawędzi dodaj siebie jako właściciela, a następnie wybierz pozycję **Zapisz**.

    ![Udostępnianie przepływu](./media/gdpr-dsr-delete/flow-sharing-save.png)

1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com/), wybierz opcję **Moje przepływy**, a następnie wybierz pozycję **Przepływy zespołu**.

1. Wybierz wielokropek **(...)** dla przepływu do skopiowania, a następnie wybierz pozycję **Zapisz jako**.

    ![Zapisywanie przepływu za pomocą polecenia Zapisz jako](./media/gdpr-dsr-delete/flow-save-as.png)

1. Skonfiguruj połączenia zgodnie z wymaganiami, a następnie wybierz pozycję **Kontynuuj**.

1. Podaj nową nazwę, a następnie wybierz pozycję **Zapisz**.

    ![Tworzenie kopii przepływu](./media/gdpr-dsr-delete/create-copy-flow.png)

1. Nowa wersja przepływu pojawi się w obszarze **Moje przepływy**, w którym będzie można w razie potrzeby udostępnić ją innym użytkownikom.

    ![Przepływy zespołu](./media/gdpr-dsr-delete/team-flows.png)

1. Usuń oryginalny przepływ, wybierając odpowiedni wielokropek **(...)** i pozycję **Usuń**, a następnie wybierz ponownie pozycję **Usuń** po wyświetleniu monitu. Ten krok spowoduje również usunięcie podstawowych identyfikatorów osobistych, które uwzględniono w zależnościach systemowych między użytkownikiem a usługą Microsoft Flow.

    ![Potwierdzenie usunięcia przepływu](./media/gdpr-dsr-delete/delete-flow-confirmation.png)

1. Włącz kopię przepływu, otwierając obszar **Moje przepływy**, a następnie przełączając kontrolkę do położenia **Wł.**
    ![Włączanie przepływu](./media/gdpr-dsr-delete/toggle-on.png)

1. Teraz kopia wykonuje tę samą logikę przepływu pracy, co wersja oryginalna.

## <a name="delete-approval-history-from-microsoft-flow"></a>Usuwanie historii zatwierdzania z usługi Microsoft Flow

 Dane zatwierdzania usługi Microsoft Flow są przechowywane w bieżącej lub poprzedniej wersji usługi Common Data Service for Apps. W ramach zatwierdzania informacje osobiste istnieją w formie przypisań zatwierdzeń i komentarzy zawartych w odpowiedzi na żądanie zatwierdzenia. Administratorzy mogą uzyskiwać dostęp do danych, wykonując następujące kroki:

1. Zaloguj się do usługi [PowerApps](https://web.powerapps.com/).

1. Wybierz pozycję **Dane**, a następnie wybierz pozycję **Jednostki**.

1. Wybierz wielokropek **(...)** dla jednostki **Zatwierdzenie przepływu**, a następnie otwórz dane w programie Microsoft Excel.

1. W programie Microsoft Excel wyszukuj, filtruj, a następnie usuwaj dane zgodnie z potrzebami.

Zobacz [Executing DSRs against Common Data Service Customer Data](https://go.microsoft.com/fwlink/?linkid=872251) (Wykonywanie żądań podmiotów danych dotyczących danych klientów usługi Common Data Service), aby uzyskać dodatkowe wskazówki dotyczące sposobu reagowania na żądania podmiotów danych w przypadku użytkowników usługi Common Data Service.

## <a name="delete-connections-created-by-a-user"></a>Usuwanie połączeń utworzonych przez użytkownika

Połączenia są używane w kombinacji z łącznikami w celu ustanowienia łączności z innymi interfejsami API i systemami SaaS.  Połączenia obejmują odwołania do użytkownika, który je utworzył, i w związku z tym można je usunąć, aby usunąć wszystkie odwołania do użytkownika.

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla twórców

Użytkownik może usunąć wszystkie połączenia za pomocą funkcji Remove-Connection należącej do [poleceń cmdlet programu PowerShell w usłudze PowerApps dla twórców](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connections for the calling user and deletes them
Get-Connection | Remove-Connection
```

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla administratorów

Niedostępne.

## <a name="delete-the-users-permissions-to-shared-connections"></a>Usuwanie uprawnień użytkownika do połączeń udostępnionych

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla twórców

Użytkownik może usunąć wszystkie swoje przypisania roli połączenia dla połączeń udostępnionych przy użyciu funkcji Remove-ConnectionRoleAssignment należącej do [poleceń cmdlet programu PowerShell w usłudze PowerApps dla twórców](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connection role assignments for the calling users and deletes them
Get-ConnectionRoleAssignment | Remove-ConnectionRoleAssignment
```

> [!NOTE]
> Przypisań roli Właściciel nie można usunąć bez wcześniejszego usunięcia zasobów połączenia.
>
>

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla administratorów

Niedostępne.

## <a name="delete-custom-connectors-created-by-the-user"></a>Usuwanie łączników niestandardowych utworzonych przez użytkownika

Łączniki niestandardowe uzupełniają istniejące wbudowane łączniki i umożliwiają łączność z innymi interfejsami API, usługami SaaS i systemami opracowanymi w sposób niestandardowy. Łączniki niestandardowe obejmują odwołania do użytkownika, który je utworzył, i w związku z tym można je usunąć, aby usunąć wszystkie odwołania do użytkownika.

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla twórców

Użytkownik może usunąć wszystkie swoje łączniki niestandardowe za pomocą funkcji Remove-Connector należącej do [poleceń cmdlet programu PowerShell w usłudze PowerApps dla twórców](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all custom connectors for the calling user and deletes them
Get-Connector -FilterNonCustomConnectors | Remove-Connector
```

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla administratorów

Niedostępne.

## <a name="delete-the-users-permissions-to-shared-custom-connectors"></a>Usuwanie uprawnień użytkownika do udostępnionych łączników niestandardowych

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla twórców

Użytkownik może usunąć wszystkie przypisania roli łącznika dla udostępnionego łącznika niestandardowego przy użyciu funkcji Remove-ConnectorRoleAssignment należącej do [poleceń cmdlet programu PowerShell w usłudze PowerApps dla twórców](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connector role assignments for the calling users and deletes them
Get-ConnectorRoleAssignment | Remove-ConnectorRoleAssignment
```

> [!NOTE]
> Przypisań roli Właściciel nie można usunąć bez wcześniejszego usunięcia zasobów połączenia.
>
>

Polecenia cmdlet programu PowerShell w usłudze PowerApps dla administratorów

Niedostępne.

## <a name="delete-or-reassign-all-environments-created-by-the-user"></a>Usuwanie lub ponowne przypisywanie wszystkich środowisk utworzonych przez użytkownika

Jako administrator podczas przetwarzania żądania podmiotu danych dotyczącego usunięcia musisz podjąć dwie decyzje w stosunku do każdego użytkownika w każdym środowisku utworzonym przez użytkownika:

1. Jeśli stwierdzisz, że środowisko nie jest używane przez inną osobę w organizacji, możesz wybrać opcję usunięcia środowiska.
1. Jeśli stwierdzisz, że środowisko jest nadal wymagane, możesz wybrać opcję rezygnacji z usunięcia środowiska i dodać siebie (lub innego użytkownika w organizacji) jako administratora środowiska.
    > [!IMPORTANT]
    > Usunięcie środowiska spowoduje trwałe usunięcie wszystkich zasobów w obrębie środowiska, w tym wszystkich aplikacji, przepływów, połączeń, itp., dlatego przed usunięciem przejrzyj zawartość środowiska.
    >
    >

## <a name="give-access-to-a-users-environments-from-the-microsoft-flow-admin-center"></a>Nadawanie praw dostępu do środowisk użytkownika z poziomu Centrum administracyjnego usługi Microsoft Flow

Administrator może nadać prawa dostępu administratora do środowiska utworzonego przez określonego użytkownika z poziomu [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com/). Aby uzyskać więcej informacji na temat administrowania środowiskami, przejdź do tematu [Używanie środowisk za pomocą usługi Microsoft Flow](https://docs.microsoft.com/flow/environments-overview-admin).

## <a name="delete-the-users-permissions-to-all-other-environments"></a>Usuwanie uprawnień użytkownika do wszystkich innych środowisk

Użytkownikom można przypisać uprawnienia (na przykład administrator środowiska, twórca środowiska itp.) w środowisku przechowywanym w usłudze Microsoft Flow jako „przypisanie roli”.

Jeśli po wprowadzeniu usługi Common Data Service for Apps baza danych jest tworzona w środowisku, „przypisania roli” są przechowywane jako rekordy w wystąpieniu bazy danych usługi Common Data Service for Apps.

Aby uzyskać więcej informacji o usuwaniu uprawnienia użytkownika w środowisku, przejdź do tematu [Używanie środowisk za pomocą usługi Microsoft Flow](https://docs.microsoft.com/flow/environments-overview-admin).
