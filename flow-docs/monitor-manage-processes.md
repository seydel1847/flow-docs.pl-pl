---
title: Monitorowanie procesów przepływu pracy i zarządzanie nimi w usłudze PowerApps | Microsoft Docs
ms.custom: ''
ms.date: 05/06/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: a987a803-4674-4eb0-87de-caefa003b1eb
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 209b0b63376a9cc0c3ad7d936d7f98f55dfddf00
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690496"
---
# <a name="monitor-and-manage-workflow-processes"></a>Monitorowanie procesów przepływu pracy i zarządzanie nimi

Aby monitorować procesy i zarządzać nimi, należy zlokalizować proces, ocenić jego stan i wykonywać wszystkie działania niezbędne do rozwiązania problemów.  
  
<a name="BKMK_MonitorAsyncWorkflows"></a>   
## <a name="monitoring-background-workflows"></a>Monitorowanie przepływów pracy w tle  
 Przepływy pracy w tle generują rekordy zadań systemowych umożliwiające śledzenie ich stanu. Dostęp do informacji o tych zadaniach systemowych możesz uzyskać w kilku miejscach w aplikacji:  
  
 **[Ustawienia](/powerapps/maker/model-driven-apps/advanced-navigation#settings) > Zadania systemowe**  
 Tutaj znajdują się wszystkie typy zadań systemowych. Konieczne będzie odfiltrowanie rekordów, dla których **Typ zadania systemowego** to **Przepływ pracy**.  
  
 **Z poziomu procesu przepływu pracy**  
 Otwórz definicję przepływu pracy w tle i przejdź do karty **Sesja procesu**. Spowoduje to wyświetlenie tylko zadań systemowych tego przepływu pracy w tle.  
  
 **Z poziomu rekordu**  
 Formularz jednostki możesz edytować tak, aby nawigacja zawierała relację **Procesy w tle**. Spowoduje to wyświetlenie wszystkich zadań systemowych, które zostały uruchomione w kontekście rekordu.  
  
> [!NOTE]
>  Jeśli asynchroniczne zadanie systemowe (przepływ pracy) kończy się niepowodzeniem kilka razy pod rząd, system zaczyna odraczać wykonywanie tego zadania o coraz dłuższe przedziały czasowe tak, aby administrator lub twórca aplikacji mógł zbadać i rozwiązać istniejący problem. Gdy zadanie będzie się kończyć pomyślnie, zostanie wznowione jego normalne wykonywanie.  
  
<a name="BKMK_ActionsOnRunningWorkflows"></a>   
### <a name="actions-on-running-background-workflows"></a>Akcje dotyczące uruchomionych przepływów pracy w tle  
 Gdy przepływ pracy w tle jest uruchomiony, możesz względem niego wykonywać następujące akcje: **Anuluj**, **Wstrzymaj** lub **Odłóż**. Jeśli wcześniej wstrzymano przepływ pracy, dostępna jest akcja **Wznów**.  
  
<a name="BKMK_MonitorSyncWorkflows"></a>   
## <a name="monitoring-real-time-workflows-and-actions"></a>Monitorowanie akcji i przepływów pracy w czasie rzeczywistym  
 Akcje i przepływy pracy w czasie rzeczywistym nie używają rekordów zadań systemowych, ponieważ są wykonywane natychmiast. Wszystkie występujące błędy będą wyświetlane użytkownikowi w aplikacji z nagłówkiem **Błąd procesu biznesowego**.  
  
 Nie jest tworzony dziennik operacji zakończonych powodzeniem. Możesz włączyć rejestrowanie błędów, zaznaczając opcję **Przechowywanie dzienników zadań przepływu pracy, które napotkały błędy** w obszarze **Przechowywanie dzienników przepływu pracy** w dolnej części karty **Administracja** dla procesu.  
  
 Aby wyświetlić dziennik błędów dla określonego procesu, otwórz definicję akcji lub przepływu pracy w czasie rzeczywistym, a następnie przejdź do karty **Sesja procesu**. Spowoduje to wyświetlenie tylko błędów zarejestrowanych dla tego procesu.  
  
 Jeśli chcesz wyświetlić wszystkie błędy dla dowolnego procesu, wybierz pozycję **Wyszukiwanie zaawansowane** i utwórz widok przedstawiający błędy dla jednostki sesji procesu.  
  
<a name="BKMK_StatusOfWorkflowProcesses"></a>   
## <a name="status-of-workflow-processes"></a>Stan procesów przepływu pracy  
 Podczas wyświetlania listy procesów przepływu pracy poszczególne procesy mogą mieć jedną z następujących wartości **Stan** i **Przyczyna stanu**:  
  
|Stan|Przyczyna stanu|  
|-----------|-------------------|  
|Gotowe|Oczekiwanie na zasoby|  
|Wstrzymano|Oczekiwanie|  
|Zablokowano|W toku<br /><br /> Wstrzymywanie<br /><br /> Anulowanie|  
|Ukończono|Zakończono powodzeniem<br /><br /> Niepowodzenie<br /><br /> Anulowano|  

## <a name="deleting-process-log-records"></a>Usuwanie rekordów dziennika procesu

Jeśli Twoja organizacja korzysta z przepływów pracy w tle lub z przepływów procesów biznesowych, które są często uruchamiane, liczba rekordów dzienników procesów może się stać na tyle duża, że będzie powodować problemy z wydajnością, a także zużywać znaczące ilości miejsca w magazynie. Aby usuwać rekordy dzienników procesów, które nie są odpowiednio usuwane przez jedno ze standardowych zadań zbiorczego usuwania rekordów, możesz użyć funkcji zbiorczego usuwania zadań systemowych w celu utworzenia niestandardowego zadania zbiorczego usuwania rekordów.

1. Wybierz pozycję **Ustawienia** > **Zarządzanie danymi** > **Zbiorcze usuwanie rekordów**.
2. W obszarze **Zbiorcze usuwanie rekordów** wybierz opcję **Nowe**. 
3. Na stronie początkowej **Kreatora usuwania zbiorczego** wybierz przycisk **Dalej**.
4. Na liście **Wyszukaj** wybierz pozycję **Zadania systemowe**.
5. Poniższe warunki umożliwiają utworzenie zadania zbiorczego usuwania rekordów służącego do usuwania rekordów dzienników procesów. 
 - **Typ zadania systemowego Równe Przepływ pracy**. Dzięki temu zadanie obejmie rekordy przepływów pracy. 
 - **Stan Równe Ukończono**. Zadanie może być uruchamiane tylko dla ukończonych przepływów pracy.
 - **Przyczyna stanu Równe Zakończono powodzeniem**. Usuń zadania zakończone pomyślnie, anulowane i zakończone niepowodzeniem.
 - **Data ukończenia Starsze niż X dni 30**. Używając pola Data ukończenia, usuń tylko rekordy dzienników procesów przepływów pracy starsze niż 30 dni.
 ![custom-bulk-record-deletion.png](media/custom-bulk-record-deletion.png)
6. Kliknij przycisk **Dalej**.
7. Ustaw częstotliwość uruchamiania zadania zbiorczego usuwania. Możesz zaplanować uruchamianie zadania w ustalonych odstępach czasu lub utworzyć jednorazowe zadanie zbiorczego usuwania [za pomocą opcji Natychmiast](#using-the-immediately-option). W tym przykładzie ustawiono uruchamianie zadania cyklicznego 21 maja 2018 r. i co każde kolejne 30 dni. 
![Opcje zbiorczego usuwania rekordów](media/custom-bulk-record-delete-options.png)

### <a name="using-the-immediately-option"></a>Używanie opcji Natychmiast

Zwróć uwagę na możliwość przeprowadzenia natychmiastowego synchronicznego zbiorczego usunięcia rekordów przez wybranie opcji **Natychmiast**. To usunięcie odbywa się przy użyciu bezpośredniego wykonania programu SQL Server, a nie przekazywania każdego rekordu za pośrednictwem potoku zdarzeń usuwania, co może zmniejszyć wpływ na wydajność systemu. Jest to dobra opcja, jeśli chcesz szybko oczyścić dodatkowe rekordy przepływów pracy, zamiast czekać na przetworzenie zadania zbiorczego usuwania znajdującego się w asynchronicznej kolejce. 

Opcja **Natychmiast** jest włączona, gdy są spełnione następujące warunki: 
- Zadanie zbiorczego usuwania dotyczy jednostki Zadania systemowe.
- Kryterium wyszukiwania zawiera warunek Typ zadania systemowego Równe Przepływ pracy. 
- Użytkownik tworzący zadanie zbiorczego usuwania ma globalne uprawnienie usuwania w jednostce AsyncOperation. Rola zabezpieczeń administratora systemu ma to uprawnienie.  

Synchroniczne usuwanie zbiorcze usunie jedynie rekordy AsyncOperation o stanie Ukończono. Dla każdego wywołania jest przetwarzanych nie więcej niż jeden milion rekordów. Jeśli w środowisku jest więcej niż jeden milion rekordów do usunięcia, należy uruchomić zadanie wielokrotnie.  
  
## <a name="next-steps"></a>Następne kroki   
 [Najlepsze rozwiązania dotyczące procesów przepływu pracy](best-practices-workflow-processes.md) <br />

