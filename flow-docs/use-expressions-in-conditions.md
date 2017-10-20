---
title: "Używanie wyrażeń z warunkami | Microsoft Docs"
description: "Używanie wyrażeń zaawansowanych, takich jak "
"\"and\"\",": 
"\"\"or\"\",": 
"\"\"empty\"\",": 
"\"\"less\"\"": 
and: 
"\"\"greater\"\"": 
with: 
microsoft: 
flow: 
conditions.": 
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/01/2017
ms.author: deonhe
ms.openlocfilehash: a833abf7cb43e6d8a1c67b0f4160c90a4b24545a
ms.sourcegitcommit: 122870842a07183ab3b90e07d99b60d822d6c5ae
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="use-expressions-in-conditions-to-check-multiple-values"></a>Sprawdzanie wielu wartości przy użyciu wyrażeń w warunkach
W tym przewodniku dowiesz się, jak porównywać wiele wartości w **trybie zaawansowanym** przy użyciu wyrażeń i **warunków**.

Po utworzeniu przepływu możesz przy użyciu karty [**Warunek**](add-condition.md#add-a-condition) w trybie podstawowym szybko porównać jedną wartość z inną wartością. Jednak niektóre sytuacje wymagają porównania wielu wartości. Może być na przykład konieczne sprawdzenie wartości kilku kolumn w arkuszu kalkulacyjnym lub bazie danych.

W warunkach możesz użyć dowolnej kombinacji następujących wyrażeń logicznych.

Wyrażenie|Opis|Przykład
--------|-----------|-------
|[and](#use-the-and-expression)|Przyjmuje dwa argumenty i zwraca wartość true, jeśli obie wartości mają wartość true.<br><b>Uwaga</b>: oba argumenty muszą być wartościami logicznymi.|To wyrażenie zwraca wartość false: <br>and(greater(1,10),equals(0,0))
|[or](#use-the-or-expression)|Przyjmuje dwa argumenty i zwraca wartość true, jeśli jeden z argumentów ma wartość true. <br><b>Uwaga</b>: oba argumenty muszą być wartościami logicznymi.|To wyrażenie zwraca wartość true:<br>or(greater(1,10),equals(0,0))
|equals|Zwraca wartość true, jeśli dwie wartości są równe.|Jeśli na przykład parametr parameter1 ma wartość someValue, to wyrażenie zwróci wartość true:<br>equals(parameters('parameter1'), 'someValue')
|[less](#use-the-less-expression)|Przyjmuje dwa argumenty i zwraca wartość true, jeśli wartość pierwszego argumentu jest mniejsza niż wartość drugiego argumentu. <br><b>Uwaga</b>: obsługiwane typy to liczba całkowita, liczba zmiennoprzecinkowa i ciąg.|To wyrażenie zwraca wartość true:<br>less(10,100)
|lessOrEquals|Przyjmuje dwa argumenty i zwraca wartość true, jeśli pierwszy argument ma wartość równą wartości drugiego argumentu lub mniejszą. <br><b>Uwaga</b>: obsługiwane typy to liczba całkowita, liczba zmiennoprzecinkowa i ciąg.|To wyrażenie zwraca wartość true:<br>lessOrEquals(10,10)
|[greater](#use-the-greater-expression)|Przyjmuje dwa argumenty i zwraca wartość true, jeśli wartość pierwszego argumentu jest większa niż wartość drugiego argumentu. <br><b>Uwaga</b>: obsługiwane typy to liczba całkowita, liczba zmiennoprzecinkowa i ciąg.|To wyrażenie zwraca wartość false:<br>greater(10,10)
|greaterOrEquals|Przyjmuje dwa argumenty i zwraca wartość true, jeśli pierwszy argument ma wartość równą wartości drugiego argumentu lub większą. <br><b>Uwaga</b>: obsługiwane typy to liczba całkowita, liczba zmiennoprzecinkowa i ciąg.|To wyrażenie zwraca wartość false:<br>greaterOrEquals(10,100)
|[empty](#use-the-empty-expression)|Zwraca wartość true, jeśli obiekt, tablica lub ciąg są puste.|To wyrażenie zwraca wartość true:<br>empty('')
|not|Przyjmuje dwa argumenty i zwraca wartość true, jeśli argumenty mają wartość false. <br><b>Uwaga</b>: oba argumenty muszą być wartościami logicznymi.|To wyrażenie zwraca wartość true:<br>not(contains('200 Success','Fail'))
|if|Zwraca określoną wartość, jeśli wynikiem wyrażenia jest wartość true lub false.|To wyrażenie zwraca wartość „yes”:<br>if(equals(1, 1), 'yes', 'no')

## <a name="prerequisites"></a>Wymagania wstępne
* Dostęp do usługi Microsoft Flow.
* Arkusz kalkulacyjny z tabelami opisanymi w dalszej części tego przewodnika. Pamiętaj, aby zapisać swój arkusz kalkulacyjny w lokalizacji takiej jak usługa Dropbox lub Microsoft OneDrive, aby usługa Microsoft Flow mogła uzyskać do niego dostęp.
* Usługa Microsoft Office 365 Outlook (w swoich przepływach możesz też używać dowolnej innej obsługiwanej usługi poczty e-mail).

## <a name="use-the-or-expression"></a>Używanie wyrażenia or
Czasami w przepływie pracy wymagane jest podjęcie akcji, jeśli wartością elementu jest wartośćA **lub** wartośćB. Możesz na przykład śledzić stan zadań w tabeli arkusza kalkulacyjnego. Załóżmy, że tabela ma kolumnę o nazwie *Status*, a wartości możliwe do wpisania w kolumnie *Status* to:

* **completed**
* **blocked**
* **unnecessary**
* **not started**

Oto przykład, jak może wyglądać taki arkusz kalkulacyjny:

![przykładowy arkusz kalkulacyjny](./media/use-expressions-in-conditions/spreadsheet-table.png)

Przy użyciu usługi Microsoft Flow chcesz w powyższym arkuszu kalkulacyjnym usunąć wszystkie wiersze, w których w kolumnie *Status* występuje wartość *completed* lub *unnecessary*.

Utwórzmy przepływ.

### <a name="start-with-a-blank-flow"></a>Zaczynanie od pustego przepływu
1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com).
   
    ![logowanie](includes/media/modern-approvals/sign-in.png)
2. Wybierz kartę **Moje przepływy**.
   
    ![wybieranie karty moje przepływy](includes/media/modern-approvals/select-my-flows.png)
3. Wybierz opcję **Utwórz z pustego**.
   
    ![tworzenie od podstaw](includes/media/modern-approvals/blank-template.png)

### <a name="add-a-trigger-to-your-flow"></a>Dodawanie wyzwalacza do przepływu
1. Wyszukaj pozycję **Harmonogram**, a następnie wybierz wyzwalacz **Harmonogram — Cykl**.
   
    ![wyzwalacz harmonogramu](includes/media/schedule-trigger/schedule-trigger.png)
2. Ustaw harmonogram tak, aby był uruchamiany raz dziennie.
   
    ![ustawianie harmonogramu](includes/media/schedule-trigger/set-schedule.png)

### <a name="select-the-spreadsheet-and-get-all-rows"></a>Wybieranie arkusza kalkulacyjnego i pobieranie wszystkich wierszy
1. Wybierz kolejno pozycje **Nowy krok** > **Dodaj akcję**.
   
    ![nowy krok](includes/media/new-step/action.png)
2. Wyszukaj pozycję **wiersze**, a następnie wybierz pozycję **Excel — Pobierz wiersze**.
   
    Uwaga: wybierz akcję „pobierz wiersze” odpowiadającą używanemu arkuszowi kalkulacyjnemu. Jeśli na przykład korzystasz z usługi Arkusze Google, wybierz pozycję **Arkusze Google — Pobierz wiersze**.
   
    ![pobieranie wierszy](includes/media/new-step/get-excel-rows.png)
3. Wybierz ikonę folderu w polu **Nazwa pliku**, przejdź do arkusza kalkulacyjnego zawierającego dane i wybierz go.
   
    ![wybieranie arkusza kalkulacyjnego](includes/media/new-step/select-spreadsheet.png)
4. Wybierz z listy **Nazwa tabeli** tabelę zawierającą dane.
   
    ![wybieranie tabeli](includes/media/new-step/select-table.png)

### <a name="check-the-status-column-of-each-row"></a>Sprawdź kolumnę stanu każdego wiersza.
1. Wybierz kolejno pozycje **Nowy krok** > **Więcej** > **Dodaj instrukcję Zastosuj do każdego**.
   
    ![wybieranie tabeli](includes/media/new-step/apply-to-each.png)
2. Dodaj token **Wartość** do pola **Wybierz dane wyjściowe z poprzednich kroków**.
   
    ![wybieranie tabeli](includes/media/apply-to-each/add-value-token.png)
3. Wybierz kolejno pozycje **Dodaj warunek** > **Edytowanie w trybie zaawansowanym**.
4. Dodaj następujące wyrażenie **or**. To wyrażenie **or** sprawdza wartość każdego wiersza w tabeli (wiersz nazywany jest elementem, gdy jest używany w wyrażeniu). Jeśli wartość kolumny **status** to *completed* **lub** *unnecessary*, wynikiem wyrażenia **or** jest wartość „true”.
   
    Wyrażenie **or** wygląda następująco:
   
    ````@or(equals(item()?['status'], 'unnecessary'), equals(item()?['status'], 'completed'))````
   
    Karta **Warunek** wygląda następująco:
   
    ![obraz wyrażenia or](./media/use-expressions-in-conditions/or-expression.png)

### <a name="delete-matching-rows-from-the-spreadsheet"></a>Usuwanie pasujących wierszy z arkusza kalkulacyjnego
1. Wybierz pozycję **Dodaj akcję** w gałęzi **JEŚLI TAK, NIC NIE RÓB** warunku.
2. Wyszukaj pozycję **Usuń wiersz**, a następnie pozycję **Excel — Usuń wiersz**.
   
    ![obraz przedstawiający usuwanie wiersza](includes/media/new-step/select-delete-excel-row.png)
3. W polu **Nazwa pliku** wyszukaj i wybierz plik arkusza kalkulacyjnego zawierający dane, które chcesz usunąć.
4. Z listy **Nazwa tabeli** wybierz tabelę zawierającą dane.
5. Umieść token **Identyfikator wiersza** w polu **Identyfikator wiersza**.
   
    ![plik arkusza kalkulacyjnego](includes/media/new-step/delete-excel-row.png)

### <a name="name-the-flow-and-save-it"></a>Nadawanie nazwy przepływowi i zapisywanie go
1. Określ nazwę przepływu, a następnie wybierz przycisk **Utwórz przepływ**.
   
    ![zapisywanie przepływu](./media/use-expressions-in-conditions/name-and-save.png)

### <a name="run-the-flow-with-the-or-expression"></a>Uruchamianie przepływu z wyrażeniem or
Przepływ zostanie uruchomiony po jego zapisaniu. Jeśli utworzono arkusz kalkulacyjny przedstawiony we wcześniejszej części tego przewodnika, oto jak wygląda ten arkusz po zakończeniu przebiegu:

![zakończenie wyrażenia or](./media/use-expressions-in-conditions/spreadsheet-table-after-or-expression-runs.png)

Zauważ, że wszystkie dane z wierszy zawierających wartości „completed” lub „unnecessary” w kolumnie Status zostały usunięte.

## <a name="use-the-and-expression"></a>Używanie wyrażenia and
Załóżmy, że masz tabelę zawierającą dwie kolumny. Nazwy kolumn to Status i Assigned. Załóżmy także, że chcesz usunąć wszystkie wiersze, w których w kolumnie Status znajduje się wartość „blocked”, a w kolumnie Przypisano znajduje się wartość „John Wonder”.  Aby wykonać to zadanie, wykonaj wszystkie kroki opisane we wcześniejszej części tego przewodnika, ale podczas edytowania karty **Warunek** w trybie zaawansowanym użyj wyrażenia **and** w następujący sposób:

````@and(equals(item()?['Status'], 'blocked'), equals(item()?['Assigned'], 'John Wonder'))````

Karta **Warunek** wygląda następująco:

![obraz wyrażenia and](./media/use-expressions-in-conditions/and-expression.png)

### <a name="run-the-flow-with-the-and-expression"></a>Uruchamianie przepływu z wyrażeniem and
Jeśli wykonano wszystkie opisane do tego miejsca czynności, arkusz kalkulacyjny powinien wyglądać następująco:

![przed uruchomieniem funkcji and](./media/use-expressions-in-conditions/spreadsheet-table-before-and-expression-runs.png)

Po uruchomieniu przepływu arkusz kalkulacyjny powinien wyglądać następująco:

![po uruchomieniu funkcji and](./media/use-expressions-in-conditions/spreadsheet-table-after-and-expression-runs.png)

## <a name="use-the-empty-expression"></a>Używanie wyrażenia empty
Zauważ, że w arkuszu kalkulacyjnym znajduje się teraz kilka pustych wierszy. Aby je usunąć, przy użyciu wyrażenia **empty** zidentyfikuj wszystkie wiersze, które w kolumnach Assigned i Status nie zawierają żadnego tekstu.

Aby wykonać to zadanie, wykonaj wszystkie kroki opisane w sekcji **Używanie wyrażenia and** we wcześniejszej części tego przewodnika, ale podczas edytowania karty **Warunek** w trybie zaawansowanym użyj wyrażenia empty w następujący sposób:

````@and(empty(item()?['Status']), empty(item()?['Assigned']))````

Karta **Warunek** wygląda następująco:

![obraz wyrażenia empty](./media/use-expressions-in-conditions/empty-expression.png)

Po uruchomieniu przepływu arkusz kalkulacyjny powinien wyglądać następująco:

![po uruchomieniu funkcji empty](./media/use-expressions-in-conditions/spreadsheet-table-after-empty-expression-runs.png)

Zauważ, że z tabeli usunięto dodatkowe wiersze.

## <a name="use-the-greater-expression"></a>Używanie wyrażenia greater
Wyobraź sobie, że masz bilety na mecz siatkówki dla swoich współpracowników i używasz arkusza kalkulacyjnego, aby mieć pewność, że każdy z nich zwróci Ci pieniądze. Możesz szybko utworzyć przepływ wysyłający codzienną wiadomość e-mail do każdej osoby, która nie zapłaciła całej kwoty.

Przy użyciu wyrażenia **greater** zidentyfikuj pracowników, którzy nie zapłacili całej kwoty. Następnie możesz automatycznie wysłać wiadomość e-mail z przypomnieniem do osób z zaległościami w zapłacie.

Oto jak wygląda arkusz kalkulacyjny:

![widok arkusza kalkulacyjnego](./media/use-expressions-in-conditions/tickets-spreadsheet-table.png)

Oto implementacja wyrażenia **greater** identyfikująca wszystkie osoby, które zapłaciły mniej niż wynosi należna kwota:

````@greater(item()?['Due'], item()?['Paid'])````

## <a name="use-the-less-expression"></a>Używanie wyrażenia less
Wyobraź sobie, że masz bilety na mecz siatkówki dla swoich współpracowników i używasz arkusza kalkulacyjnego, aby mieć pewność, że każdy z nich zwróci Ci pieniądze w ustalonym terminie. Możesz utworzyć przepływ wysyłający wiadomość e-mail z przypomnieniem do każdej osoby, która nie zapłaciła całej kwoty, jeśli bieżąca data jest późniejsza niż jeden dzień przed terminem.

Użyj wyrażenia **and** wraz z wyrażeniem **less**, ponieważ walidowane są dwa warunki:

| Warunek do sprawdzenia | wyrażenie do użycia | Przykład |
| --- | --- | --- |
| Czy została zapłacona cała kwota? |greater |@greater(item()?['Due'], item()?['Paid']) |
| Czy termin przypada na mniej niż jeden dzień od bieżącej daty? |less |@less(item()?['DueDate'], addDays(utcNow(),1)) |

## <a name="combine-the-greater-and-less-expressions-in-an-and-expression"></a>Połączenie wyrażeń greater i less w wyrażeniu and
Przy użyciu wyrażenia **greater** zidentyfikuj pracowników, którzy zapłacili mniej niż wynosi należna kwota, a przy użyciu wyrażenia **less** określ, czy termin zapłaty przypada na mniej niż jeden dzień od bieżącej daty. Następnie przy użyciu akcji **Wyślij wiadomość e-mail** możesz wysłać przypomnienie do osób, które nie zapłaciły całej kwoty, gdy termin zapłaty przypada na mniej niż jeden dzień od bieżącej daty.

Oto jak wygląda tabela arkusza kalkulacyjnego:

![widok arkusza kalkulacyjnego](./media/use-expressions-in-conditions/spreadsheet-table-due-date.png)

Oto implementacja wyrażenia **and** identyfikująca wszystkie osoby, które zapłaciły mniej niż wynosi należna kwota, gdy termin zapłaty przypada na mniej niż jeden dzień od bieżącej daty.

````@and(greater(item()?['Due'], item()?['Paid']), less(item()?['dueDate'], addDays(utcNow(),1)))````

## <a name="learn-more"></a>Dowiedz się więcej
Dowiedz się więcej na temat innych [wyrażeń](https://docs.microsoft.com/azure/logic-apps/logic-apps-workflow-definition-language#functions)

