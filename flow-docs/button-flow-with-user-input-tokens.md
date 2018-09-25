---
title: Informacje o automatyzowaniu powtarzających się zadań przy użyciu przepływów przycisku, które akceptują dane wejściowe użytkownika | Microsoft Docs
description: Usługa Microsoft Flow ułatwia automatyzację powtarzających się zadań. Przepływy mogą nawet akceptować dane wejściowe użytkownika podczas uruchamiania powtarzającego się zadania.
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
ms.date: 02/15/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: f87b0d93b912799a4977f347d89b12421cf42e70
ms.sourcegitcommit: ffed9f02092fbd19fc4108aee05dd40d1a2a3755
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711570"
---
# <a name="introducing-button-flows-with-user-input"></a>Wprowadzenie do przepływów przycisku z danymi wejściowymi użytkownika
Utwórz przepływ przycisku do uruchamiania rutynowych zadań za pomocą prostego naciśnięcia przycisku. Dostosuj przepływ przez umożliwienie użytkownikowi wprowadzenia konkretnych szczegółów, które zostaną użyte podczas przebiegów przepływów. W tym temacie omówiono tworzenie przepływu przycisku, który akceptuje dane wejściowe od użytkownika, a następnie uruchomienie przepływu przycisku ze szczególnym naciskiem na wprowadzanie danych wejściowych użytkownika.

Możesz utworzyć przepływ przycisku w witrynie internetowej usługi Microsoft Flow lub aplikacji mobilnej dla usługi Microsoft Flow. W tym temacie opisano korzystanie z witryny internetowej.

### <a name="prerequisites"></a>Wymagania wstępne
* Konto w witrynie internetowej usługi Microsoft Flow.

