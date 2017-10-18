---
title: "Monitorowanie aktywności z telefonu | Microsoft Docs"
description: "Wyświetlanie liczby pomyślnie i niepomyślnie uruchomionych przepływów, czasów uruchomienia i czasów trwania poszczególnych przebiegów"
services: 
suite: flow
documentationcenter: na
author: adiregev
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/11/2016
ms.author: adiregev
ms.openlocfilehash: a9318a1571d46635babbb0b061ff65734ad172fe
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="monitor-activity-in-microsoft-flow-from-your-phone"></a>Monitorowanie aktywności w usłudze Microsoft Flow z telefonu
Wyświetl podsumowanie liczby pomyślnie i niepomyślnie uruchomionych przepływów dzisiaj, wczoraj i w poprzednich dniach. Sprawdź szczegóły każdego przebiegu, np. czas jego uruchomienia, czas trwania każdego etapu, a także sprawdź, czy przebieg zakończył się pomyślnie, czy niepomyślnie.

**Wymagania wstępne**

<iframe width="560" height="315" src="https://www.youtube.com/embed/vZuYZ64K3tI?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

* Zainstaluj aplikację mobilną usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows) na [obsługiwanym urządzeniu](getting-started.md#use-the-mobile-app). Grafiki w tym temacie przedstawiają wersję aplikacji dla telefonu iPhone, ale interfejs na urządzeniach z systemami Android i Windows Phone jest podobny.
* Jeśli nie masz jeszcze przepływu, utwórz go w [witrynie sieci Web usługi Microsoft Flow](https://flow.microsoft.com/). Aby ułatwić sobie testowanie, użyj przepływu, który możesz wyzwolić samodzielnie bez konieczności oczekiwania na zdarzenie zewnętrzne.

Przepływ opisany w niniejszym samouczku jest uruchamiany, gdy otrzymasz wiadomość e-mail z konkretnego adresu:

![Wyzwolenie przepływu w przypadku otrzymania wiadomości e-mail z konkretnego adresu](./media/mobile-monitor-activity/create-trigger.png)

Taki przepływ możesz skonfigurować przy użyciu swojego adresu e-mail na potrzeby testów i używając innego adresu (np. przełożonego), gdy przepływ będzie gotowy do użycia w rzeczywistości.

Po uruchomieniu przepływ wysyła niestandardowe powiadomienie wypychane o następującej składni na Twój telefon:

![Wysyłanie powiadomienia wypychanego](./media/mobile-monitor-activity/create-event.png)

**Uwaga:** możesz również [zarządzać swoimi przepływami](mobile-manage-flows.md) za pomocą aplikacji mobilnej.

## <a name="display-a-summary-of-activity"></a>Wyświetlanie podsumowania działania
<iframe width="560" height="315" src="https://www.youtube.com/embed/nVCGJamOw6s?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

1. Jeśli Twój przepływ nie był wcześniej uruchamiany, wyzwól przebieg w celu wygenerowania danych.
   
    Może upłynąć trochę czasu, zanim dane pojawią się w aplikacji.
2. Otwórz aplikację mobilną, w której karta **Działanie** jest wyświetlana domyślnie.
   
    Dane na tej karcie są uporządkowane według dni, a dane z dnia dzisiejszego są widoczne u góry.
   
    ![Działania uporządkowane według dni](./media/mobile-monitor-activity/activity-day2.png)
   
    Każdy wpis przedstawia nazwę przepływu z ikonami, które odpowiadają zdarzeniom i akcjom jego wyzwalacza.
   
    ![Nazwa i ikony dla każdego przepływu](./media/mobile-monitor-activity/activity-flow-name.png)
   
    Jeśli co najmniej jeden przepływ został uruchomiony pomyślnie, wpis przedstawia liczbę pomyślnych uruchomień i czas ostatniego pomyślnego uruchomienia. Jeśli uruchomienie przepływu nie powiodło się, wówczas podobne informacje przedstawia inny wpis.
   
    ![Podsumowanie sukcesów lub błędów](./media/mobile-monitor-activity/activity-summary.png)
   
    Jeśli przepływ wyśle powiadomienie wypychane, tekst najnowszego powiadomienia pojawi się u dołu wpisu dotyczącego pomyślnych uruchomień.
   
    ![Przykład powiadomienia wypychanego](./media/mobile-monitor-activity/activity-notification.png)
3. Jeśli w ciągu dnia zostało wysłanych wiele powiadomień wypychanych, wykonaj gest szybkiego przesunięcia w lewo na powiadomieniu, aby wyświetlić maksymalnie trzy poprzednie powiadomienia. Jeśli liczba powiadomień wysłanych w ciągu dnia przekracza cztery, przesuń szybko w lewo, aż pojawi się pole **Zobacz więcej**. Następnie naciśnij to pole, aby wyświetlić listę wszystkich powiadomień.
   
    ![Przykład powiadomienia wypychanego](./media/mobile-monitor-activity/activity-notification-list.png)
4. Naciśnij pozycję **Wstecz**, aby wrócić do podsumowania aktywności.
5. Aby odfiltrować zawartość podsumowania aktywności, naciśnij ikonę w prawym górnym rogu.
   
    Możesz wyświetlić wszystkie wpisy, wpisy dotyczące samych niepowodzeń albo tylko obejmujące powiadomienia wypychane.
   
    ![Wyświetlanie wszystkich przebiegów, tylko niepowodzeń lub tylko powiadomień](./media/mobile-monitor-activity/activity-filter.png)

## <a name="show-details-of-a-run"></a>Wyświetlanie szczegółów przebiegu
1. W podsumowaniu aktywności naciśnij wpis, aby wyświetlić szczegóły dotyczące ostatniego przebiegu.
   
     Poszczególne zdarzenia i akcje zostaną wyświetlone z ikonami oznaczającymi, czy zdarzenie lub akcja zakończyła się powodzeniem. Jeśli wynik był pomyślny, wówczas widoczny będzie również czas trwania (w sekundach) określonego zdarzenia lub akcji.
   
    ![Szczegóły przebiegu](./media/mobile-monitor-activity/activity-icons.png)
2. W dolnej części ekranu naciśnij pozycję **Zobacz poprzednie przebiegi**, aby wyświetlić listę wszystkich przebiegów przepływu, a następnie naciśnij przebieg, aby wyświetlić jego szczegóły.
   
    ![Historia sukcesów/niepowodzeń](./media/mobile-monitor-activity/history-mixed.png)

