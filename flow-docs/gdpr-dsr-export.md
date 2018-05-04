---
title: 'Microsoft Flow: RODO — żądania podmiotów danych dotyczące eksportowania | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych RODO dotyczące eksportowania przy użyciu usługi Microsoft Flow.
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
ms.openlocfilehash: 1e1fe346ba6ffb264985da0115714246a621ef5a
ms.sourcegitcommit: 12fbfe22fedd780d42ef1d2febfd7a0769b4902e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="responding-to-gdpr-data-subject-export-requests-for-microsoft-flow"></a>Reagowanie na żądania podmiotów danych RODO dotyczące eksportowania przy użyciu usługi Microsoft Flow

W ramach naszego zobowiązania do współpracy z Tobą podczas podróży do wprowadzenia Ogólnego rozporządzenia o ochronie danych (RODO) opracowaliśmy dokumentację, która pomoże Ci się przygotować. W tej dokumentacji nie tylko opisano czynności wykonywane przez nas w celu przygotowania do wprowadzenia RODO, ale także udostępniono przykłady kroków, które można wykonać dzisiaj z pomocą firmy Microsoft w celu uzyskania zgodności z rozporządzeniem RODO w przypadku korzystania z usługi Microsoft Flow.

## <a name="manage-export-requests"></a>Zarządzanie żądaniami eksportowania

*Prawo do przenoszenia danych* umożliwia osobie, której dane dotyczą, zażądanie kopii jej danych osobowych w formacie elektronicznym (czyli „formacie strukturyzowanym, powszechnie używanym, umożliwiającym odczyt maszynowy i międzyoperacyjnym”), który pozwala na ich przesyłanie do innego kontrolera danych.

Usługa Microsoft Flow oferuje następujące środowiska umożliwiające wyszukiwanie lub eksportowanie danych osobowych określonego użytkownika:

