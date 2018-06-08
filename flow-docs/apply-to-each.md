---
title: Używanie akcji Zastosuj do każdego w celu przetwarzania tablicy elementów w ramach pętli | Microsoft Docs
description: Za pomocą usługi Microsoft Flow możesz przetwarzać tablice elementów w ramach pętli, aby sprawdzać wiele warunków i wykonywać akcje na podstawie tych warunków.
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/16/2017
ms.author: deonhe
ms.openlocfilehash: 37f1ce939db23694bcd92e7f1af75bf6c474be91
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "23440464"
---
# <a name="use-the-apply-to-each-action-in-microsoft-flow-to-process-a-list-of-items-periodically"></a>Używanie akcji Zastosuj do każdego w usłudze Microsoft Flow w celu okresowego przetwarzania listy elementów
Wiele wyzwalaczy może natychmiast uruchomić przepływ na podstawie zdarzenia, takiego jak odebranie nowej wiadomości e-mail w skrzynce odbiorczej. Te wyzwalacze są znakomite, ale czasami trzeba uruchomić przepływ, który wykonuje zapytania względem źródła danych zgodnie ze wstępnie zdefiniowanym harmonogramem i wykonuje określone akcje na podstawie właściwości elementów w źródle danych. W tym celu Twój przepływ może być uruchamiany zgodnie z harmonogramem (na przykład raz dziennie) i używać akcji pętli, takiej jak **Zastosuj do każdego** do przetwarzania listy elementów. Akcji **Zastosuj do każdego** można użyć na przykład w celu zaktualizowania rekordów z bazy danych lub listy elementów z programu Microsoft SharePoint.

W tym przewodniku utworzymy przepływ, który jest uruchamiany co 15 minut i wykonuje następujące działania:

1. Pobiera 10 ostatnich nieprzeczytanych wiadomości ze skrzynki odbiorczej usługi Office 365 Outlook.
2. Sprawdza każdą z 10 wiadomości, aby zweryfikować, czy którakolwiek z nich ma w temacie słowa **spotkajmy się teraz**.
3. Sprawdza, czy wiadomość e-mail jest od Twojego szefa lub została oznaczona jako wiadomość o wysokiej ważności.
4. Wysyła powiadomienie wypychane i oznacza jako przeczytaną każdą wiadomość e-mail, która zawiera w temacie słowa **spotkajmy się teraz** i pochodzi od szefa lub ma wysoką ważność.

Ten diagram przedstawia szczegółowe informacje na temat przepływu, który utworzymy w tym przewodniku:

![przegląd tworzonego przepływu](./media/apply-to-each/foreach-flow-visio.png)

## <a name="prerequisites"></a>Wymagania wstępne
Poniżej podano wymagania, które należy spełnić, aby pomyślnie wykonać czynności w tym przewodniku:

* Konto zarejestrowane do korzystania z usługi [Microsoft Flow](https://flow.microsoft.com).
* Konto usługi Office 365 Outlook.
* Aplikacja mobilna usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows).
* Połączenia z usługą Office 365 Outlook i usługą powiadomień wypychanych.

## <a name="create-a-flow"></a>Utwórz przepływ
1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com):
2. Wybierz kartę **Moje przepływy**, a następnie utwórz przepływ od podstaw:
   
    ![tworzenie od podstaw](./media/apply-to-each/foreach-1.png)
3. W polu wyszukiwania wpisz słowo „harmonogram”, aby wyszukać wszystkie usługi i wyzwalacze związane z tworzeniem harmonogramów.
4. Wybierz wyzwalacz **Harmonogram — Cykl**, aby wskazać, że Twój przepływ będzie uruchamiany zgodnie z harmonogramem, który podasz dalej:
   
    ![akcja cyklu harmonogramu](./media/apply-to-each/foreach-2.png)
5. Ustaw harmonogram w celu uruchamiania co 15 minut:
   
    ![uruchomienia harmonogramu](./media/apply-to-each/foreach-3.png)
6. Wybierz pozycję **+ Nowy krok** i **Dodaj akcję**, a następnie wpisz słowo **outlook** w polu wyszukiwania, aby wyszukać wszystkie akcje związane z programem Microsoft Outlook.
7. Wybierz akcję **Office 365 Outlook — Pobierz wiadomości e-mail**:
   
    ![wybieranie akcji Pobierz wiadomości e-mail](./media/apply-to-each/foreach-4.png)
8. Spowoduje to otwarcie karty **Pobierz wiadomości e-mail**. Skonfiguruj kartę **Pobierz wiadomości e-mail** pod kątem wybierania pierwszych 10 nieprzeczytanych wiadomości e-mail z folderu skrzynki odbiorczej. Nie dołączaj załączników, ponieważ nie będą używane w przepływie:
   
    ![konfigurowanie karty wiadomości e-mail](./media/apply-to-each/foreach-5.png)
   
   > [!NOTE]
   > Do tej pory został utworzony prosty przepływ, który pobiera niektóre wiadomości e-mail z Twojej skrzynki odbiorczej. Te wiadomości e-mail zostaną zwrócone w tablicy. Akcja **Zastosuj do każdego** wymaga tablicy, więc dokładnie takie dane są potrzebne.
   > 
   > 

