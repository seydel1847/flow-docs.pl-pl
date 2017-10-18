---
title: "Tworzenie zaplanowanych przepływów | Microsoft Docs"
description: "Dowiedz się, w jaki sposób tworzyć przepływy uruchamiane zgodnie z harmonogramem."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: hh4nmS_M8Co
courseduration: 9m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: 85c145364d684b5f91bc9f3bc7d1651f061f29d3
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="create-scheduled-flows"></a>Tworzenie zaplanowanych przepływów
W tym temacie dowiesz się, w jaki sposób uruchamiać wcześniej zaplanowane przepływy z użyciem wyzwalacza o nazwie **Cykl**.  Utworzysz przepływ dla zespołu ds. marketingu firmy Contoso, który automatycznie pobiera adresy e-mail klientów z tabeli programu Excel w usłudze OneDrive. Skonfigurujesz przepływ tak, aby raz dziennie nowe adresy e-mail dodane do arkusza kalkulacyjnego zostały dodane do listy klientów w usłudze MailChimp. 

## <a name="create-a-scheduled-flow"></a>Tworzenie zaplanowanego przepływu
1. Otwórz usługę **Microsoft Flow**, wybierz pozycję **Moje przepływy**, a następnie wybierz pozycję **Utwórz z pustego**. 
   
    ![](./media/learning-recurrence/flow-create-blank.png)
2. Wybierz pozycję **Przeszukaj setki łączników i wyzwalaczy**.
3. Wyszukaj usługę **Harmonogram**, wybierz ją, a następnie wybierz wyzwalacz **Harmonogram — Cykl**.
   
    ![](./media/learning-recurrence/flow-recurrence-trigger.png)
4. Ustaw parametr **Częstotliwość** na **Dzień** i **Interwał** na **1**. Wybierz pozycję **Nowy krok**, a następnie pozycję **Dodaj akcję**. 
   
    ![](./media/learning-recurrence/frequency-interval.png)
5. Wyszukaj ciąg **Excel**, wybierz usługę **Excel** i akcję **Excel — Pobierz wiersze**. 
   
    ![](./media/learning-recurrence/excel-get-rows.png)
   
    **Uwaga**: należy wybrać akcję **Pobierz wiersze**, a nie **Pobierz wiersz**. 
6. Wybierz pozycję **Nazwa pliku** i przejdź do lokalizacji pliku. Wybierz pozycję **Nazwa tabeli** i wybierz odpowiednią tabelę w arkuszu kalkulacyjnym. 
   
    ![](./media/learning-recurrence/excel-get-file.png)
7. Dodaj nową akcję. 
   
    ![](./media/learning-recurrence/new-step.png)
8. Wyszukaj ciąg **MailChimp**, a następnie wybierz akcję **MailChimp — Dodaj członka do listy**.
   
    ![](./media/learning-recurrence/select-mailchimp.png)
   
    **Uwaga:** MailChimp jest łącznikiem *Premium*. W zależności od używanej licencji usługi Microsoft Flow może być konieczne zarejestrowanie się w celu skorzystania z wersji próbnej, aby użyć tego łącznika.
9. Dodaj pola **Identyfikator listy** i **Stan** z menu rozwijanych:
   
   * **Identyfikator listy** — wybierz preferowaną listę adresową MailChimp
   * **Stan** — wybierz pozycję **Subskrybowane** 
     
     ![](./media/learning-recurrence/mailchimp-id-status.png)
10. W pozycji **Adres e-mail** użyj funkcji zawartości dynamicznej, aby dodać pole **Adres e-mail kontaktu**. 
    
     ![](./media/learning-recurrence/mailchimp-address.png)
    
     Zwróć uwagę, że przepływ automatycznie tworzy dodatkowy krok. Przepływ wykrywa, że zamierzasz skonfigurować akcję, która wymaga dodatkowej akcji. Za każdym razem, gdy przepływ odczyta nowy adres e-mail, utworzy również nową akcję dla każdego wiersza. 
    
     ![](./media/learning-recurrence/mailchimp-for-each.png)
11. Użyj zawartości dynamicznej, aby wypełnić pola **Imię** i **Nazwisko**:
    
    * **Imię** — Imię
    * **Nazwisko** — Nazwisko
      
      ![](./media/learning-recurrence/mailchimp-names.png)

Teraz ten przepływ będzie uruchamiany raz dziennie i będzie pobierać nowe wiersze z tej tabeli programu Excel, kopiować adres e-mail, imię i nazwisko oraz używać ich do wypełnienia listy pocztowej firmy Contoso w usłudze MailChimp, pozwalając zaoszczędzić czas i pieniądze. 

