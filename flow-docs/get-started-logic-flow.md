---
title: "Automatyzacja zadań przez utworzenie przepływu | Microsoft Docs"
description: "Utwórz przepływ, aby automatycznie wykonać jedną lub więcej akcji, na przykład wysłanie wiadomości e-mail po wystąpieniu zdarzenia, takiego jak dodanie wiersza do listy programu SharePoint."
services: 
suite: flow
documentationcenter: na
author: aftowen
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/28/2017
ms.author: deonhe
ms.openlocfilehash: fd6ed3973ed09442108bf780f76b750deea20eeb
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="create-a-flow-in-microsoft-flow"></a>Tworzenie przepływu w usłudze Microsoft Flow
<iframe width="560" height="315" src="https://www.youtube.com/embed/Gt3CMhLAQqE?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

Utwórz przepływ wykonujący automatycznie co najmniej jedno zadanie po jego wyzwoleniu przez zdarzenie. Na przykład możesz utworzyć przepływ, który powiadomi Cię za pośrednictwem wiadomości e-mail o tym, że ktoś wysłał tweet zawierający określone przez Ciebie słowo kluczowe. W tym przykładzie wysłanie tweetu jest zdarzeniem, a wysłanie wiadomości e-mail jest akcją.

## <a name="prerequisites"></a>Wymagania wstępne
* Konto w witrynie [flow.microsoft.com](https://flow.microsoft.com)
* Konto w usłudze Twitter
* Poświadczenia usługi Office 365

## <a name="specify-an-event-to-start-the-flow"></a>Określ zdarzenie uruchamiające przepływ
Najpierw wybierz, jakie zdarzenie (lub *wyzwalacz*) uruchomi przepływ.

1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) wybierz pozycję **Moje przepływy** znajdującą się na górnym pasku nawigacyjnym, a następnie wybierz pozycję **Utwórz z pustego**.
   
    ![Opcja przepływów na lewym pasku nawigacyjnym](./media/get-started-logic-flow/create-logic-flow.png)
2. W polu **Przeszukaj wszystkie łączniki i wyzwalacze** wpisz lub wklej ciąg **Twitter**, a następnie wybierz pozycję **Twitter — Po wysłaniu nowego tweetu**.
   
    ![Zdarzenie związane z serwisem Twitter](./media/get-started-logic-flow/twitter-search.png)
3. Jeśli Twoje konto w usłudze Twitter nie zostało jeszcze połączone z usługą Microsoft Flow, wybierz polecenie **Zaloguj się do usługi Twitter**, a następnie wprowadź swoje poświadczenia.
   
    ![Logowanie do usługi Twitter](./media/get-started-logic-flow/twitter-signin.png)
4. W polu **Tekst wyszukiwania** wpisz słowo kluczowe, które chcesz znaleźć.
   
    ![Słowo kluczowe w usłudze Twitter](./media/get-started-logic-flow/twitter-keyword.png)

## <a name="specify-an-action"></a>Określanie akcji
1. Wybierz pozycję **Nowy krok**, a następnie wybierz pozycję **Dodaj akcję**.
   
    ![Dodawanie akcji](./media/get-started-logic-flow/add-action-icon.png)
2. W polu **Przeszukaj wszystkie łączniki i akcje** wpisz lub wklej ciąg **wyślij wiadomość e-mail**, a następnie wybierz pozycję **Office 365 Outlook — Wyślij wiadomość e-mail**.
   
    ![Lista akcji](./media/get-started-logic-flow/send-email.png)
3. Jeśli pojawi się monit, wybierz przycisk logowania, a następnie podaj swoje poświadczenia.
4. W wyświetlonym formularzu wpisz lub wklej swój adres e-mail w polu **Do**, a następnie wybierz swoje imię i nazwisko z wyświetlonej listy kontaktów.
   
    ![Pusta wiadomość e-mail](./media/get-started-logic-flow/blank-email.png)
