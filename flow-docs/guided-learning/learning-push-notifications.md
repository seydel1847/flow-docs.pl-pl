---
title: "Publikowanie tweetów z przepływu | Microsoft Docs"
description: "Dowiedz się, jak publikować tweety na podstawie danych z listy programu SharePoint."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: y1iDal8XPAo
courseduration: 15m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: 4015377204edfde289cf04835b2660288d0690e1
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="post-tweets-from-a-flow"></a>Publikowanie tweetów z przepływu
Na potrzeby tego przepływu utworzysz listę programu **SharePoint**, w ramach której zespół ds. marketingu w firmie **Contoso Flooring** przechowuje swoje **wpisy z usługi Twitter** oraz daty ich publikacji. Następnie utworzysz przepływ, który automatycznie opublikuje te tweety. 

## <a name="connect-microsoft-flow-services"></a>Łączenie usług Microsoft Flow
W tym temacie będziesz używać usług **SharePoint** i **Twitter**. Jeśli pierwszy raz używasz danej usługi, musisz najpierw nawiązać połączenie z tą usługą. 

1. W usłudze Microsoft Flow wybierz **ikonę koła zębatego**, a następnie pozycję **Połączenia**.
   
    ![Nawiązywanie połączenia](./media/learning-push-notifications/2-get-connection.png) 
2. Wybierz pozycję **+ Utwórz połączenie**.
   
    ![Tworzenie połączenia](./media/learning-push-notifications/3-create-connection.png) 
3. Przewiń w dół listy, znajdź pozycję Twitter, a następnie wybierz pozycję **+**.
   
    ![Kliknij przycisk plus](./media/learning-push-notifications/4-click-plus.png)
4. Aby autoryzować konto w usłudze Twitter, wprowadź nazwę użytkownika lub adres e-mail oraz swoje hasło, a następnie wybierz pozycję **Autoryzuj aplikację**.
   
    ![Tworzenie identyfikatora i hasła](./media/learning-push-notifications/5-create-id-pswd.png)
5. Aby sprawdzić połączenia, wybierz **ikonę koła zębatego** i pozycję **Połączenia**.
   
    ![Moje połączenia](./media/learning-push-notifications/6-my-connections.png)
   
    Powinno zostać wyświetlone nowe połączenie z usługą Twitter oraz wszystkie inne utworzone przez Ciebie połączenia. 
   
    ![Łączenie z usługą Twitter](./media/learning-push-notifications/7-twitter-connection.png)

## <a name="build-a-sharepoint-list"></a>Tworzenie listy programu SharePoint
Musisz zacząć od utworzenia nowej listy w usłudze SharePoint Online dla firmy Contoso Flooring. 

1. W usłudze SharePoint Online wybierz pozycję **Nowy**, a następnie pozycję **Lista**.
   
    ![Tworzenie nowej listy](./media/learning-push-notifications/1-new-list.png)
2. Nadaj liście nazwę **Tweety Contoso**. 
3. Wyczyść pole wyboru **Pokaż w nawigacji po witrynie**, a następnie wybierz pozycję **Utwórz**.
   
    ![Tworzenie listy](./media/learning-push-notifications/2-name-create-list.png)
   
    Po wybraniu pozycji **Utwórz** program SharePoint wyświetli nową listę.
4. Domyślnie lista zawiera jedną kolumnę — **Tytuł**. Dodaj kolejną kolumnę i nadaj jej nazwę **Treść tweetu**. Treść Twoich tweetów będzie umieszczona w tej kolumnie. 
   
   1. Wybierz znak plus, a następnie wybierz pozycję **Więcej...**
      
       ![Tworzenie listy](./media/learning-push-notifications/3-add-more-column-types.png)
   2. Wybierz pozycję **Wiele wierszy tekstu**, a następnie wybierz pozycję **OK**.
      
       ![Tworzenie listy](./media/learning-push-notifications/4-add-column.png)
5. Dodaj kolumnę daty i godziny dla tweetów i nadaj jej nazwę **Data tweetu**.
   
   1. Podobnie jak w przypadku kolumny **Treść tweetu** powyżej, kliknij znak plus, a następnie wybierz pozycję **Więcej...**
      
       ![Kolumna daty i godziny](./media/learning-push-notifications/5-date-time-col.png)
   2. Przewiń w dół do pozycji **Format daty i godziny**. Wybierz pozycję **Data i godzina**, aby uwzględnić obie informacje.
      
       ![Data i godzina](./media/learning-push-notifications/6-date-time-must-do.png)
   3. Wybierz przycisk **OK**. Lista **Tweety Contoso** jest wyświetlana w witrynie programu SharePoint i możesz dodawać do niej nowe elementy.

