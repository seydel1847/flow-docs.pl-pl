---
title: Konfigurowanie etapów i kroków przepływu pracy w usłudze PowerApps | Microsoft Docs
description: Dowiedz się, jak skonfigurować kroki przepływu pracy
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 0b47dfd5-76db-464f-90c0-c64a0173dcdd
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 8e34f8ef8847ab08e14c91ee6d7871697b0275ce
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690450"
---
# <a name="configure-workflow-stages-and-steps"></a>Konfigurowanie etapów i kroków przepływu pracy

Podczas projektowania przepływów pracy masz możliwość dodania wykonywanej logiki w postaci etapów i kroków.  
  
 **Etapy**  
 Etapy zwiększają czytelność logiki przepływu pracy i stanowią jej objaśnienie. Jednak etapy nie wpływają na logikę ani zachowanie przepływów pracy. Jeśli proces ma etapy, wszystkie kroki w ramach procesu muszą znajdować się w etapach.  
  
 **Kroki**  
 Krok to jednostka logiki biznesowej w przepływie pracy. Kroki mogą obejmować warunki, akcje, inne kroki lub kombinację tych elementów.  
  
<a name="BKMK_ActionsWorkflowProcessesCanPerform"></a>  
 
## <a name="actions-that-workflow-processes-can-perform"></a>Akcje, które mogą wykonywać procesy przepływu pracy  

 Procesy przepływu pracy mogą wykonywać akcje przedstawione w poniższej tabeli.  
  
