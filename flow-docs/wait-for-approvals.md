---
title: "Oczekiwanie na zatwierdzenie w przepływie | Microsoft Docs"
description: "Przepływy mogą oczekiwać na wystąpienie zewnętrznego zdarzenia, takiego jak zatwierdzenie lub odrzucenie zmiany przez użytkownika, przed wykonaniem akcji, np. wysłania powiadomienia o decyzji."
services: 
suite: flow
documentationcenter: na
author: merwanhade
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/24/2016
ms.author: merwanhade
ms.openlocfilehash: a26566486cf6310dc1c33ef226bfc37b30a5ad16
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="wait-for-approval-in-microsoft-flow"></a>Oczekiwanie na zatwierdzenie w usłudze Microsoft Flow
<iframe width="560" height="315" src="https://www.youtube.com/embed/W6oxcYRtW-8?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

Utwórz przepływ, który, po utworzeniu elementu w programie SharePoint, wysyła wiadomość e-mail dotyczącą zatwierdzenia, a następnie powiadamia użytkownika, czy element został zatwierdzony, czy odrzucony. Aby postępować dokładnie według tego samouczka, utwórz prostą listę programu SharePoint jako akcję wyzwalacza, ale możesz użyć innego źródła danych, np. usługi Dropbox lub OneDrive.

**Wymagania wstępne**

* Utwórz prostą listę usługi SharePoint Online o nazwie **Monitor projektów** z kolumną o nazwie **Tytuł**, a następnie dodaj kolumnę Osoba lub Grupa o nazwie **Przypisano do**.
  
   ![Obraz listy Monitor projektów w usłudze SPO](./media/wait-for-approvals/project-tracker.png)

## <a name="add-an-event-to-trigger-the-flow"></a>Dodawanie zdarzenia w celu wyzwolenia przepływu
1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) wybierz pozycję **Moje przepływy** w górnym pasku nawigacyjnym, a następnie wybierz pozycję **Utwórz nowy przepływ**.
   
    ![Obraz tworzenia nowego przepływu](./media/wait-for-approvals/create-a-new-flow.png)
2. W polu **Jak chcesz rozpocząć?** wpisz lub wklej ciąg **nowego elementu**, a następnie wybierz pozycję **SharePoint Online — po utworzeniu nowego elementu**.
   
    ![Obraz wyzwalacza usługi SPO](./media/wait-for-approvals/send-approval-email-select-2.png)
3. Jeśli zostanie wyświetlony monit, zaloguj się do usługi SharePoint Online.
4. W obszarze **Adres URL witryny** wpisz lub wklej adres URL witryny zawierającej listę.
   
    ![Obraz adresu URL witryny usługi SPO](./media/wait-for-approvals/SPO-site-url.png)
5. W obszarze **Nazwa listy** wybierz listę, np. **Monitor projektów**.
   
    ![Obraz nazwy listy usługi SPO](./media/wait-for-approvals/SPO-list-name.png)

## <a name="add-the-resulting-action"></a>Dodawanie wynikowej akcji
1. Wybierz przycisk **+**, a następnie wybierz pozycję **Dodaj akcję**.
   
    ![Obraz dodawania akcji](./media/wait-for-approvals/add-an-action.png)
2. W polu **Co chcesz zrobić dalej?** wpisz lub wklej ciąg **wyślij wiadomość e-mail**, a następnie wybierz pozycję **Office 365 Outlook — Wyślij wiadomość e-mail dotyczącą zatwierdzenia**.
   
    ![Obraz wysyłania wiadomości e-mail dotyczącej zatwierdzenia](./media/wait-for-approvals/send-approval-mail.png)
3. Jeśli zostanie wyświetlony monit, zaloguj się do usługi Office 365 Outlook.
4. Wybierz pole **Do**, a następnie wybierz pozycję **Przypisano do wiadomości e-mail**.
   
    Użytkownik podany w kolumnie **Przypisano do** otrzyma wiadomość e-mail w celu zatwierdzenia lub odrzucenia elementu. Podczas tworzenia elementu w celu przetestowania przepływu, w tym polu należy podać swoją nazwę użytkownika. Dzięki temu nie tylko zatwierdzisz lub odrzucisz element, ale również otrzymasz wiadomość e-mail z powiadomieniem.
   
    **Uwaga**: pola **Temat** i **Opcje użytkownika** możesz dostosować do własnych potrzeb.
   
    ![Obraz pola Wyślij wiadomość e-mail dotyczącą zatwierdzenia do](./media/wait-for-approvals/send-approval-email-to.png)

## <a name="add-a-condition"></a>Dodawanie warunku
1. Wybierz przycisk **+**, a następnie wybierz pozycję **Dodaj warunek**.
   
    ![Obraz dodawania warunku](./media/wait-for-approvals/add-a-condition.png)
2. W polu **Nazwa obiektu** wybierz pozycję **SelectedOption**.
3. W polu **Wartość** wpisz lub wklej ciąg **Zatwierdź**.
   
    ![Obraz karty warunku](./media/wait-for-approvals/condition-card-2.png)
4. W obszarze **Jeśli tak** wybierz pozycję **Dodaj akcję**.
   
    ![Obraz opcji Jeśli tak — Dodaj akcję](./media/wait-for-approvals/yes-add-an-action.png)
5. W polu **Co chcesz zrobić dalej?** wpisz lub wklej ciąg **wyślij wiadomość e-mail**, a następnie wybierz pozycję **Office 365 Outlook — Wyślij wiadomość e-mail**.
   
    ![Obraz opcji Jeśli tak — wyślij wiadomość e-mail](./media/wait-for-approvals/yes-send-email.png)
6. W polu **Temat** określ temat.
   
    Na przykład wybierz pozycję **Przypisano do — DisplayName**, wpisz ciąg **— zatwierdzono element** ze spacją z każdej strony, a następnie wybierz pozycję **Tytuł**.
7. W polu **Treść** określ treść wiadomości e-mail, np. **Można przejść do następnej fazy projektu**.
8. W polu **Do** wprowadź adresata, np. **Utworzono za pomocą poczty e-mail**.
   
    Osoba, która utworzyła element na liście programu SharePoint, zostanie powiadomiona, czy projekt został zatwierdzony, czy odrzucony.
   
    ![Obraz opcji Jeśli tak — wyślij wiadomość e-mail](./media/wait-for-approvals/if-yes-send-email-card-3.png)
9. W obszarze **Jeśli nie** powtórz pięć ostatnich czynności, ale zmień pola **Temat** i **Treść**, aby poinformować o odrzuceniu projektu.
   
     ![Obraz opcji Jeśli nie — wyślij wiadomość e-mail](./media/wait-for-approvals/no-send-email-2.png)

## <a name="finish-and-test-your-flow"></a>Zakończenie i przetestowanie przepływu
1. Nadaj nazwę przepływowi, a następnie wybierz pozycję **Utwórz przepływ**.
   
     ![Obraz tworzenia przepływu](./media/wait-for-approvals/create-flow.png)
2. Utwórz element na liście programu SharePoint.
   
    Wiadomość e-mail dotycząca zatwierdzenia zostanie wysłana do określonego adresata. Gdy adresat wybierze pozycję **Zatwierdź** lub **Odrzuć** w tej wiadomości e-mail, otrzymasz wiadomości e-mail wskazującą odpowiedź. 