## <a name="build-the-flow"></a>Tworzenie przepływu
Twoja lista została utworzona, więc możesz teraz utworzyć przepływ.

### <a name="choose-a-trigger"></a>Wybór wyzwalacza
1. W usłudze Microsoft Flow wybierz pozycję **Moje przepływy**, a następnie wybierz pozycję **Utwórz z pustego**.
   
    ![Tworzenie z pustego](./media/learning-push-notifications/8-create-from-blank.png)
2. Wybierz pozycję **Po utworzeniu elementu**.
   
    ![Dodawanie wyzwalacza](./media/learning-push-notifications/9-add-trigger.png)
   
    Chcemy, aby wyzwalacz był uruchamiany po dodaniu nowego wiersza z treścią tweetu.
3. Wybierz witrynę programu SharePoint, a następnie wybierz skonfigurowaną wcześniej listę **Tweety Contoso**.
   
    ![Utworzono nowy element](./media/learning-push-notifications/11-set-trigger.png)

To wszystko, jeśli chodzi o wyzwalacz.

### <a name="add-an-action-to-delay-posting"></a>Dodawanie akcji opóźnienia publikowania
1. Wybierz pozycję **+ Nowy krok**, a następnie wybierz pozycję **Dodaj akcję**. 
   
    ![Dodawanie kroku i akcji](./media/learning-push-notifications/12-add-step-and-action.png)
2. W obszarze usługi **Harmonogram** wybierz pozycję **Opóźnienie do**. 
   
    ![Opóźnienie do](./media/learning-push-notifications/13-delay-until-schedule.png)  
3. Ustaw wartość opóźnienia.
   
   1. Kliknij lub naciśnij pole **Sygnatura czasowa**. 
   2. Po otwarciu okna zawartości dynamicznej przewiń w dół, aby zobaczyć trzy kolumny z listy programu SharePoint: **Tytuł**, **Data tweetu** i **Treść tweetu**.
   3. Wybierz kolumnę **Data tweetu**. 
      
       ![Opóźnienie do sygnatury czasowej](./media/learning-push-notifications/14-delay-until-timestamp.png)
      
       Teraz po dodaniu elementu do listy programu SharePoint wykonanie akcji zostanie opóźnione do nadejścia dnia i godziny określonych w kolumnie **Data tweetu**.
      
       ![Dynamiczna sygnatura czasowa](./media/learning-push-notifications/15-dynamic-timestamp.png)

### <a name="add-an-action-to-post-a-tweet"></a>Dodawanie akcji publikowania tweetu
Teraz dodasz kolejną akcję, którą przepływ ma wykonać w dniu i o godzinie określonej w kolumnie **Data tweetu**.

1. Wybierz pozycję **+ Nowy krok**, **Dodaj akcję**, a następnie wyszukaj ciąg **Twitter**.
   
    ![Dodawanie tweetu](./media/learning-push-notifications/16-add-tweet.png) 
2. Wybierz akcję **Twitter — Wyślij tweet**.
   
    ![Wysyłanie tweetu](./media/learning-push-notifications/17-post-tweet.png) 
3. Kliknij lub naciśnij pole **Tekst tweetu**, a w polu zawartości dynamicznej wybierz pozycję **Treść tweetu**. Oto utworzona sekwencja. 
   
    ![Zawartość daty tweetu](./media/learning-push-notifications/18-tweet-date-content.png)
4. Wybierz pozycję **Utwórz przepływ...**
   
    ![Tworzenie przepływu](./media/learning-push-notifications/19-tiny-create.png) 
5. Wybierz pozycję **Gotowe**.
   
    ![Klikanie pozycji Gotowe](./media/learning-push-notifications/19-click-done.png)
   
    Przepływ jest gotowy.
   
    ![Przepływ jest gotowy](./media/learning-push-notifications/20-flow-is-done.png)
   
    Po utworzeniu nowego elementu na liście programu SharePoint przepływ opóźni publikację do wcześniej określonej daty. Po spełnieniu warunku daty przepływ opublikuje tweet w usłudze Twitter, pobierając tekst z kolumny **Treść tweetu** na liście.

## <a name="next-lesson"></a>Następna lekcja
W ramach następnej lekcji dowiesz się, jak **uruchamiać przepływy zgodnie z harmonogramem** przy użyciu wyzwalacza o nazwie **Cykl**.