|Akcja|Opis|  
|------------|-----------------|  
|**Utwórz rekord**|Umożliwia utworzenie nowego rekordu dla jednostki i przypisanie wybranych wartości do atrybutów.|  
|**Aktualizuj rekord**|Istnieje możliwość zaktualizowania rekordu, którego dotyczy przepływ pracy, dowolnego rekordu połączonego z tym rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Przypisz rekord**|Istnieje możliwość przypisania rekordu, którego dotyczy przepływ pracy, dowolnego rekordu połączonego z takim rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Wyślij wiadomość e-mail**|Umożliwia wysłanie wiadomości e-mail. Istnieje możliwość utworzenia nowej wiadomości e-mail lub użycia szablonu wiadomości e-mail skonfigurowanego dla jednostki rekordu, której dotyczy przepływ pracy, dowolnej jednostki połączonej relacją N:1 z tą jednostką lub jednostki dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Uruchom podrzędny przepływ pracy**|Umożliwia uruchomienie procesu przepływu pracy skonfigurowanego jako podrzędny przepływ pracy.|  
|**Zmień stan**|Umożliwia zmianę stanu rekordu, którego dotyczy proces, dowolnego rekordu połączonego z tym rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Zatrzymaj przepływ pracy**|Umożliwia zatrzymanie bieżącego przepływu pracy. Istnieje możliwość ustawienia stanu **Powodzenie** lub **Anulowano** i określenia komunikatu o stanie.<br /><br /> Jeśli dla zdarzenia skonfigurowano przepływy pracy w czasie rzeczywistym, zatrzymanie przepływu pracy ze stanem Anulowano uniemożliwi zakończenie akcji zdarzenia. Aby uzyskać więcej informacji, zobacz [Używanie przepływów pracy w czasie rzeczywistym](configure-workflow-steps.md#BKMK_SynchronousWorkflows).|  
|**Krok niestandardowy**|Deweloperzy mogą tworzyć niestandardowe kroki przepływu pracy, które definiują akcje. Domyślnie nie ma dostępnych kroków niestandardowych.|  
  
### <a name="setting-record-values"></a>Ustawianie wartości rekordu  

 Podczas tworzenia rekordu można ustawić dla niego wartości. W ramach aktualizowania rekordu można ustawić, dołączyć, zwiększyć, zmniejszyć, pomnożyć lub wyczyścić wartości.  
  
 Po wybraniu polecenia **Ustaw właściwości** zostanie otwarte okno dialogowe zawierające domyślny formularz dla jednostki.  
  
 W dolnej części okna dialogowego znajduje się lista dodatkowych pól, których nie ma na formularzu.  
  
 Dla dowolnego pola możesz określić wartość statyczną, która zostanie ustawiona przez przepływ pracy.  
  
 Po prawej stronie okna dialogowego znajduje się **Asystent formularzy**, który umożliwia ustawienie lub dołączenie wartości dynamicznych z kontekstu bieżącego rekordu. Obejmuje to wartości z powiązanych rekordów dostępnych za pomocą relacji N:1 (wiele do jednego) z jednostki.  
  
 Opcje dostępne w **Asystencie formularzy** zależą od pola wybranego w formularzu. Po ustawieniu wartości dynamicznej zostanie wyświetlony żółty symbol zastępczy (znany jako dynamiczne pole danych), który pokazuje miejsce dołączenia danych dynamicznych. Aby usunąć wartość, po prostu wybierz dynamiczne pole danych i usuń je. W przypadku pól tekstowych możesz użyć kombinacji danych statycznych i dynamicznych.  
  
 W przypadku wartości dynamicznych nie masz pewności, czy pole lub powiązana jednostka ma wartość, którą chcesz ustawić. Dlatego możesz określić pewną liczbę pól do wypróbowania na potrzeby ustawienia wartości i zdefiniować ich kolejność za pomocą zielonych strzałek. Jeśli pierwsze pole nie zawiera danych, zostanie wypróbowane drugie itd. Dla sytuacji, gdy żadne z pól nie zawiera danych, możesz określić wartość domyślną do użycia.  
  
<a name="BKMK_SettingConditionsForWorkflowActions"></a>   

## <a name="setting-conditions-for-workflow-actions"></a>Ustawianie warunków dla akcji przepływu pracy  

 Stosowane akcje często zależą od warunków. Procesy przepływu pracy udostępniają kilka metod ustawiania warunków i tworzenia logiki rozgałęziania w celu uzyskania pożądanych wyników. Istnieje możliwość sprawdzenia wartości rekordu, względem którego działa proces przepływu pracy, dowolnego rekordu połączonego relacją N:1 z tym rekordem lub wartości w ramach samego procesu.  
  
|Typ warunku|Opis|  
|--------------------|-----------------|  
|**Sprawdź warunek**|Instrukcja logiczna „if-\<warunek> then”.<br /><br /> Istnieje możliwość sprawdzenia bieżących wartości rekordu, którego dotyczy przepływ pracy, dowolnego rekordu połączonego z tym rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach. Na podstawie tych wartości możesz zdefiniować dodatkowe kroki wykonywane, jeśli warunek jest spełniony.<br /><br /> W instrukcji „if-\<warunek> then” możesz użyć następujących operatorów: **Równa się**, **Nie równa się**, **Zawiera dane**,  **Nie zawiera danych**, **Pod** i **Nie pod**. **Uwaga:** Operatory **Pod** i **Nie pod** to operatory hierarchiczne. Można ich użyć tylko dla jednostek ze zdefiniowaną relacją hierarchiczną. Jeśli spróbujesz użyć tych operatorów dla jednostek bez zdefiniowanej relacji hierarchicznej, zobaczysz komunikat o błędzie podobny do następującego: „Używasz operatora hierarchicznego dla jednostki bez zdefiniowanej relacji hierarchicznej. Ustaw jednostkę jako hierarchiczną (oznaczając relację jako hierarchiczną) lub użyj innego operatora.” Aby uzyskać więcej informacji na temat relacji hierarchicznych, zobacz [Definiowanie i odpytywanie danych powiązanych hierarchicznie](/powerapps/maker/common-data-service/define-query-hierarchical-data). Zrzut ekranu po tabeli przedstawia przykład definicji procesu przepływu pracy, która używa operatorów hierarchicznych **Pod** i **Nie pod**.|  
|**Odgałęzienie warunkowe**|Dla instrukcji logicznej „else-if-then” edytor używa tekstu „W przeciwnym przypadku if \<warunek> then:”<br /><br /> Wybierz zdefiniowany wcześniej warunek sprawdzenia, aby można było dodać odgałęzienie warunkowe w celu zdefiniowania dodatkowych kroków wykonywanych, jeśli warunek sprawdzenia nie jest spełniony.|  
|**Akcja domyślna**|Instrukcja logiczna „else”. Edytor używa tekstu „W przeciwnym razie:”<br /><br /> Wybierz zdefiniowany wcześniej warunek sprawdzenia, odgałęzienie warunkowe, warunek oczekiwania lub gałąź równoległego oczekiwania, aby można było użyć akcji domyślnej do zdefiniowania kroków dla wszystkich przypadków niespełniających kryteriów zdefiniowanych w warunku lub elementach gałęzi.|  
|**Warunek oczekiwania**|Umożliwia przepływowi pracy w tle samodzielne wstrzymanie się do momentu spełnienia kryteriów zdefiniowanych przez warunek. Przepływ pracy automatycznie uruchomi się ponownie po spełnieniu kryteriów warunku oczekiwania.<br /><br /> Przepływy pracy w czasie rzeczywistym nie mogą używać warunków oczekiwania.|  
|**Równoległa gałąź oczekiwania**|Umożliwia zdefiniowanie warunku oczekiwania dla przepływu pracy w tle przy użyciu odpowiadającego zestawu dodatkowych kroków wykonywanych tylko wtedy, gdy początkowe kryterium zostanie spełnione. Równoległych gałęzi oczekiwania możesz użyć do tworzenie limitów czasu w logice przepływu pracy. Umożliwiają one zapobieżenie nieskończonemu oczekiwaniu przez przepływ pracy na spełnienie kryteriów zdefiniowanych w warunku oczekiwania.|  
|**Krok niestandardowy**|Deweloperzy mogą tworzyć niestandardowe kroki przepływu pracy, które definiują warunki. Domyślnie nie ma dostępnych kroków niestandardowych.|  
  
 Następujący zrzut ekranu przedstawia przykład definicji procesu przepływu pracy, która używa operatorów hierarchicznych **Pod** i **Nie pod**. W tym przykładzie stosujemy dwa różne rabaty dla dwóch grup kont. W polu **Dodaj krok** wybraliśmy opcję **Sprawdź warunek**, aby określić warunek **if-then** zawierający operatory **Pod** lub **Nie pod**. Pierwszy warunek **if-then** dotyczy wszystkich kont **„pod”** kontem Alpine Ski House. Te konta otrzymują 10% rabatu na zakupione towary i usługi. Drugi warunek **if-then** dotyczy wszystkich kont **„ nie pod”** kontem Alpine Ski House. Otrzymują one 5% rabatu. Następnie wybraliśmy polecenie **Aktualizuj rekord**, aby zdefiniować akcję do wykonania na podstawie warunku.  
  
 ![Proces przepływu pracy z operatorami Pod i Nie pod](media/wfp-under-not-under.PNG "Proces przepływu pracy z operatorami Pod i Nie pod")  
  
<a name="BKMK_SynchronousWorkflows"></a>   

## <a name="using-real-time-workflows"></a>Używanie przepływów pracy w czasie rzeczywistym  

 Możesz konfigurować przepływy pracy w czasie rzeczywistym, lecz należy ich używać z rozwagą. Przepływy pracy w tle są zazwyczaj zalecane, ponieważ umożliwiają systemowi ich stosowanie w miarę dostępności zasobów na serwerze. Umożliwia to bardziej równomierną pracę serwera i ułatwia zachowanie optymalnej wydajności dla wszystkich użytkowników systemu. Wadą jest to, że akcje zdefiniowane przez przepływy pracy w tle nie są natychmiastowe. Nie można przewidzieć, kiedy zostaną one zastosowane, lecz zwykle trwa to kilka minut. W przypadku większości automatyzacji procesów biznesowych jest to wystarczające, ponieważ osoby używające systemu nie muszą być świadome, że proces działa.  
  
 Użyj przepływów pracy w czasie rzeczywistym, gdy proces biznesowy wymaga natychmiastowego przejrzenia wyników procesu przez użytkownika lub aby udostępnić możliwość anulowania operacji. Na przykład możesz ustawić pewne wartości domyślne dla rekordu przy jego pierwszym zapisywaniu lub chcesz zapewnić, że wybrane rekordy nie zostaną usunięte.  
  
### <a name="converting-between-real-time-and-background-workflows"></a>Konwertowanie między przepływami pracy w czasie rzeczywistym i w tle  

 Przepływ pracy w czasie rzeczywistym można przekształcić w przepływ pracy w tle, wybierając polecenie **Konwertuj na przepływ pracy w tle** na pasku narzędzi.  
  
 Przepływ pracy w tle można przekształcić w przepływ pracy w czasie rzeczywistym, wybierając polecenie **Konwertuj na przepływ pracy w czasie rzeczywistym** na pasku narzędzi. Jeśli przepływ pracy w tle używa warunków oczekiwania, stanie się on nieprawidłowy i nie będzie można go uaktywnić, dopóki warunek oczekiwania nie zostanie usunięty.  
  
### <a name="initiating-real-time-workflows-before-or-after-status-changes"></a>Inicjowanie przepływów pracy w czasie rzeczywistym przed zmianą stanu lub po niej  

 Po skonfigurowaniu **opcji procesów automatycznych** dla przepływów pracy w czasie rzeczywistym opcje **Uruchom, gdy** dla zdarzenia zmiany stanu umożliwiają wybranie pozycji **Po** lub **Przed** dla zmiany stanu. Opcja domyślna to **Po**.  
  
 Wybranie pozycji **Przed** oznacza, że logika przepływu pracy ma zostać zastosowana przed zapisaniem danych powodujących zmianę stanu. Umożliwia to sprawdzenie wartości przed zastosowaniem innej logiki po operacji i zapobieżenie wykonywaniu dalszej logiki. Na przykład dodatkowa logika może znajdować się we wtyczce lub niestandardowej akcji przepływu pracy, która może inicjować akcje w innym systemie. Zatrzymując dalsze przetwarzanie, można uniknąć przypadków wpływania na systemy zewnętrzne. Zastosowanie przepływów pracy w czasie rzeczywistym przed zdarzeniem oznacza także, że inne akcje przepływu pracy lub wtyczki nie muszą być wycofywane w przypadku anulowania operacji.  
  
### <a name="using-the-stop-workflow-action-with-real-time-workflows"></a>Używanie akcji Zatrzymaj przepływ pracy w przepływach pracy w czasie rzeczywistym  

 Po zastosowaniu akcji **Zatrzymaj przepływ pracy** w przepływie pracy jest dostępna opcja określenia warunku stanu: **Powodzenie** lub **Anulowano**. Jeśli stan zostanie ustawiony na Anulowano, zapobiegnie to wykonaniu operacji. Zostanie wyświetlony komunikat o błędzie z tekstem pochodzącym z komunikatu o stanie akcji wraz z nagłówkiem **Błąd procesu biznesowego**.  
  
## <a name="next-steps"></a>Następne kroki  
 [Tworzenie niestandardowej logiki biznesowej z użyciem procesów](guide-staff-through-common-tasks-processes.md)   
 [Omówienie procesów przepływu pracy](workflow-processes.md)   
 [Monitorowanie procesów przepływu pracy i zarządzanie nimi](monitor-manage-processes.md)   
 [Najlepsze rozwiązania dotyczące procesów przepływu pracy](best-practices-workflow-processes.md)
