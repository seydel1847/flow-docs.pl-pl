---
title: 'Microsoft Flow: RODO — żądania podmiotów danych dotyczące eksportowania w przypadku kont Microsoft (MSA) | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych RODO dotyczące eksportowania przy użyciu usługi Microsoft Flow w przypadku kont Microsoft.
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
ms.date: 5/25/2018
ms.author: keweare
ms.openlocfilehash: 6c1bf3038020f56e5eae57e345391ace2fe65d7f
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34563321"
---
# <a name="responding-to-gdpr-data-subject-export-requests-for-microsoft-flow"></a>Reagowanie na żądania podmiotów danych RODO dotyczące eksportowania przy użyciu usługi Microsoft Flow

W ramach naszego zobowiązania do współpracy z Tobą podczas podróży do wprowadzenia Ogólnego rozporządzenia o ochronie danych (RODO) opracowaliśmy dokumentację, która pomoże Ci się przygotować. W tej dokumentacji nie tylko opisano czynności wykonywane przez nas w celu przygotowania do wprowadzenia RODO, ale także udostępniono przykłady kroków, które można wykonać dzisiaj z pomocą firmy Microsoft w celu uzyskania zgodności z rozporządzeniem RODO w przypadku korzystania z usługi Microsoft Flow.

## <a name="manage-export-requests"></a>Zarządzanie żądaniami eksportowania

*Prawo do przenoszenia danych* umożliwia osobie, której dane dotyczą, zażądanie kopii jej danych osobowych w formacie elektronicznym (czyli „formacie strukturyzowanym, powszechnie używanym, umożliwiającym odczyt maszynowy i międzyoperacyjnym”), który pozwala na ich przesyłanie do innego kontrolera danych.

Skorzystaj z [pulpitu nawigacyjnego zachowania poufności informacji firmy Microsoft](https://account.microsoft.com/privacy/) lub usługi [Microsoft Flow](https://flow.microsoft.com/), aby znaleźć lub wyeksportować dane osobowe dla określonego użytkownika.

|Dane osobowe|Lokalizacja|
|-----------------|-------------------|
|Działania produktów i usług|Pulpit nawigacyjny zachowania poufności informacji firmy Microsoft|
|Przepływy|Portal twórców w usłudze Microsoft Flow|
|Historia uruchamiania|Portal twórców w usłudze Microsoft Flow|
|Kanał aktywności|Portal twórców w usłudze Microsoft Flow|
|Połączenia|Portal twórców w usłudze Microsoft Flow|

## <a name="export-product-and-service-activity"></a>Eksportowanie działań produktów i usług

1. Zaloguj się do [pulpitu nawigacyjnego zachowania poufności informacji firmy Microsoft](https://account.microsoft.com/privacy/), używając swojego konta Microsoft (MSA).
1. Wybierz pozycję **Historia działań**.

    ![Historia działań](./media/gdpr-dsr-export-msa/activityhistory.png) Możesz przeglądać historię działań dla różnych aplikacji i usług firmy Microsoft, których używasz.
1. Aby wyeksportować dane **działań produktów i usług**, wybierz pozycję **Pobierz dane**, a następnie wybierz pozycję **UTWÓRZ NOWE ARCHIWUM**.

    ![Pobieranie danych](./media/gdpr-dsr-export-msa/downloaddata.png)

1. Wybierz pozycję **Użycie aplikacji i usług**, a następnie wybierz pozycję **Utwórz archiwum**.

    ![Pobieranie danych](./media/gdpr-dsr-export-msa/create-archive.png)
1. Zostanie utworzone nowe archiwum. Wybierz pozycję **Pobierz**, aby uzyskać wyeksportowane dane działań produktów i usług.

    ![Pobieranie](./media/gdpr-dsr-export-msa/download.png)

## <a name="export-a-flow"></a>Eksportowanie przepływu

Użytkownik końcowy, który ma dostęp do przepływu, może wyeksportować ten przepływ, wykonując następujące czynności:

1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com/).

1. Wybierz pozycję **Moje przepływy**, a następnie wybierz przepływ do wyeksportowania.

1. Wybierz pozycję **... Więcej**, a następnie wybierz pozycję **Eksportuj**.

    ![Eksportowanie przepływu](./media/gdpr-dsr-export/export-flow.png)

1. Wybierz pozycję **Pakiet (plik ZIP)**.

Twój przepływ będzie teraz dostępny jako pakiet skompresowany. Aby uzyskać więcej informacji, zobacz wpis w blogu dotyczący [sposobu eksportowania i importowania przepływu](https://flow.microsoft.com/blog/import-export-bap-packages/).

## <a name="export-run-history"></a>Eksportowanie historii przebiegów

Historia przebiegów zawiera listę wszystkich przebiegów dla przepływu. Te dane obejmują stan przepływu, czas rozpoczęcia, czas trwania oraz dane wejściowe/wyjściowe wyzwalaczy i akcji.

Użytkownik końcowy, który ma dostęp do przepływu, może wykonać następujące czynności, aby wyeksportować te dane:

1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com/).
1. Wybierz link **Moje przepływy**, a następnie wybierz przepływ, dla którego chcesz wyeksportować historię przebiegów.
1. W okienku **HISTORIA PRZEBIEGÓW** wybierz pozycję **Zobacz wszystko**.

    ![Historia uruchamiania](./media/gdpr-dsr-export/run-history.png)

1. Wybierz pozycję **Pobierz plik CSV**.

    ![Pobieranie pliku CSV](./media/gdpr-dsr-export/download-csv.png)

Historia przebiegów jest pobierana jako plik CSV, dzięki czemu można ją otworzyć w programie Microsoft Excel lub edytorze tekstów, aby przeanalizować uzyskane wyniki.

## <a name="export-a-users-activity-feed"></a>Eksportowanie źródła działań użytkownika

W usłudze [Microsoft Flow](https://flow.microsoft.com/) źródło działań pokazuje historię działań, niepowodzeń i powiadomień użytkownika. Użytkownik może przeglądać swoje źródło działań, wykonując następujące kroki:

1. Zaloguj się do usługi [Microsoft Flow](http://flow.microsoft.com/), wybierz ikonę dzwonka w pobliżu prawego górnego rogu, a następnie wybierz pozycję **Pokaż wszystkie działania**.

    ![Pokazywanie źródła działań](./media/gdpr-dsr-export/show-activity-feed.png)

1. Na ekranie **Działania** skopiuj wyniki, a następnie wklej je w edytorze tekstu, takim jak program Microsoft Word.

    ![Pokazywanie źródła działań](./media/gdpr-dsr-export/export-activity-feed.png)

## <a name="export-a-users-connections"></a>Eksportowanie połączeń użytkownika

Połączenia pozwalają na nawiązywanie połączeń z interfejsami API, aplikacjami SaaS oraz systemami innych firm. Wykonaj następujące kroki, aby wyświetlić swoje połączenia:

1. Zaloguj się do usługi [Microsoft Flow](http://flow.microsoft.com/), wybierz ikonę koła zębatego w pobliżu prawego górnego rogu, a następnie wybierz pozycję **Połączenia**.

    ![Pokazywanie połączeń](./media/gdpr-dsr-export/show-connections.png)
1. Skopiuj wyniki, a następnie wklej je w edytorze tekstu, takim jak program Microsoft Word.
