---
title: Konfigurowanie akcji dla przepływów pracy w usłudze PowerApps | MicrosoftDocs
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
- PowerApps
author: Mattp123
ms.assetid: 6dbc0f10-7ac5-4685-ab74-22d24bf7102d
caps.latest.revision: 19
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 7bd236368e572c7204309094982b2868db0bce8f
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690694"
---
# <a name="configure-custom-actions-from-a-workflow"></a>Konfigurowanie akcji niestandardowych za pomocą przepływu pracy

Akcję niestandardową można włączyć z poziomu przepływu pracy bez pisania kodu. Więcej informacji: [Wywoływanie akcji niestandardowych z przepływu pracy](invoke-custom-actions-workflow-dialog.md).  
  
 Można również utworzyć akcję, aby deweloper mógł użyć jej w kodzie, albo edytować akcję, która została wcześniej zdefiniowana. Podobnie jak w przypadku procesów przepływu pracy należy rozważyć następujące kwestie:  
  
-   Co powinna robić akcja?  
  
-   Jakie są warunki wykonywania akcji?  
  
 
W przeciwieństwie do procesów przepływu pracy nie trzeba ustawiać następujących opcji:  
  
- **Uruchom, gdy**: akcje są uruchamiane, gdy kod wywołuje komunikat, który został dla nich wygenerowany.  
  
- **Zakres**: akcje są zawsze uruchamiane w kontekście użytkownika wywołującego.  
  
- **Uruchom w tle**: akcje są zawsze przepływami pracy w czasie rzeczywistym.  
  
