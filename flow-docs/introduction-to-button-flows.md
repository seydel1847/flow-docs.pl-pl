---
title: "Informacje o automatyzowaniu i uruchamianiu powtarzających się zadań przy użyciu przepływów przycisku | Microsoft Docs"
description: "Wprowadzenie do przepływów przycisku."
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
ms.date: 01/30/2017
ms.author: deonhe
ms.openlocfilehash: 558570733819e1fde6c1845ed5ca9debe9232c88
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="introducing-button-flows"></a>Wprowadzenie do przepływów przycisku
## <a name="what-are-button-flows"></a>Co to są przepływy przycisku?
Istnieje wiele powtarzających się zadań, które wszyscy chcielibyśmy uruchamiać jednym naciśnięciem przycisku. Na przykład chcesz szybko wysłać do członków zespołu wiadomość e-mail przypominającą o dołączeniu do codziennego spotkania lub chcesz uruchomić nową kompilację bazy kodu w usłudze Visual Studio Online po otrzymaniu informacji, że w tym dniu nie są już planowane żadne operacje zaewidencjonowania. Przepływy przycisku pozwalają wykonać to i wiele innych zadań po prostu przez naciśnięcie przycisku na urządzeniu przenośnym.

**Uwaga** Przepływy przycisku można utworzyć na urządzeniu przenośnym lub za pomocą portalu usługi Flow.  
  ![Obraz poglądowy](./media/introduction-to-button-flows/buttons-montage.png)  

## <a name="why-create-buttons"></a>Dlaczego warto tworzyć przyciski?
Dzięki utworzeniu przycisków można łatwo uruchamiać powtarzające się zadania z dowolnego miejsca i w dowolnym momencie za pomocą urządzenia przenośnego. Uruchamianie przycisków pozwala zaoszczędzić czas, a ponieważ zadania są wykonywane automatycznie, będzie mniej błędów, niż gdyby były wykonywane ręcznie.  

## <a name="create-a-button"></a>Tworzenie przycisku
### <a name="prerequisites"></a>Wymagania wstępne
* Dostęp do usługi Flow. Dostępu może udzielić administrator.
* Konto z uprawnieniami do korzystania z łączników potrzebnych do utworzenia danego przycisku. Na przykład do utworzenia przycisku, który uzyskuje dostęp do usługi Dropbox, będzie Ci potrzebne konto usługi Dropbox.

### <a name="from-the-portal"></a>W portalu
W tym przewodniku utworzymy przycisk, który uruchamia kompilację w usłudze Visual Studio Online (VSO) i wysyła powiadomienia z informacją o uruchomieniu kompilacji:  

1. Wybierz listę rozwijaną **Pokazywanie** i wybierz kategorię **Przycisk**. Powoduje przefiltrowanie listy szablonów, aby widoczne były te, z których można skorzystać w przepływach przycisku.  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-1.png)   
2. Na liście szablonów wybierz szablon **Trigger a new build in VSO** (Wyzwalaj nową kompilację w usłudze VSO).  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-2.png)  
3. Wybierz przycisk **Użyj tego szablonu** na stronie **Trigger a new build in VSO** (Wyzwalaj nową kompilację w usłudze VSO).   
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-3.png)  
4. Jeśli logowanie zostało pominięte, zostanie wyświetlony monit, aby to teraz zrobić:  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-4.png)  
5. Po zalogowaniu się do usługi Flow zostanie wyświetlony monit o zalogowanie się do łączników używanych w wybranym szablonie. W tym przykładzie w kroku 2 powyżej został wybrany szablon **Trigger a new build in VSO** (Wyzwalaj nową kompilację w usłudze VSO), dlatego konieczne jest zalogowanie się do usługi VSO (i innych łączników, z którymi pracujesz), o ile nie zrobiono tego wcześniej:  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-pre-req-1.png)    
6. Wybierz przycisk **Akceptuj**, jeśli zgadzasz się autoryzować dostęp usługi Flow do Twojego konta usługi VSO.  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-5.png)   
   **Uwaga** W podobny sposób musisz autoryzować każdy łącznik. Gdy wszystko będzie gotowe do przejścia do następnego kroku, powinien zostać wyświetlony widok projektanta, jak poniżej. Wybierz przycisk **Kontynuuj**, aby przejść dalej:  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-6.png)   
