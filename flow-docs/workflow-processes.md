---
title: Przepływy pracy klasycznej usługi Common Data Service (CDS) for Apps | MicrosoftDocs
ms.custom: ''
ms.date: 08/06/2018
ms.reviewer: matp
ms.service: flow
ms.topic: article
ms.assetid: 1f3c9780-26ad-49ec-a3fb-fc226def19c5
author: msftman
ms.author: deonhe
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 137cfd02ef3ba41cc9fffacc0aa23dc88e31fcef
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690979"
---
# <a name="classic-common-data-service-cds-for-apps-workflows"></a>Przepływy pracy klasycznej usługi Common Data Service (CDS) for Apps 

Przepływy pracy pozwalają automatyzować procesy biznesowe bez interfejsu użytkownika. Użytkownicy zwykle używają procesów przepływu pracy do inicjowania automatyzacji, które nie wymagają żadnych interakcji z użytkownikiem.  
  
 Każdy proces przepływu pracy jest skojarzony z pojedynczą jednostką. Podczas konfigurowania przepływów pracy należy uwzględnić cztery główne obszary:  
  
-   Kiedy mają być uruchamiane?  
  
-   Czy mają być uruchamiane jako przepływy pracy w czasie rzeczywistym, czy jako przepływy pracy w tle?  
  
-   Jakie akcje mają wykonywać?  
  
-   Jakie są warunki dla wykonywania akcji?  
  
 W tym temacie omówiono wstępnie wyszukiwanie procesów przepływu pracy, kiedy należy je uruchamiać oraz czy powinny być uruchamiane w czasie rzeczywistym, czy w tle. Aby uzyskać informacje na temat wykonywanych akcji i warunków, zobacz [Konfigurowanie procesów przepływu pracy](configure-workflow-steps.md).  
  
<a name="BKMK_WhereToCustomizeWorkflows"></a>   
## <a name="where-do-you-customize-workflow-processes"></a>Gdzie dostosowuje się procesy przepływu pracy?  
 Przepływy pracy w organizacji można zobaczyć, wyświetlając węzeł **Procesy** w polu **Rozwiązanie domyślne** i filtrując procesy, których właściwość **Kategoria** ma wartość **Przepływ pracy**.  
  
 ![Procesy filtrowane według przepływu pracy w usłudze Dynamics 365](media/workflow-processes-filtered.PNG "Procesy filtrowane według przepływu pracy w usłudze Dynamics 365")  
  
 W zależności od tego, jak aplikacja jest zbudowana, użytkownicy mogą tworzyć lub modyfikować swoje przepływy pracy w aplikacji. 
 
Deweloperzy mogą tworzyć przepływy pracy, korzystając z informacji w dokumencie [Dynamics 365 Customer Engagement Developer Guide (Przewodnik dewelopera platformy Dynamics 365 Customer Engagement)](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-guide), a kupowane rozwiązania mogą obejmować modyfikowalne przepływy pracy.  
  