Akcje mają również coś, czego pozbawione są procesy przepływu pracy — argumenty wejściowe i wyjściowe. Więcej informacji: [Definiowanie argumentów procesu](configure-actions.md#BKMK_DefineProcessArgs)  
  
<a name="create"></a>   
## <a name="create-an-action"></a>Tworzenie akcji  
  
> [!IMPORTANT]
>  Jeśli tworzysz akcję, która ma być częścią rozwiązania przeznaczonego do rozpowszechniania, utwórz ją w kontekście rozwiązania. Przejdź do obszaru **[Ustawienia](/powerapps/maker/model-driven-apps/advanced-navigation#settings)** > **Rozwiązania** i znajdź rozwiązanie niezarządzane, którego część będzie stanowić akcja. Następnie na pasku menu wybierz pozycję **Nowy** > **Proces**. Daje to pewność, że prefiks dostosowania skojarzony z nazwą akcji będzie zgodny z innymi składnikami rozwiązania. Po utworzeniu akcji nie można zmienić prefiksu.  
  
 Podobnie jak w przypadku procesów przepływu pracy, akcje mają następujące właściwości w oknie dialogowym **Tworzenie procesu**.  
  
 **Nazwa procesu**  
 Po wprowadzeniu nazwy procesu zostanie dla niego utworzona unikatowa nazwa przez usunięcie spacji lub znaków specjalnych z nazwy procesu.  
  
 **Kategoria**  
 Ta właściwość określa, że jest to proces akcji. Po zapisaniu procesu nie można zmienić tej właściwości.  
  
 **Jednostka**  
 W przypadku procesów akcji można wybrać jednostkę, aby zapewnić kontekst dla przepływu pracy, podobnie jak dla innych typów procesów ale dostępna jest również opcja **Brak (globalnie)**. Użyj tej opcji, jeśli akcja nie wymaga kontekstu określonej jednostki. Po zapisaniu procesu nie można zmienić tej właściwości.  
  
 **Typ**  
 Użyj tej właściwości, aby określić, czy utworzyć nową akcję od podstaw, czy też rozpocząć przy użyciu istniejącego szablonu.  
  
<a name="edit"></a>   
## <a name="edit-an-action"></a>Edytowanie akcji  
 Aby edytować procesy, należy je dezaktywować.  
  
 Można edytować akcję, która została utworzona jako część rozwiązania niezarządzanego lub dodana do rozwiązania zainstalowanego w organizacji. Jeśli rozwiązanie jest zarządzane, jego edytowanie może okazać się niemożliwe. Wydawca rozwiązania ma możliwość edycji zarządzanych właściwości, aby nie można było edytować akcji zainstalowanej z rozwiązaniem zarządzanym.  
  
 Podczas zapisywania akcji unikatowa nazwa jest generowana na podstawie nazwy procesu. Do tej unikatowej nazwy jest dodawany prefiks od wydawcy rozwiązania. Jest to nazwa komunikatu, którego deweloper będzie używać w kodzie.  
  
 Podczas edytowania akcji są dostępne następujące opcje:  
  
 **Nazwa procesu**  
 Po utworzeniu procesu i wygenerowaniu unikatowej nazwy na podstawie nazwy procesu można edytować nazwę procesu. Można zastosować konwencję nazewnictwa, aby ułatwić odnajdywanie określonych procesów.  
  
 **Unikatowa nazwa**  
 Podczas zapisywania akcji unikatowa nazwa jest generowana na podstawie nazwy procesu. Do tej unikatowej nazwy jest dodawany prefiks od wydawcy rozwiązania. Jest to nazwa komunikatu, którego deweloper będzie używać w kodzie. Nie zmieniaj tej unikatowej nazwy, jeśli proces został aktywowany i utworzono kod z założeniem możliwości wywołania akcji przy użyciu tej nazwy.  
  
> [!IMPORTANT]
>  Po uaktywnieniu akcji i napisaniu kodu z wykorzystaniem unikatowej nazwy nie należy zmieniać unikatowej nazwy bez zmiany kodu, który odwołuje się do niej.  
  
 **Włącz wycofanie**  
 Zwykle procesy obsługujące transakcje wycofają całą operację w przypadku niepowodzenia dowolnej części. Istnieją pewne wyjątki od tej reguły. Niektóre akcje dodane przez deweloperów w kodzie, które są inicjowane przez akcję, mogą nie obsługiwać transakcji. Jeśli na przykład kod wykonuje akcje w innych systemach, które wykraczają poza zakres transakcji. Nie mogą one zostać wycofane przez akcję uruchamianą w aplikacji. Niektóre komunikaty platformy nie obsługują transakcji. Jednak wszystkie akcje, które można wykonać przy użyciu interfejsu użytkownika akcji, będą obsługiwać transakcje. Wszystkie akcje, które są częścią przepływu pracy w czasie rzeczywistym są uwzględniane w transakcji, ale akcje umożliwiają rezygnację z uczestnictwa.  
  
 Należy skontaktować się z deweloperem, który będzie używać tego komunikatu, aby określić, czy musi być uwzględniany w transakcji czy nie. Ogólnie rzecz biorąc, akcja powinna być uwzględniona w transakcji, jeśli akcje wykonywane przez proces biznesowy nie mają sensu, jeśli któraś z nich nie zostanie ukończona pomyślnie. Klasycznym przykładem jest przenoszenie środków między dwoma kontami bankowymi. W przypadku wypłaty środków z jednego konta należy złożyć je na innym. Jeśli któraś z akcji nie powiedzie się, obie muszą zakończyć się niepowodzeniem.  
  
> [!NOTE]
>  Nie można włączyć wycofywania, jeśli akcja niestandardowa jest wywoływana bezpośrednio z poziomu przepływu pracy. Można włączyć wycofywanie, jeśli akcja jest wyzwalana przez komunikat usług internetowych PowerApps.  
  
 **Aktywuj jako**  
 Podobnie jak wszystkie procesy, możesz aktywować proces jako szablon i używać go jako zaawansowanego punktu początkowego dla procesów, do których stosowany jest podobny wzorzec.  
  
 **Definiowanie argumentów procesu**  
 W tym obszarze określisz dane oczekiwane przez akcję w celu uruchomienia oraz przekazywane dane wyjściowe akcji. Więcej informacji: [Definiowanie argumentów procesu](configure-actions.md#BKMK_DefineProcessArgs)  
  
 **Dodawanie etapów, warunków i akcji**  
 Podobnie jak dla innych procesów, określ akcje do wykonania i czas ich wykonywania. Więcej informacji: [Dodawanie etapów, warunków i akcji](configure-actions.md#BKMK_AddStagesConditionsAndActions)

<a name="BKMK_DefineProcessArgs"></a>   
### <a name="define-process-arguments"></a>Definiowanie argumentów procesu  
 Gdy deweloper używa komunikatu, może rozpocząć od określonych danych, które można przekazać do komunikatu. Aby na przykład utworzyć nowy rekord przypadku, może istnieć wartość tytułu przypadku, która jest przekazywana jako argument wejściowy.  
  
 Po zakończeniu komunikatu może być konieczne przekazanie danych, które uległy zmianie lub zostały wygenerowane przez komunikat, do innej operacji w kodzie dewelopera. Te dane są argumentem wyjściowym.  
  
 Zarówno argumenty wejściowe, jak i wyjściowe, muszą mieć nazwę, typ oraz informację, czy argument jest zawsze wymagany. Można również wprowadzić opis.  
  
 Nazwa komunikatu i informacje o wszystkich argumentach procesu stanowią „podpis” komunikatu. Po uaktywnieniu akcji i użyciu jej w kodzie nie można zmieniać podpisu. W przypadku zmiany tego podpisu kod, którzy korzysta z komunikatu, nie powiedzie się. Jedynym wyjątkiem od tej reguły jest zmiana jednego z parametrów, aby nie był zawsze wymagany.  
  
 Można zmieniać kolejność argumentów, sortując je lub przenosząc je w górę lub w dół, ponieważ argumenty są identyfikowane na podstawie nazwy, a nie kolejności. Ponadto zmiana opisu nie spowoduje przerwania działania kodu korzystającego z komunikatu.  
  
#### <a name="action-process-argument-types"></a>Typy argumentów procesu akcji  
 W poniższej tabeli opisano typy argumentów procesu akcji.  
  
|Typ|Opis|  
|----------|-----------------|  
|Wartość logiczna|Wartość `true` lub `false`.|  
|Data/godzina|Wartość, która przechowuje informacje o dacie i godzinie.|  
|Dziesiętna|Wartość liczbowa z precyzją dziesiętną. Używana, gdy dokładność jest niezwykle ważna.|  
|Jednostka|Rekord dla określonej jednostki. Po wybraniu jednostki zostaje włączona lista rozwijana umożliwiająca wybór typu jednostki.|  
|Kolekcja jednostek|Kolekcja rekordów jednostki.|  
|Odwołanie do jednostki|Obiekt, który zawiera nazwę, identyfikator i typ rekordu jednostki, który jednoznacznie go identyfikuje. Po wybraniu odwołania zostaje włączona lista rozwijana umożliwiająca wybór typu jednostki.|  
|Liczba zmiennoprzecinkowa|Wartość liczbowa z precyzją dziesiętną. Używane, gdy dane pochodzą z pomiaru, który nie jest całkowicie dokładny.|  
|Liczba całkowita|Liczba całkowita.|  
|Pieniądze|Wartość, w której są przechowywane dane o ilości pieniędzy.|  
|Lista wyboru|Wartość, która reprezentuje opcję dla atrybutu OptionSet.|  
|Ciąg|Wartość tekstowa.|  
  
> [!NOTE]
> Wartości argumentu **EntityCollection** nie można ustawić w interfejsie użytkownika dla warunków lub akcji. Są one udostępniane do użycia przez deweloperów w kodzie niestandardowym. Więcej informacji: [Create your own actions (Tworzenie własnych akcji)](https://docs.microsoft.com/dynamics365/customer-engagement/developer/create-own-actions) 
  
<a name="BKMK_AddStagesConditionsAndActions"></a>   
### <a name="add-stages-and-steps"></a>Dodawanie etapów i kroków  
 Akcje są typem procesu bardzo podobnym do przepływów pracy w czasie rzeczywistym. Wszystkie kroki, które mogą być używane w przepływach pracy w czasie rzeczywistym, mogą być używane w akcji. Aby uzyskać informacje na temat kroków, które można zastosować w przypadku przepływów pracy czasu rzeczywistego i akcji, zobacz temat [Workflow stages and steps (Etapy i kroki przepływu pracy)](configure-workflow-steps.md).  
  
 Oprócz kroków wymaganych w przepływach pracy czasu rzeczywistego, akcje mają również krok **Przypisywanie wartości**.  W akcji można go użyć tylko do ustawiania argumentów wyjściowych. Można użyć asystenta formularza, aby ustawić wszystkie argumenty wyjściowe na określone wartości lub bardziej konkretnie, wartości z rekordu, dla którego jest uruchomiona akcja, rekordy związane z tym rekordem mające relację wiele do jednego, rekordy utworzone w poprzednim kroku oraz wartości będące częścią procesu.  
  
## <a name="next-steps"></a>Następne kroki  
 [Akcje](actions.md)  

 [Wywoływanie akcji niestandardowych z przepływu pracy](invoke-custom-actions-workflow-dialog.md)   
 [Monitorowanie akcji i przepływów pracy w czasie rzeczywistym](monitor-manage-processes.md#BKMK_MonitorSyncWorkflows)
 
 