## <a name="open-the-template"></a>Otwieranie szablonu
1. Zaloguj się w [witrynie usługi Microsoft Flow](https://flow.microsoft.com), wpisz **Visual Studio** w polu wyszukiwania, a następnie kliknij lub naciśnij ikonę wyszukiwania, aby znaleźć wszystkie szablony związane z programem Visual Studio.
   
    ![](./media/button-flow-with-user-input-tokens/1.png)  
2. Wybierz szablon **Otwórz usterkę priorytetu 2 w programie Visual Studio**:
   
    ![](./media/button-flow-with-user-input-tokens/2.png)  
3. Wybierz przycisk **Użyj tego szablonu**:
   
    ![](./media/button-flow-with-user-input-tokens/3.png)  
   
    Ten szablon korzysta z usług Visual Studio Team Services (VSTS) oraz usług powiadomień wypychanych. Należy zalogować się w tych usługach, jeśli nie nawiązano połączenia z żadną z nich. Przycisk **Zaloguj** zostanie wyświetlony tylko wtedy, gdy konieczne będzie zalogowanie się w usłudze.
4. Po zalogowaniu się we wszystkich wymaganych usługach wybierz przycisk **Dalej**:
   
    ![](./media/button-flow-with-user-input-tokens/4.png)  
5. (opcjonalnie) Zmień nazwę przepływu, wpisując wybraną przez siebie nazwę w polu w górnej części portalu:
   
    ![](./media/button-flow-with-user-input-tokens/5.png)

## <a name="customize-the-user-input"></a>Dostosowywanie danych wejściowych użytkownika
1. Na karcie wyzwalacza wybierz pozycję **Edytuj**:
   
    ![](./media/button-flow-with-user-input-tokens/6.png)  
2. Wybierz ikonę **+**, aby rozwinąć stronę i umożliwić dodawanie niestandardowych pól danych wejściowych:
   
    ![](./media/button-flow-with-user-input-tokens/7.png)
3. Wprowadź **Tytuł danych wejściowych** i **Opis danych wejściowych** dla każdego pola niestandardowego, które ma być dostępne, gdy ktoś uruchamia przepływ.  
   
    W tym przykładzie utworzysz dwa pola niestandardowych danych wejściowych (**Kroki odtwarzania usterki** i **Waga usterki**), aby każda osoba korzystająca z tego przepływu mogła wprowadzić kroki umożliwiające odtworzenie usterki i ocenić jej wagę:  
   
    ![](./media/button-flow-with-user-input-tokens/8.png)

## <a name="customize-the-bug"></a>Dostosowywanie usterki
1. Naciśnij pasek tytułu karty **Utwórz nowy element roboczy**:
   
    ![](./media/button-flow-with-user-input-tokens/9.png)  
2. Wybierz opcje odpowiednie do środowiska usług VSTS, a następnie wybierz pozycję **Edytuj**:
   
    Na przykład połącz się z witryną myinstance.visualstudio.com, wpisując **myinstance**.
   
    ![](./media/button-flow-with-user-input-tokens/10.png)  
3. Wybierz pozycję **Pokaż opcje zaawansowane**, aby wyświetlić inne pola dla tej karty:
   
    ![](./media/button-flow-with-user-input-tokens/11.png)  
4. Umieść kursor przed tokenem **Tytuł usterki**, a następnie wpisz „Waga: ” w polu tekstowym **Tytuł**.
5. Pozostaw kursor w polu tekstowym tytułu, wybierz token **Waga usterki**, a następnie wpisz „ -- ”.  
6. W polu tekstowym **Opis** umieść kursor tuż za tokenem **Opis usterki**, a następnie naciśnij klawisz Enter, aby rozpocząć nowy wiersz.
7. Umieść kursor w nowym wierszu, a następnie wybierz token **Kroki odtwarzania usterki**:
   
    ![](./media/button-flow-with-user-input-tokens/12.png)

## <a name="customize-the-push-notification"></a>Dostosowywanie powiadomienia wypychanego
1. Naciśnij pasek tytułu na karcie **Wysyłanie powiadomienia wypychanego**, aby ją rozwinąć.
2. Z listy tokenów zawartości dynamicznej wybierz pozycję **Zobacz więcej**, a następnie dodaj token **Adres URL** w polu tekstowym **Link**.
3. W polu tekstowym **Etykieta linku** dodaj token **Identyfikator**:
   
    ![](./media/button-flow-with-user-input-tokens/13.png)  
4. Naciśnij w menu pozycję **Utwórz przepływ**, aby utworzyć przepływ: ![](./media/button-flow-with-user-input-tokens/14.png)  

## <a name="run-your-flow"></a>Uruchamianie przepływu
W tym przewodniku uruchomisz utworzony właśnie przepływ przycisku za pomocą aplikacji mobilnej dla usługi Microsoft Flow. Podasz wszystkie dane wejściowe użytkownika niezbędne do utworzenia usterki z tytułem, opisem, krokami odtworzenia i poziomem wagi.  

1. W aplikacji mobilnej dla usługi Microsoft Flow naciśnij kartę **Przyciski**, a następnie naciśnij przycisk **Utwórz raport o usterce z krokami**.
   
    ![](./media/button-flow-with-user-input-tokens/runmt1.png)  
2. Wprowadź tytuł zgłaszanej usterki, a następnie naciśnij przycisk **Dalej**. Na przykład:
   
    ![](./media/button-flow-with-user-input-tokens/runmt2.png)  
3. Wprowadź opis zgłaszanej usterki, a następnie naciśnij przycisk **Dalej**. Na przykład:
   
    ![](./media/button-flow-with-user-input-tokens/runmt3.png)  
4. Wprowadź kroki umożliwiające odtworzenie zgłaszanej usterki, a następnie naciśnij przycisk **Dalej**. Na przykład:
   
    ![](./media/button-flow-with-user-input-tokens/runmt3-1.png)  
5. Wprowadź wagę zgłaszanej usterki, a następnie naciśnij przycisk **Dalej**.  
    ![](./media/button-flow-with-user-input-tokens/runmt3-2.png)  
   
    Zostanie wykonany przebieg przepływu.
6. (opcjonalnie) Naciśnij kartę **Działanie**, aby wyświetlić wyniki.
   
    ![](./media/button-flow-with-user-input-tokens/runmt5.png)  
7. (opcjonalnie) Wyświetl szczegółowe wyniki przebiegu przepływu, naciskając krok **Utwórz nowy element roboczy**.
   
    ![](./media/button-flow-with-user-input-tokens/runmt6.png)  

## <a name="next-steps"></a>Następne kroki
* [Udostępnianie przepływów przycisków](share-buttons.md)
* [Więcej informacji na temat przepływów przycisku](introduction-to-button-flows.md)  
* [Więcej informacji na temat przepływów przycisku z tokenami wyzwalacza](introduction-to-button-trigger-tokens.md)  