5. W polu **Temat** wpisz lub wklej ciąg **Nowy tweet od:**, a następnie wpisz spację.
   
    ![Wiersz tematu z symbolem zastępczym](./media/get-started-logic-flow/message-token.png)
6. Z listy tokenów wybierz token **Tweet opublikowany przez**, aby dodać jego symbol zastępczy.
   
    ![Dodawanie parametru](./media/get-started-logic-flow/add-parameter.png)
7. Kliknij lub naciśnij pole **Treść**, a następnie kliknij lub naciśnij token **Tekst tweetu**, aby dodać jego symbol zastępczy.
8. (opcjonalnie) Dodaj kolejne tokeny i/lub inną zawartość do treści wiadomości e-mail.
9. W górnej części ekranu nazwij przepływ, a następnie wybierz pozycję **Utwórz przepływ**.
   
    ![Wybieranie przycisku Utwórz przepływ](./media/get-started-logic-flow/create-button.png)
10. Wybierz przycisk **Gotowe**, aby zaktualizować listę przepływów.
    
     ![Wybór przycisku Gotowe](./media/get-started-logic-flow/done-button.png)
11. Wyślij tweet zawierający określone przez Ciebie słowo kluczowe.
    
     W ciągu minuty otrzymasz wiadomość e-mail z powiadomieniem o nowym tweecie.

## <a name="manage-a-flow"></a>Zarządzanie przepływem
1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) wybierz pozycję **Moje przepływy** na górnym pasku nawigacji.
2. Na liście przepływów możesz wykonać następujące czynności:
   
   * Aby wstrzymać przepływ, ustaw odpowiedni przełącznik na wartość **Wyłączone**.
     
       ![Wstrzymywanie przepływu](./media/get-started-logic-flow/pause-flow.png)
   * Aby wznowić przepływ, ustaw odpowiedni przełącznik na wartość **Włączone**.
     
       ![Wznawianie przepływu](./media/get-started-logic-flow/resume-flow.png)
   * Aby edytować przepływ, wybierz ikonę ołówka odpowiadającą przepływowi, który chcesz edytować.
     
       ![Wybieranie przepływu](./media/get-started-logic-flow/select-flow.png)
   * Aby usunąć przepływ, wybierz ikonę **...**, wybierz pozycję **Usuń**, a następnie wybierz pozycję **Usuń** w wyświetlonym oknie komunikatu.
     
       ![Ikona Usuń](./media/get-started-logic-flow/delete-icon.png)
   * Aby wyświetlić historię przebiegów przepływu, wybierz przepływ na stronie **Moje przepływy**, a następnie obejrzyj historię w sekcji **HISTORIA PRZEBIEGÓW** na stronie, która zostanie otwarta.
     
       ![historia przebiegów](./media/get-started-logic-flow/run-history.png)
     
     Wybierz przebieg przepływu z listy przebiegów, aby wyświetlić dane wejściowe i dane wyjściowe każdego kroku.

**Uwaga**: Na swoim koncie możesz mieć maksymalnie 50 przepływów. Jeśli masz już 50 przepływów, przed utworzeniem nowego musisz któryś usunąć.

## <a name="next-steps"></a>Następne kroki
* [Dodaj kroki](multi-step-logic-flow.md) — takie jak różne sposoby powiadomień — do swojego przepływu.
* [Uruchamiaj zadania zgodnie z harmonogramem](run-tasks-on-a-schedule.md), jeśli chcesz, aby dana akcja występowała codziennie, w określonym dniu lub po określonej liczbie minut.
* [Dodaj przepływ do aplikacji](https://powerapps.microsoft.com/tutorials/using-logic-flows/), aby umożliwić aplikacji uruchamianie logiki w chmurze.
* [Zacznij korzystać z przepływów zespołu](create-team-flows.md) i zaproś inne osoby do wspólnego projektowania przepływów.

