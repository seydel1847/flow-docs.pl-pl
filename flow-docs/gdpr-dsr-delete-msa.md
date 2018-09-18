---
title: 'Microsoft Flow: RODO — żądania podmiotów danych dotyczące usuwania w przypadku kont Microsoft (MSA) | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych RODO dotyczące usuwania przy użyciu usługi Microsoft Flow w przypadku kont Microsoft.
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: KFile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 5/25/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: e42da775d5c004bfbe0d6bb8923e6d05aaa5e976
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688978"
---
# <a name="respond-to-gdpr-data-subject-delete-requests"></a>Reagowanie na żądania podmiotów danych RODO dotyczące usuwania

**Prawo do bycia zapomnianym** przez usunięcie danych osobowych to kluczowa metoda ochrony stosowana w rozporządzeniu RODO. Usunięcie danych osobowych obejmuje usunięcie wszystkich danych, z wyjątkiem informacji z dzienników inspekcji.

Usługa Microsoft Flow umożliwia użytkownikom tworzenie automatycznych przepływów pracy. Użytkownik, który decyduje się na usunięcie swoich danych osobowych z usługi Microsoft Flow, może przejrzeć te dane osobowe i określić, czy chce usunąć wszystkie, czy tylko niektóre nich.

W poniższej tabeli przedstawiono automatycznie usuwane dane osobowe i dane, które wymagają przejrzenia i usunięcia ich przez użytkownika konta Microsoft (MSA):

|Wymaga przejrzenia i usunięcia przez użytkownika konta MSA|Usuwane automatycznie|
|------|------|
|Działania produktów i usług|Historia uruchamiania|
|Przepływy|Kanał aktywności|
|Połączenia||

Usługa Microsoft Flow oferuje następujące środowiska umożliwiające użytkownikom wyszukiwanie, przeglądanie lub zmienianie danych osobowych i zasobów, które nie są usuwane automatycznie:

## <a name="manage-delete-requests"></a>Zarządzanie żądaniami usunięcia

Poniższe kroki opisują, jak samodzielnie obsłużyć żądania usunięcia dla rozporządzenia RODO.

### <a name="delete-product-and-service-activity"></a>Usuwanie działań produktów i usług

1. Zaloguj się do [pulpitu nawigacyjnego zachowania poufności informacji firmy Microsoft](https://account.microsoft.com/privacy/) za pomocą konta MSA.
1. Wybierz link **Historii działań**.

    ![Historia działań](./media/gdpr-dsr-export-msa/activityhistory.png)

1. Możesz wyszukiwać lub przeglądać historię działań dla różnych aplikacji i usług firmy Microsoft, których używasz, w tym dla usługi Microsoft Flow. Wybierz pozycję **Usuń**, aby usunąć zdarzenia działań określonego produktu lub usługi.

    ![Usuwanie zdarzenia](./media/gdpr-dsr-delete-msa/deleteevent.png)

1. W ciągu kilku chwil element zostanie usunięty z konta i z pulpitu nawigacyjnego zachowania poufności informacji.

### <a name="list-and-delete-flows"></a>Wyświetlanie i usuwanie przepływów

Użytkownik może wyświetlić i usunąć swoje przepływy z usługi [Microsoft Flow](https://flow.microsoft.com), wykonując następujące kroki:

1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com), a następnie wybierz pozycję **Moje przepływy**.

1. Wybierz pozycję **...** obok usuwanego przepływu, a następnie wybierz pozycję **Usuń**.

    ![Usuwanie zdarzenia](./media/gdpr-dsr-delete-msa/deleteflow.png)

### <a name="delete-connections"></a>Usuwanie połączeń

Łączniki komunikują się z interfejsami API i systemami SaaS za pomocą połączeń. Połączenia zawierają odwołania do użytkownika, który je utworzył. Użytkownik może usunąć te odwołania w dowolnym momencie, wykonując następujące kroki:

1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com), wybierz ikonę koła zębatego, a następnie wybierz pozycję **Połączenia**.

    ![Usuwanie zdarzenia](./media/gdpr-dsr-delete-msa/deleteconnections.png)

1. Wybierz połączenie, które chcesz usunąć, wybierz pozycję **...**, a następnie wybierz pozycję **Usuń**.

    ![Usuwanie zdarzenia](./media/gdpr-dsr-delete-msa/delete-connection.png)

1. W monicie o potwierdzenie wybierz ikonę **Usuń**.

    ![Usuwanie zdarzenia](./media/gdpr-dsr-delete-msa/confirmdelete.png)

> [!NOTE]
> Jeśli inne przepływy korzystają z usuwanego połączenia, otrzymasz powiadomienie, że wymagane jest nowe połączenie. W przeciwnym razie wybierz pozycję **Usuń**, aby kontynuować.
>
>

## <a name="learn-more"></a>Dowiedz się więcej

* Wprowadzenie do usługi [Microsoft Flow](getting-started.md)
* Dowiedz się, [co nowego](release-notes.md) w usłudze Microsoft Flow