* **Dostęp do witryny internetowej:** zaloguj się do [Centrum administracyjnego usługi PowerApps](https://admin.powerapps.com/) lub [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com/).

* **Dostęp do programu PowerShell:** [Polecenia cmdlet programu PowerShell w usłudze PowerApps dla administratorów ](https://go.microsoft.com/fwlink/?linkid=871804).

|**Dane klienta**|**Dostęp do witryny internetowej**|**Dostęp do programu PowerShell**|
|-----------------|------------------|-------------------|
|Dzienniki generowane przez system|[Portal zaufania usługi Office 365](https://servicetrust.microsoft.com/)|
|Historia uruchamiania|Portal twórców w usłudze Microsoft Flow||
|Zadania użytkownika|| |
|Przepływy|Portal twórców w usłudze Microsoft Flow||
|Uprawnienia przepływu| Portal twórców w usłudze Microsoft Flow i Centrum administracyjne usługi Microsoft Flow||
|Szczegóły użytkownika|| |
|Połączenia|Portal twórców w usłudze Microsoft Flow| |
|Uprawnienia do połączenia|Portal twórców w usłudze Microsoft Flow| |
|Łączniki niestandardowe|Portal twórców w usłudze Microsoft Flow| |
|Uprawnienia łącznika niestandardowego|Portal twórców w usłudze Microsoft Flow| |
|Brama|Portal twórców w usłudze Microsoft Flow|Polecenia cmdlet programu PowerShell w bramie lokalnej|
|Uprawnienia do bramy|Portal twórców w usłudze Microsoft Flow|

## <a name="export-a-flow"></a>Eksportowanie przepływu

Użytkownik końcowy lub administrator, który przyznał sobie prawa dostępu do przepływu, może wyeksportować przepływ, wykonując następujące kroki:

1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com/).

1. Wybierz link **Moje przepływy**, a następnie wybierz przepływ do wyeksportowania.

1. Wybierz pozycję **... Więcej**, a następnie wybierz pozycję **Eksportuj**.

    ![Eksportowanie przepływu](./media/gdpr-dsr-export/export-flow.png)

1. Wybierz pozycję **Pakiet (plik ZIP)**.

Twój przepływ będzie teraz dostępny jako pakiet skompresowany. Aby uzyskać więcej informacji, zobacz wpis w blogu dotyczący [sposobu eksportowania i importowania przepływu](https://flow.microsoft.com/blog/import-export-bap-packages/).

## <a name="export-run-history"></a>Eksportowanie historii przebiegów

Historia przebiegów zawiera listę wszystkich wykonań, które przeprowadzono w przypadku przepływu. Te dane obejmują stan przepływu, czas rozpoczęcia, czas trwania oraz dane wejściowe/wyjściowe wyzwalaczy i akcji.

Użytkownik końcowy lub administrator, który przyznał sobie prawa dostępu do przepływu w Centrum administracyjnym usługi Microsoft Flow, może wykonać poniższe kroki, aby wyeksportować te dane:

1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com/).
1. Wybierz link **Moje przepływy**, a następnie wybierz przepływ, dla którego chcesz wyeksportować historię przebiegów.
1. W okienku **HISTORIA PRZEBIEGÓW** wybierz pozycję **Zobacz wszystko**.

    ![Historia uruchamiania](./media/gdpr-dsr-export/run-history.png)

1. Wybierz pozycję **Pobierz plik CSV**.

    ![Pobieranie pliku CSV](./media/gdpr-dsr-export/download-csv.png)

Historia przebiegów jest pobierana jako plik CSV, dzięki czemu można ją otworzyć w programie Microsoft Excel lub edytorze tekstów, a następnie przeanalizować uzyskane wyniki.

## <a name="export-a-users-activity-feed"></a>Eksportowanie źródła działań użytkownika

W usłudze [Microsoft Flow](https://flow.microsoft.com/) źródło działań pokazuje historię działań, niepowodzeń i powiadomień użytkownika. Każdy użytkownik może przeglądać swoje źródło działań, wykonując następujące kroki:

1. Zaloguj się do usługi [Microsoft Flow](http://flow.microsoft.com/), wybierz ikonę dzwonka w pobliżu prawego górnego rogu, a następnie wybierz pozycję **Pokaż wszystkie działania**.

    ![Pokazywanie źródła działań](./media/gdpr-dsr-export/show-activity-feed.png)

1. Na ekranie **Działania** skopiuj wyniki, a następnie wklej je w edytorze dokumentów, takim jak program Microsoft Word.

    ![Pokazywanie źródła działań](./media/gdpr-dsr-export/export-activity-feed.png)

## <a name="export-a-users-connections"></a>Eksportowanie połączeń użytkownika

Połączenia pozwalają na nawiązywanie połączeń z interfejsami API, aplikacjami SaaS oraz systemami innych firm. Wykonaj następujące kroki, aby wyświetlić swoje połączenia:

1. Zaloguj się do usługi [Microsoft Flow](http://flow.microsoft.com/), wybierz ikonę koła zębatego w pobliżu prawego górnego rogu, a następnie wybierz pozycję **Połączenia**.

    ![Pokazywanie połączeń](./media/gdpr-dsr-export/show-connections.png)
1. Skopiuj wyniki, a następnie wklej je w edytorze dokumentów, takim jak program Microsoft Word.

## <a name="export-a-list-of-a-users-connection-permissions"></a>Eksportowanie listy uprawnień połączeń uprawnień użytkownika

Użytkownik może eksportować przypisania ról wszystkich połączeń, do których ma dostęp, za pośrednictwem funkcji Get-ConnectionRoleAssignment należącej do [poleceń cmdlet programu PowerShell w usłudze PowerApps](https://go.microsoft.com/fwlink/?linkid=871804).
![Eksportowanie uprawnień połączenia](./media/gdpr-dsr-export/export-connection-permissions.png)

## <a name="export-a-users-custom-connectors"></a>Eksportowanie łączników niestandardowych użytkownika

Łączniki niestandardowe uzupełniają wbudowane łączniki i umożliwiają łączność z innymi interfejsami API, usługami SaaS i systemami opracowanymi w sposób niestandardowy. Prawo własności łącznika niestandardowego można przenieść lub usunąć łącznik.

Wykonaj następujące kroki, aby wyeksportować listę łączników klienta:

1. Przejdź do usługi [Microsoft Flow](https://flow.microsoft.com).
1. Wybierz ikonę ustawień przedstawiającą **koło zębate**.
1. Wybierz pozycję **Łączniki niestandardowe**.
1. Skopiuj i wklej listę łączników niestandardowych w edytorze tekstów, takim jak program Microsoft Word.

    ![Eksportowanie łączników niestandardowych](./media/gdpr-dsr-export/export-custom-connectors.png)

Oprócz środowiska pracy oferowanego w usłudze Microsoft Flow, do wyeksportowania wszystkich łączników niestandardowych możesz użyć funkcji Get-Connector należącej do [poleceń cmdlet programu PowerShell w usłudze PowerApps](https://go.microsoft.com/fwlink/?linkid=871804).

![Eksportowanie łączników niestandardowych w programie PowerShell](./media/gdpr-dsr-export/export-custom-connectors-powershell.png)

## <a name="export-a-users-custom-connector-permissions"></a>Eksportowanie uprawnień łączników niestandardowych użytkownika

Użytkownik może wyeksportować wszystkie uprawnienia łączników niestandardowych utworzone za pośrednictwem funkcji Get-ConnectorRoleAssignment należącej do [poleceń cmdlet programu PowerShell w usłudze PowerApps](https://go.microsoft.com/fwlink/?linkid=871804).

![Eksportowanie uprawnień łączników niestandardowych w programie PowerShell](./media/gdpr-dsr-export/export-connector-permissions.png)

## <a name="export-approval-history"></a>Eksportowanie historii zatwierdzania

Historia zatwierdzania w usłudze Microsoft Flow umożliwia przechwytywanie historycznego rekordu zatwierdzeń, które zostały odebrane przez użytkownika lub do niego wysłane. Każdy użytkownik może przeglądać swoją historię zatwierdzania, wykonując następujące czynności:

1. Zalogowanie do usługi [Microsoft Flow](http://flow.microsoft.com/), wybranie pozycji **Zatwierdzenia**, a następnie wybranie pozycji **Historia**.

    ![Wyświetlanie historii zatwierdzania](./media/gdpr-dsr-export/view-approval-history.png)

1. Lista zawiera zatwierdzenia odebrane przez użytkownika. Użytkownicy mogą wyświetlać wysłane do nich zatwierdzenia, wybierając strzałkę w dół obok pozycji **Odebrane**, a następnie wybierając pozycję **Wysłane**.

    ![Wyświetlanie odebranych zatwierdzeń](./media/gdpr-dsr-export/view-received-approvals.png)