7. Teraz można przystąpić do konfigurowania właściwości kompilacji, którą chcesz uruchomić:    
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-7.png)  
8. Wybierz lub wprowadź wartości pól **Nazwa konta**, **Nazwa projektu**, **Identyfikator definicji kompilacji**, **Rozgałęzienie źródłowe** i opcjonalnie **Parametry** na karcie **Dodaj nową kompilację do kolejki**:    
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-8.png)  
9. Następnie skonfiguruj właściwości powiadomienia wypychanego na karcie **Wyślij powiadomienie wypychane**. Domyślnie to powiadomienie wypychane jest skonfigurowane do wysłania linku HTML do strony sieci Web, na której jest wyświetlany stan kompilacji:  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-9.png)  
10. Wybierz przycisk **Utwórz przepływ**, aby zapisać swój przepływ przycisku: ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-10.png)  
11. W ciągu kilku minut powinien zostać wyświetlony ten komunikat o powodzeniu:  
    ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-11.png)  

Gratulacje, przycisk przepływu został utworzony! Od tego momentu można w dowolnym czasie i w dowolnym miejscu uruchamiać ten przepływ przycisku za pomocą karty **Przyciski** w aplikacji Flow. Po prostu naciśnij „przycisk”, a przepływ przycisku zostanie uruchomiony! Aplikacja mobilna usługi Microsoft Flow jest dostępna dla systemów [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) i [Windows Phone](https://aka.ms/flowmobilewindows).

### <a name="from-your-mobile-device"></a>Na urządzeniu przenośnym
**Uwaga**: W ramach tego przewodnika prezentowane są ekrany urządzenia z systemem Android, jednak ekrany i obsługa na urządzeniu z systemem iOS są podobne.

W aplikacji Flow:

1. Wybierz kartę **Przeglądaj**, a następnie przewiń listę do kategorii **Przycisk**.  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-1.png)  
2. Wybierz link **Zobacz wszystkie**. Zostaną wyświetlone wszystkie gotowe do użycia szablony.     
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-2.png)  
3. Wybierz szablon **Send an email to remind your team to join a meeting** (Wyślij wiadomość e-mail przypominającą członkom zespołu o dołączeniu do spotkania).    
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-3.png)  
4. Wybierz link **UŻYJ TEGO SZABLONU** u dołu strony.    
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-4.png)  
5. Musisz zalogować się do wszystkich usług używanych przez ten szablon:    
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-5.png)  
6. Po zalogowaniu się do wszystkich usług wybierz link**Dalej**.      
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-6.png)  
7. Wybierz link **Utwórz**. W tym miejscu można również przejrzeć przepływ i wprowadzić dowolne zmiany, na przykład wymagane w celu spersonalizowania wiadomości e-mail.        
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-7.png)  
8. Po krótkiej chwili przepływ przycisku zostanie utworzony. Wybierz opcję **SEE MY FLOW** (ZOBACZ MÓJ PRZEPŁYW):   
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-8.png)  
9. Wyświetl wszystkie swoje przepływy na karcie **Moje przepływy**.  
   ![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-9.png)  

Gratulacje, przycisk przepływu został utworzony! Od tego momentu można w dowolnym czasie i w dowolnym miejscu uruchamiać ten przepływ przycisku za pomocą karty **Przyciski** w aplikacji Flow. Po prostu naciśnij „przycisk”, a przepływ przycisku zostanie uruchomiony! Aplikacja Flow jest obecnie dostępna na urządzeniach przenośnych z systemem Android lub iOS.  

![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-10.png)  

