---
title: Dodawanie opcji zaawansowanej i wielu akcji | Microsoft Docs
description: "Rozwiń przepływ, uwzględniając w nim opcję zaawansowaną, taką jak ustawienie wysokiego priorytetu wiadomości e-mail, i dodaj kolejną akcję dla tego samego zdarzenia."
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/20/2017
ms.author: stepsic
ms.openlocfilehash: f6c936cbf5a2bd481adb52ec9b01545fb9ba7b0b
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="add-multiple-actions-and-advanced-options-to-a-flow"></a>Dodawanie wielu akcji i opcji zaawansowanych do przepływu
Dostosuj przepływ, dodając jedną lub więcej opcji zaawansowanych i wiele akcji dla tego samego wyzwalacza. Możesz na przykład dodać opcję zaawansowaną, która wysyła wiadomość e-mail, nadając jej wysoki priorytet. Oprócz wysyłania wiadomości e-mail po dodaniu elementu do listy programu SharePoint, możesz też utworzyć plik zawierający te same informacje w usłudze Dropbox.

## <a name="prerequisites"></a>Wymagania wstępne
* [Tworzenie przepływu](get-started-logic-flow.md)

## <a name="add-another-action"></a>Dodawanie kolejnej akcji
W tej procedurze do środka przepływu zostanie dodana akcja. Ta akcja spowoduje zapisanie pliku w usłudze Dropbox, archiwizując element na liście.

1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) wybierz pozycję **Moje przepływy** na górnym pasku nawigacji.
2. Na liście przepływów wybierz ten, który chcesz edytować.
3. Wybierz pozycję **Nowy krok**, a następnie wybierz pozycję **Dodaj akcję**.
   
    ![Zwinięte dodawanie](./media/multi-step-logic-flow/add-action.png)
4. Na liście dostępnych akcji wyszukaj pozycję **Utwórz plik**, a następnie wybierz pozycję **Dropbox — Utwórz plik**.
   
    ![wyszukiwanie pozycji utwórz plik](./media/multi-step-logic-flow/create-file-search.png)
5. Jeśli wyświetli się monit, wprowadź swoje poświadczenia usługi Dropbox.
6. Wybierz ikonę folderu po prawej stronie pola **Ścieżka folderu**.
7. Znajdź, a następnie wybierz folder, w którym chcesz umieścić nowy plik.
   
    ![wyszukiwanie pozycji utwórz plik](./media/multi-step-logic-flow/create-file-folder.png)
8. Wprowadź nazwę nowego pliku w polu **Nazwa pliku**. Pamiętaj o dodaniu do nazwy pliku rozszerzenia, takiego jak „.txt”. W tym przypadku użyjemy w nazwie pliku wartości **Identyfikator tweetu** w celu zapewnienia unikatowości plików. Może być konieczne wybranie pozycji **Zobacz więcej**, aby znaleźć token **Identyfikator tweetu**.
9. Dodaj tekst, który powinien znaleźć się w pliku, wpisując go w polu **Zawartość pliku**. W polu **Zawartość pliku** możesz też dodać tokeny.
   
    ![nazwa pliku i zawartość](./media/multi-step-logic-flow/create-file-name-and-contents.png)
   
   > [!IMPORTANT]
   > Jeśli nadasz plikowi nazwę, którą ma już istniejący plik (w wybranym folderze), ten istniejący plik zostanie zastąpiony.
   > 
   > 
10. Wybierz pozycję **Aktualizuj przepływ**, która znajduje się w menu w górnej części ekranu.
11. Wyślij tweet zawierający określone przez Ciebie słowo kluczowe.
    
     W ciągu minuty na Twoim koncie Dropbox zostanie utworzony plik.

## <a name="reorder-or-delete-an-action"></a>Zmiana kolejności lub usuwanie akcji
* Aby otrzymać wiadomość e-mail po utworzeniu pliku w usłudze Dropbox, przeciągając pasek tytułu, przenieś akcję dotyczącą usługi Dropbox powyżej akcji dotyczącej wiadomości e-mail. Upuść ją nad strzałką znajdującą się między wyzwalaczem (**Po wysłaniu nowego tweetu**) a akcją dotyczącą wiadomości e-mail. (Kursor wskaże, że akcja jest umieszczona poprawnie).
  
  > [!NOTE]
  > Nie można przenieść danego kroku przed inny, jeśli są używane jakiekolwiek dane wyjściowe z tego kroku.
  > 
  > 
  
    ![Usuwanie menu](./media/multi-step-logic-flow/draggingaction.png)
* Aby usunąć akcję, wybierz symbol wielokropka (...) obok prawej krawędzi paska tytułu akcji, którą chcesz usunąć, wybierz polecenie **Usuń**, a następnie wybierz pozycję **OK**.
  
    ![Usuwanie menu](./media/multi-step-logic-flow/deletemenu.png)
  
     **Uwaga:** Nie można usunąć danej akcji, jeśli jakiekolwiek dane wyjściowe z tej akcji są używane w dowolnym miejscu przepływu. Najpierw należy usunąć te dane wyjściowe z pól, a następnie można usunąć akcję.

## <a name="add-advanced-options"></a>Dodawanie opcji zaawansowanych
Rozpocznij przy użyciu przepływu, który zawiera akcję **Wyślij wiadomość e-mail**.

1. Wybierz pozycję **Pokaż opcje zaawansowane**, która znajduje się w dolnej części karty **Wyślij wiadomość e-mail**.
   
     Zostaną wyświetlone opcje zaawansowane wysyłania wiadomości e-mail.
   
    ![Wyzwalacze programu SharePoint](./media/multi-step-logic-flow/advanced.png)
2. Na liście **Ważność** wybierz pozycję **Wysoka**, a następnie wybierz pozycję **Ukryj opcje zaawansowane**, aby ukryć opcje zaawansowane.
3. Wybierz pozycję **Aktualizuj przepływ**, która znajduje się w menu w górnej części ekranu.
   
     Ta czynność spowoduje zapisanie zmian.

