---
title: Najlepsze rozwiązania dotyczące procesów przepływu pracy w usłudze PowerApps | MicrosoftDocs
description: Informacje o zalecanych sposobach użycia przepływów pracy
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 34e34c33-003a-494f-858c-3d34aacb308c
caps.latest.revision: 10
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: bba5b203782cfa813de6ddc509a8be604e5e146b
ms.sourcegitcommit: 50ea1cdd763863a2cbc88f9f965bdf9351f1059c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51225545"
---
# <a name="best-practices-for-workflow-processes"></a>Najlepsze rozwiązania dotyczące procesów przepływu pracy

Ten temat zawiera informacje o najlepszych rozwiązaniach dotyczących tworzenia procesów przepływu pracy i zarządzania nimi.  
  
<a name="BKMK_AvoidInfiniteLoops"></a>   
## <a name="avoid-infinite-loops"></a>Unikanie nieskończonych pętli  
 W przepływie pracy istnieje możliwość utworzenia logiki inicjującej nieskończoną pętlę, która zużywa zasoby serwera i wpływa na wydajność. Zwykle nieskończona pętla może wystąpić w sytuacji, gdy przepływ pracy jest skonfigurowany tak, aby uruchamiał się, gdy atrybut jest aktualizowany, a następnie aktualizuje ten atrybut w logice przepływu pracy. Akcja aktualizacji wyzwala ten sam przepływ pracy, który aktualizuje rekord i wciąż na nowo wyzwala przepływ pracy.  
  
 Tworzone przepływy pracy zawierają logikę do wykrywania i zatrzymywania nieskończonych pętli. Jeśli proces przepływu pracy zostanie uruchomiony więcej niż określona liczba razy na określony rekord w krótkim czasie, proces zakończy się niepowodzeniem z następującym błędem: **To zadanie przepływu pracy zostało anulowane, ponieważ przepływ pracy, który je zainicjował, zawierał nieskończoną pętlę. Popraw logikę przepływu pracy i spróbuj ponownie**. Limit wynosi 16 razy.  
  
<a name="BKMK_UseWorkflowTemplates"></a>   
## <a name="use-workflow-templates"></a>Używanie szablonów przepływów pracy  
 Jeśli masz podobne przepływy pracy i planujesz utworzenie większej liczby przepływów pracy, które wykonują te same czynności, zapisz przepływ pracy jako szablon przepływu pracy. Dzięki temu następnym razem, gdy zajdzie konieczność utworzenia podobnego przepływu pracy, będzie można go utworzyć przy użyciu szablonu i nie będzie konieczne wprowadzanie wszystkich warunków i akcji od początku.  
  
 W oknie dialogowym **Tworzenie procesu** wybierz pozycję **Nowy proces z istniejącego szablonu (wybierz z listy)**.  
  
<a name="BKMK_UseChildWorkflows"></a>   
## <a name="use-child-workflows"></a>Używanie podrzędnych przepływów pracy  
 Jeśli ta sama logika jest stosowana w różnych przepływach pracy lub gałęziach warunkowych, zdefiniuj tę logikę jako podrzędny przepływ pracy, dzięki czemu nie będzie trzeba replikować tej logiki ręcznie w każdym przepływie pracy lub gałęzi warunkowej. Dzięki temu utrzymywanie przepływów pracy jest łatwiejsze. Zamiast badać wiele przepływów pracy, które mogą stosować tę samą logikę, wystarczy zaktualizować tylko jeden przepływ pracy.  
  
## <a name="automatically-delete-completed-workflow-jobs"></a>Automatyczne usuwanie ukończonych zadań przepływu pracy
W przypadku przepływów pracy w tle (asynchronicznych) zalecane jest wybranie opcji **Automatycznie usuwaj zakończone zadania przepływu pracy (aby zwolnić miejsce na dysku)** w definicji przepływu pracy. Zaznaczenie tego pola wyboru umożliwia systemowi usuwanie dzienników przepływu pracy po pomyślnym wykonaniu w celu zaoszczędzenia miejsca. Należy zauważyć, że dzienniki z wykonań przepływów pracy, które się nie powiodły, zawsze będą zapisywane w celu rozwiązywania problemów.  

![Przechowywanie zadań przepływu pracy](media/workflow-job-retention.png)

<a name="BKMK_AutoDeleteCompletedWorkflowJobs"></a>   
## <a name="keep-logs-for-workflow-jobs-that-encountered-errors"></a>Przechowywanie dzienników zadań przepływu pracy, które napotkały błędy  
W przypadku przepływów pracy, które nie działają w tle (synchroniczne), zalecane jest wybranie opcji **Przechowywanie dzienników zadań przepływu pracy, które napotkały błędy** w definicji przepływu pracy. Wybranie tej opcji umożliwia zapisanie dzienników z wykonań przepływów pracy, które się nie powiodły, w celu rozwiązywania problemów. Dzienniki z pomyślnych wykonań synchronicznego przepływu pracy zawsze będą usuwane w celu zaoszczędzenia miejsca.   

![Opcja zachowywania dzienników z przepływów pracy, które się nie powiodły](media/keep-logs-for-workflows.png)

## <a name="limit-the-number-of-workflows-that-update-the-same-entity"></a>Ograniczanie liczby przepływów pracy, które aktualizują tę samą jednostkę
Uruchomienie więcej niż jednego przepływu pracy, który aktualizuje tę samą jednostkę, może powodować problemy z blokowaniem zasobów. Wyobraź sobie wiele uruchomionych przepływów pracy, w których każda aktualizacja szansy sprzedaży powoduje aktualizację powiązanego klienta. Gdy wiele wystąpień tych przepływów pracy działa i próbuje jednocześnie zaktualizować ten sam rekord klienta, mogą pojawić się problemy z blokadą zasobów. Wystąpią błędy przepływu pracy i zostanie zarejestrowany komunikat o błędzie, taki jak **Limit czasu SQL: nie można uzyskać blokady zasobu _nazwa zasobu_**. 

  
<a name="BKMK_DocumentChangesUsingNotes"></a>   
## <a name="use-notes-to-keep-track-of-changes"></a>Używanie karty Uwagi do śledzenia zmian  
 Podczas edytowania przepływów pracy warto używać karty Uwagi do notowania, co zostało zrobione i dlaczego. Dzięki temu inny użytkownik będzie mógł zapoznać się z wprowadzonymi zmianami.  
  
## <a name="next-steps"></a>Następne kroki  
 [Omówienie procesów przepływu pracy](workflow-processes.md)   
 [Konfigurowanie procesów przepływu pracy](configure-workflow-steps.md)   
 [Monitorowanie procesów przepływu pracy i zarządzanie nimi](monitor-manage-processes.md)
   