## <a name="trigger-a-button-flow"></a>Wyzwalanie przepływu przycisku
Teraz, gdy przepływ przycisku został utworzony, można go uruchomić. Ponieważ przepływy przycisku można uruchamiać tylko z aplikacji Flow, upewnij się, że masz ją zainstalowaną na swoim urządzeniu przenośnym z systemem Android lub iOS.  

1. Teraz uruchom aplikację przepływu, naciśnij kartę **Przyciski** znajdującą się w dolnej części strony, a następnie naciśnij *przycisk* reprezentujący przepływ przycisku, który chcesz wyzwolić:  
   ![Obraz poglądowy](./media/introduction-to-button-flows/trigger-button-1.png)   
2. W czasie wykonywania przepływu wyświetlany jest postęp:  
   ![Obraz poglądowy](./media/introduction-to-button-flows/trigger-button-2.png)   
3. Na koniec strona zostanie zaktualizowana, wskazując, że przepływ przycisku został ukończony:  
   ![Obraz poglądowy](./media/introduction-to-button-flows/trigger-button-3.png)   

To wszystko na temat uruchamiania przepływu. 

Teraz powinno nadejść powiadomienie wypychane, wskazujące, że wiadomość e-mail została wysłana.  

## <a name="monitor-your-button-flow-runs"></a>Monitorowanie przebiegów przepływu przycisku
Przepływy przycisku można monitorować, korzystając z karty **Działanie** w aplikacji przepływu:   
![Obraz poglądowy](./media/introduction-to-button-flows/create-button-from-mobile-13.png)  

**Uwaga**: Wybierz dowolne działanie, aby wyświetlić szczegółowe wyniki uruchomienia i dowiedzieć się więcej o przebiegu.  

![Obraz poglądowy](./media/introduction-to-button-flows/activity-details-1.png)  

## <a name="manage-button-flows"></a>Zarządzanie przepływami przycisku
Masz pełną kontrolę nad swoimi przepływami przycisku, dzięki czemu możesz w dowolnym czasie i w dowolnym miejscu włączać i wyłączać, edytować lub usuwać przycisk. Aby rozpocząć zarządzanie przepływami, w aplikacji mobilnej lub w portalu przepływów wybierz opcję **Moje przepływy**.    

Na karcie **Moje przepływy** w aplikacji Flow:

1. Wybierz przepływ, którym chcesz zarządzać:    
   ![Obraz poglądowy](./media/introduction-to-button-flows/trigger-button-4.png)   
2. Możesz wybrać dowolną z tych opcji, w zależności od tego, co chcesz wykonać:    
   ![Obraz poglądowy](./media/introduction-to-button-flows/manage-flow-1.png)  
3. Aby usunąć przepływ, wybierz opcję **Usuń przepływ**.  

**Uwaga** Wraz z usunięciem przepływu zostanie usunięta cała historia wykonywania:   
![Obraz poglądowy](./media/introduction-to-button-flows/manage-flow-2.png)   

1. Po zakończeniu edytowania przepływu przycisku wybierz opcję **Aktualizuj**, aby zapisać zmiany:   
   ![Obraz poglądowy](./media/introduction-to-button-flows/manage-flow-3.png)   
2. Aby wyświetlić wyniki wszystkich przebiegów określonego przepływu przycisku, wybierz opcję **Historia uruchamiania**:    
   ![Obraz poglądowy](./media/introduction-to-button-flows/manage-flow-4.png)  
3. Po wyłączeniu przepływu przestanie on być dostępny na karcie **Przyciski**:    
   ![Obraz poglądowy](./media/introduction-to-button-flows/manage-flow-5.png)  

## <a name="next-steps"></a>Następne kroki
* [Udostępnianie przepływów przycisków](share-buttons.md).
* Dowiedz się, jak używać [tokenów wyzwalacza przycisku](introduction-to-button-trigger-tokens.md) do wysyłania danych w czasie rzeczywistym, gdy są uruchamiane przepływy przycisku.
* Zainstaluj aplikację mobilną usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows).