## <a name="add-actions-and-conditions"></a>Dodawanie akcji i warunków
1. Wybierz pozycję **+ Nowy krok** i **Więcej**, a następnie akcję **Dodaj akcję Zastosuj do każdego**:
   
    ![wybieranie akcji Zastosuj do każdego](./media/apply-to-each/foreach-6.png)
2. Wstaw token **Treść** w polu **Wybierz dane wyjściowe z poprzednich kroków** na karcie **Zastosuj do każdego**. Spowoduje to pobranie treści wiadomości e-mail do użycia w akcji **Zastosuj do każdego**:
   
    ![dodawanie tokenu Treść](./media/apply-to-each/foreach-7.png)
3. Wybierz pozycję **Dodaj warunek**:
   
    ![dodawanie warunku](./media/apply-to-each/foreach-8.png)
4. Skonfiguruj kartę **Warunek** pod kątem wyszukiwania słów „spotkajmy się teraz” w tytule każdej wiadomości e-mail:
   
   * Wstaw token **Temat** w polu **Nazwa obiektu**.
   * Wybierz pozycję **zawiera** z listy **Relacja**.
   * Wpisz słowa **spotkajmy się teraz** w polu **Wartość**.
     
     ![konfigurowanie warunku](./media/apply-to-each/foreach-subject-condition.png)
5. Wybierz opcję **Więcej**, a następnie wybierz pozycję **Dodaj warunek** z gałęzi **Jeśli tak, nic nie rób**. Spowoduje to otwarcie karty **Warunek 2**. Skonfiguruj tę kartę następująco:
   
   * Wstaw token **Ważność** w polu **Nazwa obiektu**.
   * Wybierz pozycję **jest równe** z listy **Relacja**.
   * Wpisz ciąg **Wysoka** w polu **Wartość**.
     
     ![dodawanie warunku](./media/apply-to-each/foreach-importance-condition.png)
6. Wybierz pozycję **Dodaj akcję** w sekcji **Jeśli tak, nic nie rób**. Spowoduje to otwarcie karty **Wybór akcji**, na której zdefiniujesz, co ma się zdarzyć, jeśli warunek wyszukiwania (wiadomość e-mail **spotkajmy się teraz** została wysłana jako wiadomość o wysokiej ważności) zostanie spełniony:
   
    ![dodawanie akcji](./media/apply-to-each/foreach-9.png)
7. Wyszukaj ciąg **powiadomienia**, a następnie wybierz akcję **Powiadomienia — Wyślij mi powiadomienie na urządzenie przenośne**:
   
    ![wyszukiwanie i wybór powiadomienia](./media/apply-to-each/foreach-10.png)
8. Na karcie **Wyślij mi powiadomienie na urządzenie przenośne** podaj szczegóły powiadomienia wypychanego, które będzie wysyłane, jeśli temat wiadomości e-mail zawiera słowa „spotkajmy się teraz”, a następnie wybierz pozycję **Dodaj akcję**:
   
    ![konfigurowanie powiadomienia](./media/apply-to-each/foreach-11.png)
9. Wpisz ciąg **przeczytane** jako wyszukiwany termin, a następnie wybierz akcję **Office 365 Outlook — Oznacz jako przeczytane**. Spowoduje to oznaczenie każdej wiadomości e-mail jako przeczytanej po wysłaniu powiadomienia wypychanego:
   
    ![dodawanie akcji Oznacz jako przeczytane](./media/apply-to-each/foreach-12.png)
10. Dodaj token **Identyfikator wiadomości** w polu **Identyfikator wiadomości** na karcie **Oznacz jako przeczytane**. Może być konieczne wybranie pozycji **Zobacz więcej**, aby znaleźć token **Identyfikator wiadomości**. Wskazuje on identyfikator wiadomości, która zostanie oznaczona jako przeczytana:
    
     ![dodawanie identyfikatora wiadomości](./media/apply-to-each/foreach-13.png)
11. Powróć do karty **Warunek 2** w gałęzi **Jeśli nie, nic nie rób**:
    
    * Wybierz pozycję **Dodaj akcję**, a następnie wpisz ciąg **pobierz menedżera** w polu wyszukiwania.
    * Wybierz akcję **Użytkownicy usługi Office 365 — Pobierz menedżera** z listy wyników wyszukiwania.
    * Wprowadź swój *pełny* adres e-mail w polu **Użytkownik** na karcie **Pobierz menedżera**.
      
      ![dodawanie i konfigurowanie akcji Pobierz menedżera](./media/apply-to-each/foreach-get-manager.png)
