---
title: Uruchamianie przepływów zgodnie z harmonogramem| Microsoft Docs
description: Zautomatyzuj powtarzające się zadania, uruchamiając przepływy zgodnie z harmonogramem, na przykład codziennie lub co godzinę.
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/14/2017
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 809ea2202971df854b2351d57a09da8918d13b8b
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690197"
---
# <a name="run-flows-on-a-schedule"></a>Uruchamianie przepływów zgodnie z harmonogramem
Utwórz przepływ, który wykonuje jedno lub więcej zadań (takich jak wysłanie raportu w wiadomości e-mail):

* raz na dzień, na godzinę lub na minutę
* w wybranym dniu
* po upływie wybranej liczby dni, godzin lub minut

## <a name="create-a-recurring-flow"></a>Tworzenie przepływu cyklicznego
1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com), a następnie wybierz pozycję **Moje przepływy** na górnym pasku nawigacji.
   
    ![Opcja Moje przepływy](./media/run-scheduled-tasks/create-flow.png)
2. Wybierz opcję **Utwórz z pustego**.
   
    ![Tworzenie przepływu od podstaw](./media/run-scheduled-tasks/create-from-blank.png)
3. W polu **Wyszukaj wszystkie łączniki i wyzwalacze** wpisz słowo **Cykl**, a następnie wybierz pozycję **Harmonogram — cyklicznie**.
   
    ![Wyszukiwanie wyzwalacza cyklu](./media/run-scheduled-tasks/select-recurrence.png)
4. W oknie dialogowym **Cykl** określ częstotliwość uruchamiania przepływu.
   
    Na przykład określ wartość **2** w obszarze **Interwał** i wartość **Tydzień** w obszarze **Częstotliwość**, jeśli chcesz uruchamiać przepływ co dwa tygodnie.
   
    ![Określanie cyklu](./media/run-scheduled-tasks/specify-recurrence.png)

## <a name="specify-advanced-options"></a>Określanie opcji zaawansowanych
1. Wykonaj kroki opisane w poprzedniej sekcji, a następnie wybierz pozycję **Pokaż opcje zaawansowane**.
   
    **Uwaga**: te opcje zmieniają się w oparciu o wartości, na które ustawiono pozycje **Interwał** i **Częstotliwość**. Jeśli Twój ekran wygląda inaczej niż na poniższym rysunku, upewnij się, że pozycje **Interwał** i **Częstotliwość** zostały ustawione na wartości, które pokazano na rysunku.
2. Wybierz wartość pozycji **Strefa czasowa**, aby określić, czy wartość **Godzina rozpoczęcia** odzwierciedla lokalną strefę czasową, skoordynowany czas uniwersalny (UTC), itp.
3. Podaj **godzinę rozpoczęcia** w następującym formacie:
   <br>RRRR-MM-DDTGG:MM:SSZ
4. Jeśli wybrano wartość **Dzień** w obszarze **Częstotliwość**, określ porę dnia na potrzeby uruchamiania przepływu.
5. Jeśli wybrano wartość **Tydzień** w obszarze **Częstotliwość**, określ dzień lub dni tygodnia oraz porę lub pory dnia na potrzeby uruchamiania przepływu.
   
    Na przykład skonfiguruj opcje, tak jak pokazano, aby uruchomić przepływ nie wcześniej niż w południe (czasu pacyficznego) w poniedziałek, 1 stycznia 2018 r., i uruchamiać go co dwa tygodnie we wtorki o 17:30 (czasu pacyficznego).
   
    ![Określanie opcji zaawansowanych](./media/run-scheduled-tasks/advanced-options.png)
6. Dodaj akcje, które mają być wykonywane w ramach przepływu zgodnie z opisem w sekcji [Tworzenie przepływu od podstaw](get-started-logic-flow.md).

## <a name="delay-a-flow"></a>Opóźnienie przepływu
1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com), a następnie wybierz pozycję **Moje przepływy** na górnym pasku nawigacji.
   
    ![Tworzenie przepływu od podstaw](./media/run-scheduled-tasks/create-flow.png)
2. Wybierz opcję **Utwórz z pustego**.
   
    ![Tworzenie przepływu od podstaw](./media/run-scheduled-tasks/create-from-blank.png)
3. Określ zdarzenie zgodnie z opisem w sekcji [Tworzenie przepływu od podstaw](get-started-logic-flow.md).
4. Wybierz pozycję **Nowy krok**, a następnie wybierz pozycję **Dodaj akcję**.
   
    ![Opcje umożliwiające dodanie akcji do przepływu](./media/run-scheduled-tasks/add-action.png)
5. Na liście akcji wykonaj dowolną z następujących czynności:
   
   * Wybierz wartość pozycji **Opóźnienie**, określ wartość pozycji **Liczba** i określ wartość pozycji **Jednostka** dla czasu, taką jak sekunda, minuta lub godzina.
   * Wybierz pozycję **Opóźnienie do**, a następnie określ datę w poniższym formacie.<br>RRRR-MM-DDTGG:MM:SSZ
     
     ![Dodawanie opóźnienia](./media/run-scheduled-tasks/add-delay.png)
     ![Określanie opóźnienia w jednostkach czasu](./media/run-scheduled-tasks/delay.png)
     ![Określanie opóźnienia do](./media/run-scheduled-tasks/delay-until.png)

