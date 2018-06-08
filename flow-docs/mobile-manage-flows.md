---
title: Zarządzanie przepływami z telefonu | Microsoft Docs
description: Wyświetlaj listę przepływów, włączaj je lub wyłączaj oraz wyświetlaj zdarzenia, akcje i historię uruchomień każdego przepływu
services: ''
suite: flow
documentationcenter: na
author: adiregev
manager: erikre
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/11/2016
ms.author: adiregev
ms.openlocfilehash: 4a04fec70ae70ff17ddf6e1f93e6461ec432e8d2
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "23440104"
---
# <a name="manage-flows-in-microsoft-flow-from-your-phone"></a>Zarządzanie przepływami w usłudze Microsoft Flow z telefonu
Wyświetlaj listę wszystkich utworzonych przepływów oraz wyświetlaj powiązane z każdym przepływem zdarzenia i akcje, włączaj je lub wyłączaj, a także poznawaj ich historię uruchomień.

**Wymagania wstępne**

* Zainstaluj aplikację mobilną usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows) na [obsługiwanym urządzeniu](getting-started.md#use-the-mobile-app). Grafiki w tym temacie przedstawiają wersję aplikacji dla telefonu iPhone, ale interfejs na urządzeniach z systemami Android i Windows Phone wygląda podobnie.
* Jeśli nie masz jeszcze przepływu, utwórz go w [witrynie sieci Web usługi Microsoft Flow](https://flow.microsoft.com/). Aby ułatwić sobie testowanie, użyj przepływu, który możesz wyzwolić samodzielnie bez konieczności oczekiwania na zdarzenie zewnętrzne.

Przepływ opisany w niniejszym samouczku jest uruchamiany, gdy otrzymasz wiadomość e-mail z konkretnego adresu:

![Wyzwolenie przepływu w przypadku otrzymania wiadomości e-mail z konkretnego adresu](./media/mobile-manage-flows/create-trigger.png)

Taki przepływ możesz skonfigurować przy użyciu swojego adresu e-mail na potrzeby testów i używając innego adresu (np. przełożonego), gdy przepływ będzie gotowy do użycia w rzeczywistości.

Po uruchomieniu przepływ wysyła niestandardowe powiadomienie wypychane o następującej składni na Twój telefon:

![Wysyłanie wiadomości w usłudze Slack](./media/mobile-manage-flows/create-event.png)

**Uwaga**: za pomocą aplikacji mobilnej możesz także [monitorować aktywność przepływu](mobile-monitor-activity.md).

## <a name="manage-a-flow"></a>Zarządzanie przepływem
1. Otwórz aplikację mobilną, a następnie naciśnij pozycję **Moje przepływy** znajdującą się u dołu ekranu, aby wyświetlić listę wszystkich swoich przepływów.
   
    Każdy wpis zawiera nazwę przepływu, ikony związane ze zdarzeniami i akcjami, czas ostatniego uruchomienia oraz ikonę informującą o tym, czy ostatnie uruchomienie zakończyło się powodzeniem.
   
    ![Lista przepływów](./media/mobile-manage-flows/flow-list.png)
2. Naciśnij przepływ, aby wyświetlić dostępne opcje zarządzania.
   
    ![Opcje zarządzania przepływem](./media/mobile-manage-flows/flow-details.png)
3. Naciśnij przełącznik **Włącz przepływ**, aby włączyć lub wyłączyć przepływ.
4. Naciśnij pozycję **Zobacz przepływ**, aby zobaczyć zdarzenia i akcje związane z tym przepływem. Naciśnij każde zdarzenie lub akcję, aby je rozwinąć, a następnie naciśnij pozycję **Wstecz**.
   
    ![Zdarzenia i akcje związane z przepływem](./media/mobile-manage-flows/flow-event-action.png)
5. Naciśnij pozycję **Historia uruchomień**, aby zobaczyć uruchomienia zakończone powodzeniem i/lub niepowodzeniem.
   
    ![Lista uruchomień](./media/mobile-manage-flows/history-mixed.png)
6. Naciśnij uruchomienie, aby zobaczyć, czy wszystkie zdarzenia i akcje zakończyły się powodzeniem, a jeśli tak — ile czasu (w sekundach) to zabrało.
   
    ![Szczegóły uruchomienia](./media/mobile-manage-flows/flow-run.png)