12. Wybierz opcję **Więcej**, a następnie wybierz pozycję **Dodaj warunek** z gałęzi **Jeśli nie**. Spowoduje to otwarcie karty **Warunek 3**. Skonfiguruj kartę pod kątem sprawdzania, czy adres e-mail nadawcy (token Od) jest taki sam, jak adres e-mail Twojego szefa (token Adres e-mail):
    
    * Wstaw token **Od** w polu **Nazwa obiektu**.
    * Wybierz pozycję **zawiera** z listy **Relacja**.
    * Wprowadź token **Adres e-mail** w polu **Wartość**.
      
      ![konfigurowanie warunku wyszukiwania](./media/apply-to-each/foreach-condition3-card.png)
13. Wybierz pozycję **Dodaj akcję** w sekcji **Jeśli tak, nic nie rób** na karcie **Warunek 3**. Spowoduje to otwarcie karty **Jeśli tak**, na której zdefiniujesz, co ma się zdarzyć, jeśli warunek wyszukiwania (wiadomość e-mail została wysłana przez szefa) zostanie spełniony:
    
     ![konfigurowanie warunku](./media/apply-to-each/foreah-condition3-add-action.png)
14. Wyszukaj ciąg **powiadomienia**, a następnie wybierz akcję **Powiadomienia — Wyślij mi powiadomienie na urządzenie przenośne**:
    
     ![wyszukiwanie akcji powiadomienia](./media/apply-to-each/foreach-10.png)
15. Na karcie **Wyślij mi powiadomienie na urządzenie przenośne 2** podaj szczegóły powiadomienia wypychanego, które będzie wysyłane, jeśli wiadomość e-mail pochodzi od szefa, a następnie wybierz pozycję **Dodaj akcję**:
    
     ![konfigurowanie karty powiadomienia](./media/apply-to-each/foreach-boss-notification.png)
16. Dodaj akcję **Office 365 Outlook — Oznacz jako przeczytane**. Spowoduje to oznaczenie każdej wiadomości e-mail jako przeczytanej po wysłaniu powiadomienia wypychanego:
    
     ![dodawanie akcji Oznacz jako przeczytane](./media/apply-to-each/foreach-12.png)
17. Dodaj token **Identyfikator wiadomości** do karty **Oznacz jako przeczytane 2**. Może być konieczne wybranie pozycji **Zobacz więcej**, aby znaleźć token **Identyfikator wiadomości**. Wskazuje on identyfikator wiadomości, która zostanie oznaczona jako przeczytana:
    
     ![konfigurowanie akcji Oznacz jako przeczytane](./media/apply-to-each/foreach-mark-as-read2.png)
18. Nadaj nazwę swojemu przepływowi, a następnie utwórz go:
    
     ![nadawanie nazwy przepływowi i zapisywanie go](./media/apply-to-each/foreach-14.png)

Po wykonaniu powyższych kroków Twój przepływ powinien wyglądać podobnie do przedstawionego na poniższym diagramie:

![przegląd utworzonego przepływu](./media/apply-to-each/foreach-flow-finished.png)

## <a name="run-the-flow"></a>Uruchamianie przepływu
1. Wyślij do siebie wiadomość e-mail o wysokiej ważności, która zawiera w tytule słowa **spotkajmy się teraz** (lub niech ktoś z Twojej organizacji wyśle do Ciebie taką wiadomość e-mail).
2. Upewnij się, że wiadomość e-mail znajduje się w Twojej skrzynce odbiorczej i jest nieprzeczytana.
3. Zaloguj się do usługi Microsoft Flow, wybierz opcję **Moje przepływy**, a następnie wybierz pozycję **Uruchom teraz**:
   
    ![uruchamianie teraz](./media/apply-to-each/foreach-run-1.png)
4. Wybierz pozycję **Uruchom przepływ**, aby potwierdzić, że na pewno chcesz uruchomić przepływ:
   
    ![potwierdzanie uruchomienia](./media/apply-to-each/foreach-run-2.png)
5. Po kilku chwilach powinny być widoczne wyniki pomyślnego przebiegu:
   
    ![wyniki przebiegu](./media/apply-to-each/foreach-run-3.png)

## <a name="view-results-of-the-run"></a>Wyświetlanie wyników przebiegu
Po pomyślnym przebiegu przepływu urządzenie przenośne powinno odebrać powiadomienie wypychane.

1. Otwórz aplikację Microsoft Flow na urządzeniu przenośnym, a następnie wybierz kartę **Działanie**. Zobaczysz powiadomienie wypychane o spotkaniu:
   
    ![wybieranie karty Działanie](./media/apply-to-each/foreach-notification-1.png)
2. Aby wyświetlić całą zawartość powiadomienia, może być konieczne jego wybranie. Zobaczysz pełne powiadomienie, podobne do poniższego:
   
    ![szczegóły powiadomienia](./media/apply-to-each/foreach-notification-2.png)
   
   > [!NOTE]
   > Jeśli nie otrzymasz powiadomienia wypychanego, sprawdź, czy urządzenie przenośne ma działające połączenie danych.
   > 
   > 

