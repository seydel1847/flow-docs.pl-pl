---
title: Oczekiwanie na zatwierdzenie w przepływie | Microsoft Docs
description: Przepływy mogą oczekiwać na wystąpienie zewnętrznego zdarzenia, takiego jak zatwierdzenie lub odrzucenie zmiany przez użytkownika, przed wykonaniem akcji, np. wysłania powiadomienia o decyzji.
services: ''
suite: flow
documentationcenter: na
author: merwanhade
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/15/2018
ms.author: merwanhade
ms.openlocfilehash: b75cacf14da7d1b339e8a2f9e35eece389c2a6f7
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "29563162"
---
# <a name="wait-for-approval-in-microsoft-flow"></a>Oczekiwanie na zatwierdzenie w usłudze Microsoft Flow

> [!VIDEO https://www.youtube.com/embed/W6oxcYRtW-8?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF]
>


Utwórz przepływ, który, po utworzeniu elementu w programie SharePoint, wysyła wiadomość e-mail dotyczącą zatwierdzenia, a następnie powiadamia użytkownika, czy element został zatwierdzony, czy odrzucony. Aby postępować dokładnie według tego samouczka, utwórz prostą listę programu SharePoint jako akcję wyzwalacza, ale możesz użyć innego źródła danych, np. usługi Dropbox lub OneDrive.

**Wymagania wstępne**

* Utwórz prostą listę programu SharePoint o nazwie **Monitor projektów**, dodaj kolumnę o nazwie **Tytuł**, a następnie dodaj kolumnę Osoba lub Grupa o nazwie **Przypisano do**.

   ![Obraz listy Monitor projektów w usłudze SPO](./media/wait-for-approvals/project-tracker.png)

## <a name="add-an-event-to-trigger-the-flow"></a>Dodawanie zdarzenia w celu wyzwolenia przepływu

1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com), wybierz pozycję **Moje przepływy** znajdującą się na górnym pasku nawigacyjnym, a następnie wybierz pozycję **Utwórz z pustego**.

1. Wybierz pole **Przeszukaj setki łączników i wyzwalaczy**, wpisz **nowy element**, a następnie przejdź do pozycji **SharePoint — po utworzeniu elementu**.

1. Jeśli zostanie wyświetlony monit, zaloguj się do programu SharePoint.
1. W obszarze **Adres witryny** podaj adres URL witryny programu SharePoint, która zawiera listę.

1. W obszarze **Nazwa listy** wybierz utworzoną wcześniej listę. Jeśli postępujesz zgodnie ze wskazówkami, jej nazwa to **Monitor projektów**.

    ![Obraz nazwy listy usługi SPO](./media/wait-for-approvals/SPO-list-name.png)

## <a name="add-the-resulting-action"></a>Dodawanie wynikowej akcji

1. Wybierz przycisk **Nowy krok**, a następnie pozycję **Dodaj akcję**.

1. W polu **Przeszukaj wszystkie łączniki i akcje** wpisz lub wklej ciąg **wyślij wiadomość e-mail**, a następnie wybierz pozycję **Office 365 Outlook — Wyślij wiadomość e-mail z opcjami**.

1. Jeśli zostanie wyświetlony monit, zaloguj się do usługi Office 365 Outlook.

1. Wybierz pole **Do**, a następnie wybierz token **Przypisano do wiadomości e-mail**.

    Użytkownik podany w kolumnie **Przypisano do** otrzyma wiadomość e-mail umożliwiającą zatwierdzenie lub odrzucenie elementów. Podczas tworzenia elementu w celu przetestowania przepływu w tym polu podaj swoją nazwę użytkownika. Dzięki temu nie tylko zatwierdzisz lub odrzucisz element, ale również otrzymasz wiadomość e-mail z powiadomieniem.

    > [!NOTE]
    > Pola **Temat** i **Opcje użytkownika** możesz dostosować do własnych potrzeb.

    ![Obraz pola Wyślij wiadomość e-mail dotyczącą zatwierdzenia do](./media/wait-for-approvals/send-approval-email-to.png)

## <a name="add-a-condition"></a>Dodawanie warunku

1. Wybierz przycisk **Nowy krok**, a następnie pozycję **Dodaj warunek**.

    ![Obraz dodawania warunku](./media/wait-for-approvals/add-a-condition.png)
1. Wybierz pierwsze pole, a następnie wybierz token **SelectedOption**.
1. Wybierz ostatnie pole, a następnie wpisz ciąg **Zatwierdź**.

    ![Obraz karty warunku](./media/wait-for-approvals/condition-card-2.png)

1. W obszarze **Jeśli tak** wybierz pozycję **Dodaj akcję**.

1. W polu **Przeszukaj wszystkie łączniki i akcje** wpisz lub wklej ciąg **wyślij wiadomość e-mail**, a następnie wybierz pozycję **Office 365 Outlook — Wyślij wiadomość e-mail**.

1. W polu **Do** podaj adresata, np. **Utworzono za pomocą poczty e-mail**.

1. W polu **Temat** określ temat.

    Na przykład wybierz pozycję **Przypisano do — DisplayName**, wpisz ciąg **— zatwierdzono element** ze spacją z każdej strony, a następnie wybierz pozycję **Tytuł**.

1. W polu **Treść** określ treść wiadomości e-mail, np. **Można przejść do następnej fazy projektu**.

    > [!NOTE]
    > Osoba, która utworzyła element na liście programu SharePoint, zostanie powiadomiona, czy projekt został zatwierdzony, czy odrzucony.

    ![Obraz opcji Jeśli tak — wyślij wiadomość e-mail](./media/wait-for-approvals/if-yes-send-email-card-3.png)

1. W obszarze **Jeśli nie** powtórz pięć ostatnich czynności, ale zmień pola **Temat** i **Treść**, aby poinformować o odrzuceniu projektu.

     ![Obraz opcji Jeśli nie — wyślij wiadomość e-mail](./media/wait-for-approvals/no-send-email-2.png)

## <a name="finish-and-test-your-flow"></a>Zakończenie i przetestowanie przepływu

1. Nadaj nazwę przepływowi, a następnie wybierz pozycję **Utwórz przepływ**.

     ![Obraz tworzenia przepływu](./media/wait-for-approvals/create-flow.png)
1. Utwórz element na liście programu SharePoint.

    Wiadomość e-mail dotycząca zatwierdzenia zostanie wysłana do określonego adresata. Gdy adresat wybierze pozycję **Zatwierdź** lub **Odrzuć** w tej wiadomości e-mail, otrzymasz wiadomość e-mail wskazującą odpowiedź.

## <a name="learn-more"></a>Dowiedz się więcej

* [Przewodnik dotyczący nowoczesnych zatwierdzeń z jedną osobą zatwierdzającą](modern-approvals.md)
* Tworzenie [zatwierdzeń sekwencyjnych](sequential-modern-approvals.md)
* Tworzenie [zatwierdzeń równoległych](parallel-modern-approvals.md)
* [Mobilne zatwierdzanie żądań](mobile-approvals.md)