<a name="BKMK_WorkflowProperties"></a>   
## <a name="workflow-properties"></a>Właściwości przepływu pracy  
 W Eksploratorze rozwiązań wybierz pozycję **Procesy** i kliknij pozycję **Nowy**.  
  
 Podczas tworzenia przepływu pracy w oknie dialogowym **Tworzenie procesu** będzie trzeba ustawić trzy właściwości, które dotyczą wszystkich procesów:  
  
 ![Tworzenie przepływu pracy w usłudze Dynamics 365](media/create-workflow.PNG "Tworzenie przepływu pracy w usłudze Dynamics 365")  
  
 **Nazwa procesu**  
 Nazwa procesu przepływu pracy nie musi być unikatowa, ale jeśli spodziewasz się wielu przepływów pracy, warto używać konwencji nazewnictwa, aby wyraźnie rozróżnić procesy. Dla nazw przepływów pracy można stosować standardowe prefiksy. Prefiks może opisywać funkcję przepływu pracy lub dział firmy. Pomoże to grupować podobne elementy na liście przepływów pracy.  
  
 **Kategoria**  
 Ta właściwość określa, że proces dotyczy przepływu pracy.  
  
 **Jednostka**  
 Każdy proces przepływu pracy musi być pojedynczą jednostką. Nie można zmienić jednostki po utworzeniu procesu przepływu pracy.  
  
 **Uruchom ten przepływ pracy w tle (zalecane)**  
 Ta opcja jest dostępna po wybraniu przepływu pracy jako kategorii. To ustawienie określa, czy przepływ pracy jest wykonywany w czasie rzeczywistym, czy w tle. Przepływy pracy w czasie rzeczywistym są uruchamiane natychmiast (synchronicznie), a przepływy pracy w tle są uruchamiane asynchronicznie. Dostępne opcje konfiguracji zależą od wyboru dla tego ustawienia. Przepływy pracy w tle umożliwiają stosowanie warunków oczekiwania, które nie są dostępne dla przepływów pracy w czasie rzeczywistym. Tak długo, jak warunki oczekiwania nie są używane, możesz później przekształcić przepływy pracy w tle na przepływy pracy w czasie rzeczywistym i odwrotnie. Aby uzyskać więcej informacji na temat warunków oczekiwania, zobacz [Ustawianie warunków dla akcji przepływu pracy](configure-workflow-steps.md#BKMK_SettingConditionsForWorkflowActions).  
  
 Jest także dostępna opcja **Typ** umożliwiająca określenie, czy nowy przepływ pracy będzie tworzony od zera, czy na podstawie istniejącego szablonu. Po wybraniu pozycji **Nowy proces z istniejącego szablonu (wybierz z listy)** możesz wybrać dostępne procesy przepływu pracy, które zostały wcześniej zapisane jako szablony procesu.  
  
 Po utworzeniu nowego lub zmodyfikowaniu istniejącego przepływu pracy będą dostępne następujące dodatkowe właściwości:  
  
 ![Karta Ogólne w przepływie pracy](media/create-workflow-general-tab.PNG "Karta Ogólne w przepływie pracy")  
  
 **Aktywuj jako**  
 Możesz wybrać pozycję **Szablon procesu**, aby utworzyć zaawansowany punkt początkowy dla innych szablonów. Jeśli wybierzesz tę opcję, po aktywowaniu przepływu pracy nie zostanie on zastosowany, lecz zamiast tego będzie dostępny do wybrania w oknie dialogowym **Tworzenie procesu** po wybraniu w polu **Typ**: wartości **Nowy proces z istniejącego szablonu (wybierz z listy)**  
  
 Szablony procesu są wygodne, jeśli istnieje wiele podobnych procesów przepływu pracy i chcesz je zdefiniować bez duplikowania logiki.  
  
> [!NOTE]
>  Zmodyfikowanie szablonu procesu nie powoduje zmiany zachowania żadnych procesów przepływu pracy utworzonych wcześniej na podstawie tego szablonu. Nowy przepływ pracy utworzony za pomocą szablonu jest kopią zawartości w szablonie.  
  
 **Dostępne do uruchomienia**  
 Ta sekcja zawiera opcje, które opisują, jak można uruchomić przepływ pracy.  
  
 **Uruchom ten przepływ pracy w tle (zalecane)**  
 To pole wyboru odzwierciedla opcję wybraną podczas tworzenia przepływu pracy. Ta opcja jest wyłączona, lecz można zmienić ją w menu **Akcje**, wybierając pozycję **Konwertuj na przepływ pracy w czasie rzeczywistym** lub **Konwertuj na przepływ pracy w tle**.  
  
 **Jako proces na żądanie**  
 Wybierz tę opcję, jeśli chcesz umożliwić użytkownikom uruchamianie tego przepływu pracy za pomocą polecenia **Uruchom przepływ pracy**.  
  
 **Jako proces podrzędny**  
 Wybierz tę opcję, jeśli chcesz umożliwić uruchamianie przepływu pracy z innego przepływu pracy.  
  
 **Przechowywanie zadań przepływu pracy**  
 Ta sekcja zawiera opcję usunięcia przepływu pracy po zakończeniu wykonywania przepływu pracy.  
  
 **Automatyczne usuwanie ukończonych zadań przepływu pracy (w celu zaoszczędzenia miejsca na dysku)**  
 Wybierz tę opcję, jeśli chcesz automatycznie usuwać zakończone przepływy pracy.  
  
> [!NOTE]
>  Zadania przepływu pracy nie są usuwane natychmiast po ich zakończeniu, lecz niedługo potem, za pomocą procesu wsadowego.  
  
 **Zakres**  
 W przypadku jednostek należących do użytkownika opcje to **Organizacja**, **Obiekt nadrzędny: podrzędne jednostki biznesowe**, **Jednostka biznesowa** lub **Użytkownik**. W przypadku jednostek należących do organizacji jedyna opcja to **Organizacja**.  
  
 Jeśli zakres to **Organizacja**, logikę przepływu pracy można zastosować dla dowolnego rekordu w organizacji. W przeciwnym przypadku przepływ pracy można zastosować tylko do podzbioru rekordów należących do zakresu.  
  
> [!NOTE]
>  Wartość domyślna zakresu to **Użytkownik**. Upewnij się, że wartość zakresu jest odpowiednia, przed aktywowaniem przepływu pracy.  
  
 **Uruchom, gdy**  
 Użyj opcji w tej sekcji, aby określić, kiedy przepływ pracy ma zostać uruchomiony automatycznie. Przepływ pracy w czasie rzeczywistym można skonfigurować pod kątem uruchamiania przed określonymi zdarzeniami. Jest to bardzo zaawansowana możliwość, ponieważ przepływ pracy może zatrzymać akcję, zanim ona nastąpi. Aby uzyskać więcej informacji, zobacz [Używanie przepływów pracy w czasie rzeczywistym](configure-workflow-steps.md#BKMK_SynchronousWorkflows). Dostępne opcje to:  
  
- **Utworzenie rekordu**  
  
- **Zmiana stanu rekordu**  
  
- **Przypisanie rekordu**  
  
- **Zmiana pól rekordu**  
  
- **Usunięcie rekordu**  
  
> [!NOTE]
>  Pamiętaj, że akcje i warunki zdefiniowane dla przepływu pracy nie rozpoznają momentu uruchomienia przepływu pracy. Na przykład jeśli zdefiniujesz przepływ pracy aktualizujący rekord, przepływ pracy w czasie rzeczywistym nie może wykonać tej akcji przed utworzeniem rekordu. Nie można zaktualizować rekordu, który nie istnieje. Podobnie przepływ pracy w tle nie może zaktualizować usuniętego rekordu, mimo że można zdefiniować tę akcję dla przepływu pracy. Jeśli dla przepływu pracy zostanie skonfigurowane wykonanie akcji, której nie można wykonać — akcja nie powiedzie się, tak samo jak cały przepływ pracy.  
  
 **Wykonaj jako**  
 Ta opcja jest dostępna tylko wtedy, gdy wybór opcji **Uruchom ten przepływ pracy w tle (zalecane)** zostanie anulowany podczas tworzenia przepływu pracy lub później w ramach konwersji przepływu pracy w tle na przepływ pracy w czasie rzeczywistym.  
  
<a name="BKMK_SecurityContextOfWorkflowProcesses"></a>   
## <a name="security-context-of-workflow-processes"></a>Kontekst zabezpieczeń procesów przepływu pracy  
 Gdy przepływ pracy w tle jest skonfigurowany jako proces na żądanie i uruchamiany przez użytkownika za pomocą polecenia **Uruchom przepływ pracy**, akcje, które przepływ pracy może wykonać, są ograniczone do akcji dostępnych dla użytkownika na podstawie jego uprawnień i poziomów dostępu zdefiniowanych przez role zabezpieczeń ustawione dla konta tego użytkownika.  
  
 Gdy przepływ pracy w tle zostanie uruchomiony na podstawie zdarzenia, przepływ pracy będzie działać w kontekście osoby, do której należy — zazwyczaj osoby, która utworzyła przepływ pracy.  
  
 W przypadku przepływów pracy w czasie rzeczywistym jest dostępna opcja **Wykonaj jako** i można wybrać, czy przepływ pracy ma zastosować kontekst zabezpieczeń właściciela przepływu pracy, czy użytkownika, który wprowadził zmiany w rekordzie. Jeśli przepływ pracy zawiera akcje, które nie wszyscy użytkownicy będą mogli wykonać z powodu ograniczeń zabezpieczeń, należy wybrać opcję uruchomienia przepływu pracy za pomocą właściciela przepływu pracy.  
  
<a name="BKMK_ActivatingWorkflows"></a>   
## <a name="activate-a-workflow"></a>Aktywowanie przepływu pracy  
 Przepływy pracy można edytować tylko wtedy, gdy są zdezaktywowane. Aby można było użyć przepływu pracy ręcznie lub zastosować go w związku ze zdarzeniem, musi być on aktywny. Aby można było aktywować przepływ pracy, musi on zawierać co najmniej jeden krok. Aby uzyskać informacje na temat konfigurowania kroków, zobacz [Konfigurowanie procesów przepływu pracy](configure-workflow-steps.md)  
  
 Przepływ pracy może aktywować lub dezaktywować tylko właściciel przepływu pracy lub osoba z uprawnieniem **Działanie w imieniu innego użytkownika**, taka jak administrator systemu.  Jest tak dlatego, że złośliwy użytkownik mógłby zmodyfikować przepływ pracy innego użytkownika, który nie byłby świadomy zmiany. Posiadany przepływ pracy można przypisać ponownie, zmieniając właściciela. To pole znajduje się na karcie **Administracja**. Jeśli nie jesteś administratorem systemu, a potrzebujesz zmodyfikować przepływ pracy należący do innego użytkownika, ten użytkownik musi zdezaktywować go i przypisać do Ciebie. Po zakończeniu edytowania przepływu pracy możesz przypisać go z powrotem do oryginalnego właściciela, aby ten mógł go aktywować.  
  
 Przepływy pracy w czasie rzeczywistym wymagają, aby użytkownik miał uprawnienie **Aktywowanie procesów w czasie rzeczywistym**. Ponieważ przepływy pracy w czasie rzeczywistym mogą z większym prawdopodobieństwem wpływać na wydajność systemu, to uprawnienie powinny mieć tylko osoby, które mogą ocenić potencjalne ryzyko.  
  
 Przepływy pracy są zapisywane przy aktywacji, więc zapisanie przepływu pracy przed aktywowaniem nie jest konieczne.  
  
## <a name="next-steps"></a>Następne kroki  
 [Konfigurowanie procesów przepływu pracy](configure-workflow-steps.md)  <br/>
[Dodawanie przepływu pracy na żądanie do przepływu procesów biznesowych](bpf-add-on-demand-workflow.md) 

