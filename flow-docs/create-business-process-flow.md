---
title: Tworzenie przepływu procesów biznesowych w usłudze PowerApps | Microsoft Docs
description: Informacje o sposobie tworzenia przepływu procesów biznesowych
ms.custom: ''
ms.date: 08/17/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: efe86ab3-430f-485a-b924-6ed82cfbb449
caps.latest.revision: 39
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: 258fedabea816b9a20a8f768632e797dec576365
ms.sourcegitcommit: d3243c9f82c5e058919c5cb85d36d45f1f034411
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2018
ms.locfileid: "43774236"
---
# <a name="tutorial-create-a-business-process-flow-to-standardize-processes"></a>Samouczek: tworzenie przepływu procesów biznesowych umożliwiającego standaryzowanie procesów

W tym samouczku przedstawiono sposób tworzenia przepływu procesów biznesowych za pomocą usługi PowerApps. Aby dowiedzieć się więcej na temat korzyści związanych z używaniem przepływów procesów biznesowych, zobacz [Business process flows overview (Omówienie przepływów procesów biznesowych)](business-process-flows-overview.md). Aby uzyskać informacje na temat tworzenia przepływu zadań dla urządzeń przenośnych, zobacz [Create a mobile task flow (Tworzenie przepływu zadań dla urządzeń przenośnych)](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-mobile-task-flow).  
  
 Po uruchomieniu przepływu procesów biznesowych etapy i kroki procesu są widoczne na pasku procesu w górnej części formularza:  
  
 ![Etapy procesu biznesowego](media/business-process-stages.png "Etapy procesu biznesowego")  
  
 > [!TIP]
 >  W utworzonej definicji przepływu procesów biznesowych możesz określić uprawnienia użytkowników do tworzenia, odczytu, aktualizacji lub usuwania wystąpienia przepływu procesów biznesowych. Na przykład w przypadku procesów związanych z usługami można przyznać pełny dostęp przedstawicielom działu obsługi klienta, którzy muszą zmieniać wystąpienie przepływu procesów biznesowych. Z kolei przedstawiciele handlowi mogą mieć dostęp tylko do odczytu, który umożliwia monitorowanie działań posprzedażnych. Aby ustawić zabezpieczenia w utworzonej definicji przepływu procesów biznesowych, wybierz pozycję **Włącz role zabezpieczeń** na pasku akcji.  
  
<a name="BKMK_Createbusinessprocessflows"></a>   
## <a name="create-a-business-process-flow"></a>Tworzenie przepływu procesów biznesowych  
  
1. Otwórz [eksploratora rozwiązań](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer).
  
2. W okienku nawigacji po lewej stronie wybierz pozycję **Procesy**. 
  
3.  Na pasku narzędzi **Akcje** wybierz pozycję **Nowa**.  
  
4.  W oknie dialogowym **Tworzenie procesu** wypełnij wymagane pola:  
  
    -   Wprowadź nazwę procesu. Nazwa procesu nie musi być unikatowa, ale powinna być zrozumiała dla osób, które muszą wybierać proces. Później można ją zmienić.  
  
    -   Na liście **Kategoria** wybierz pozycję **Przepływ procesów biznesowych**.  
  
         Nie można zmienić kategorii po utworzeniu procesu.  
  
    -   Na liście **Encja** wybierz encję, na której ma być oparty proces.  
  
         Wybrana encja ma wpływ na pola dostępne dla kroków, które można dodać do pierwszego etapu przepływu procesów. Jeśli nie możesz znaleźć odpowiedniej encji, upewnij się, że w jej definicji zaznaczono opcję przepływów procesów biznesowych (umożliwiającą tworzenie pól). Po zapisaniu procesu nie można zmienić tych ustawień.  
  
5. Wybierz przycisk **OK**.  
  
     Po utworzeniu nowego procesu zostanie otwarty projektant przepływu procesów biznesowych z utworzonym jednym etapem.  
  
 ![Okno przepływu procesów biznesowych z wyświetlonymi głównymi elementami](media/business-process-flow-window-showing-main-elements.png "Okno przepływu procesów biznesowych z wyświetlonymi głównymi elementami")  
  
6. **Dodaj etapy**. Jeśli użytkownicy będą przechodzić między etapami biznesowymi w procesie:  
  
    1.  Przeciągnij składnik **Etap** z karty **Składniki** na znak „+” w projektancie i upuść go.  
  
        ![Przeciąganie etapu procesu biznesowego](media/drag-business-process-stage.png "Przeciąganie etapu procesu biznesowego")  
  
    2.  Aby ustawić właściwości etapu, wybierz etap, a następnie wprowadź odpowiednie zmiany na karcie **Właściwości** po prawej stronie ekranu:  
  
        -   Podaj nazwę wyświetlaną.  
  
        -   W razie potrzeby wybierz kategorię etapu.  Kategoria (na przykład **Kwalifikowanie** lub **Programowanie**) jest wyświetlana na strzałce na pasku procesu.  
  
            ![Strzałka na pasku procesu biznesowego](media/business-process-bar-chevron.png "Strzałka na pasku procesu biznesowego")  
  
        -   Gdy skończysz zmieniać właściwości, wybierz przycisk **Zastosuj**.  
  
7. **Dodaj kroki do etapu**. Aby wyświetlić kroki etapu, wybierz pozycję **Szczegóły** w prawym dolnym rogu etapu. Aby dodać kolejne kroki:  
  
    1.  Przeciągnij składnik **Krok** z karty **Składniki** do etapu.  
  
        ![Dodawanie kroku do etapu w procesie biznesowym](media/add-step-stage-business-process.png "Dodawanie kroku do etapu w procesie biznesowym")  
  
    2.  Wybierz krok, a następnie ustaw właściwości na karcie **Właściwości**:  
  
        1.  Wprowadź nazwę wyświetlaną kroku.  
  
        2.  Jeśli chcesz, aby ukończenie kroku wymagało wprowadzenia danych przez użytkowników, wybierz odpowiednie pole z listy rozwijanej.  
  
        3.  Jeśli chcesz, aby przejście do kolejnego etapu procesu wymagało ukończenia danego kroku przez wypełnienie pola, wybierz pozycję **Wymagane**.  
  
        4.  Gdy skończysz, wybierz pozycję **Zastosuj**.  
  
8. **Dodaj gałąź (warunek) do procesu**. Aby dodać rozgałęzianie warunkowe:  
  
    1.  Przeciągnij składnik **Warunek** z karty **Składniki** na znak „+” widoczny między dwoma etapami.  
  
        ![Dodawanie warunku do przepływu procesów biznesowych](media/add-condition-business-process-flow.png "Dodawanie warunku do przepływu procesów biznesowych")  
  
    2.  Wybierz warunek, a następnie ustaw właściwości na karcie **Właściwości**. Aby uzyskać więcej informacji na temat właściwości rozgałęziania, zobacz [Enhance business process flows with branching (Rozszerzanie przepływów procesów biznesowych za pomocą rozgałęziania)](enhance-business-process-flows-branching.md). Gdy skończysz ustawiać właściwości warunku, wybierz przycisk **Zastosuj**.  
  
9. **Dodaj przepływ pracy**. Aby wywołać przepływ pracy:  
  
    1.  Przeciągnij składnik **Przepływ pracy** z karty **Składniki** na etap lub element **Globalny przepływ pracy** w projektancie.   Wybór obiektu docelowego zależy od przeznaczenia przepływu pracy:  
  
       - **Przeciągnij ten składnik na etap**, jeśli chcesz, aby przepływ pracy był wyzwalany na początku lub na końcu etapu. Składnik przepływu pracy musi być oparty na tej samej encji podstawowej co etap.  
  
       - **Przeciągnij ten składnik na element Globalny przepływ pracy**, jeśli chcesz, aby przepływ pracy był wyzwalany przy aktywowaniu lub archiwizowaniu procesu (gdy stan zmieni się na **Ukończone** lub **Porzucone**). Składnik przepływu pracy musi być oparty na tej samej encji podstawowej co proces.  
  
    2.  Wybierz przepływ pracy, a następnie ustaw właściwości na karcie **Właściwości**:  
  
       1.  Podaj nazwę wyświetlaną.  
  
       2.  Wskaż, kiedy powinno następować wyzwalanie przepływu pracy.  
  
       3.  Wyszukaj istniejący aktywny przepływ pracy na żądanie, który odpowiada encji etapu, lub utwórz nowy przepływ pracy, wybierając pozycję **Nowy**.  
  
       4.  Gdy skończysz, wybierz pozycję **Zastosuj**.  
  
       Aby uzyskać więcej informacji na temat przepływów pracy, zobacz [Workflow processes (Procesy przepływu pracy)](../common-data-service/workflow-processes.md).  
  
10. Aby zweryfikować przepływ procesów biznesowych, wybierz pozycję **Weryfikuj** na pasku akcji.  
  
11. Aby zapisać nieukończony proces jako wersję roboczą, wybierz pozycję **Zapisz** na pasku akcji.  
  
    > [!IMPORTANT]
    >  Pozostali użytkownicy nie mogą korzystać z wersji roboczej procesu.  
  
12. Aby aktywować proces i udostępnić go zespołowi, wybierz pozycję **Aktywuj** na pasku akcji.  

13. Aby określić uprawnienia użytkowników do tworzenia, odczytu, aktualizacji lub usuwania wystąpienia przepływu procesów biznesowych, wybierz pozycję **Edytuj role zabezpieczeń** na pasku poleceń projektanta. Na przykład w przypadku procesów związanych z usługami można przyznać pełny dostęp przedstawicielom działu obsługi klienta, którzy muszą zmieniać wystąpienie przepływu procesów biznesowych. Z kolei przedstawiciele handlowi mogą mieć dostęp tylko do odczytu, który umożliwia monitorowanie działań posprzedażnych.

  Na ekranie **Role zabezpieczeń** wybierz nazwę roli, aby otworzyć stronę z informacjami o roli zabezpieczeń. Wybierz kartę Przepływy procesów biznesowych, a następnie przyznaj roli zabezpieczeń odpowiednie uprawnienia do przepływu procesu biznesowego.

  > [!NOTE]
  > Domyślnie dostęp do nowych przepływów procesów biznesowych mają role zabezpieczeń administratora systemu i konfiguratora systemu.

   ![Przyznawanie uprawnień do przepływu procesów biznesowych](media/bpf-assign-privileges.png)

  Określ uprawnienia, wybierając odpowiednie przyciski radiowe, a następnie kliknij przycisk Zapisz. Aby uzyskać więcej informacji na temat uprawnień, zobacz [Business process flow privileges (Uprawnienia do przepływu procesów biznesowych)](business-process-flows-overview.md#BKMK_MultipleBPF).

  Ponadto nie zapomnij przypisać roli zabezpieczeń odpowiednim użytkownikom w organizacji.

> [!TIP] 
>  Oto garść porad, o których warto pamiętać podczas pracy nad przepływem zadań w oknie projektanta:  
>   
> - Aby zrobić migawkę wszystkich elementów widocznych w oknie przepływu procesów biznesowych, wybierz pozycję **Migawka** na pasku akcji. Jest to przydatne, jeśli na przykład chcesz uzyskać komentarze od członka zespołu dotyczące udostępnionego procesu.  
> - Minimapa umożliwia szybkie nawigowanie po różnych częściach procesu. Ułatwia to poruszanie się po skomplikowanych procesach, które nie mieszczą się na ekranie.  
> - Aby dodać opis procesu biznesowego, wybierz pozycję **Szczegóły** widoczną pod nazwą procesu w lewym rogu okna przepływu procesów biznesowych. Opis może zawierać maksymalnie 2000 znaków.  
  
<a name="BKMK_Editbusinessprocessflows"></a>   
## <a name="edit-a-business-process-flow"></a>Edytowanie przepływu procesów biznesowych  
 Aby edytować przepływy procesów biznesowych, otwórz eksploratora rozwiązań, wybierz pozycję **Procesy**, a następnie z listy procesów wybierz **przepływ procesów biznesowych**, który chcesz edytować.  
  
 Wybrany przepływ procesów biznesowych zostanie otwarty w projektancie, gdzie możesz wprowadzić dowolne zmiany. Po rozwinięciu sekcji **Szczegóły** widocznej pod nazwą procesu możesz zmienić jego nazwę, dodać opis oraz wyświetlić dodatkowe informacje.  
  
 ![Rozwinięta sekcja szczegółów przepływu procesów biznesowych](media/business-process-flow-details.png "Rozwinięta sekcja szczegółów przepływu procesów biznesowych")  
  
  
## <a name="other-things-to-know-about-business-process-flows"></a>Inne ważne kwestie dotyczące przepływów procesów biznesowych
 **Edytowanie etapów**  
Przepływy procesów biznesowych mogą zawierać maksymalnie 30 etapów.    
  
Można dodawać lub zmieniać następujące właściwości etapu:  
  
- **Nazwa etapu**  
  
- **Encja**. Encję można zmieniać dla dowolnego etapu z wyjątkiem pierwszego.  
  
- **Kategoria etapu**. Kategoria umożliwia pogrupowanie etapów według typu akcji. Jest to przydatne przy raportach grupujących rekordy według etapów. Opcje dla kategorii etapu pochodzą z globalnego zestawu opcji kategorii etapu. Do globalnego zestawu opcji możesz dodać kolejne opcje oraz w razie potrzeby zmienić etykiety istniejących opcji. Możesz również usunąć te opcje, ale zalecamy ich zachowanie. Po usunięciu danej opcji nie można dodać jej ponownie. Jeśli nie chcesz używać jakichś opcji, zmień ich etykiety na „Nie używać”.  
  
- **Relacja**. Jeśli poprzedni etap procesu jest oparty na innej encji, wprowadź relację. W aktualnie definiowanym etapie wybierz pozycję **Wybierz relacje**, aby określić relację, która ma być używana podczas przechodzenia między tymi dwoma etapami. Wybranie relacji zapewnia następujące korzyści:  
  
    -   Relacje często mają zdefiniowane mapy atrybutów, które automatycznie przenoszą dane między rekordami, co pozwala ograniczyć nakład pracy związany z wprowadzaniem danych.  
  
    -   Po wybraniu pozycji **Następny etap** na pasku procesu dla rekordu w przepływie procesów zostaną wyświetlone wszystkie rekordy, w których ta relacja jest używana. Ułatwia to ponowne użycie rekordów w procesie. Ponadto można zautomatyzować tworzenie rekordów za pomocą przepływów pracy, tak aby użytkownik po prostu wybierał taki przepływ, aby utworzyć nowy rekord. To również upraszcza cały proces.  
  
**Edytowanie kroków**  
 Każdy etap może zawierać maksymalnie 30 kroków.    
  
**Dodawanie gałęzi**  
Aby dowiedzieć się więcej o dodawaniu gałęzi do etapu, zobacz [Enhance business process flows with branching (Rozszerzanie przepływów procesów biznesowych za pomocą rozgałęziania)](enhance-business-process-flows-branching.md).  
  
Aby umożliwić innym użytkownikom używanie przepływu procesów biznesowych, musisz uporządkować przepływ procesów i aktywować go oraz włączyć role zabezpieczeń.  
  
**Ustawianie kolejności przepływu procesów**  
 Jeśli z encją (typem rekordu) jest skojarzony więcej niż jeden przepływ procesów biznesowych, musisz określić, który proces zostanie automatycznie przypisany do nowych rekordów. Na pasku poleceń wybierz pozycję **Określanie kolejności przepływu procesów**. W przypadku nowych rekordów lub rekordów, z którymi nie skojarzono przepływu procesów, zostanie użyty pierwszy przepływ procesów biznesowych dostępny dla użytkownika.  
  
**Włączanie ról zabezpieczeń**  
Dostęp użytkownika do przepływu procesów biznesowych zależy od uprawnienia do tego przepływu zdefiniowanego w roli zabezpieczeń przypisanej do tego użytkownika. 

Domyślnie tylko role zabezpieczeń **Administrator systemu** i **Konfigurator systemu** mogą wyświetlić nowy przepływ procesów biznesowych. 

Aby określić uprawnienia do przepływu procesów biznesowych, otwórz przepływ procesów biznesowych do edycji, a następnie wybierz pozycję **Edytuj role zabezpieczeń** na pasku poleceń projektanta przepływu procesów biznesowych. Zobacz krok 13 sekcji [Tworzenie przepływu procesów biznesowych](#create-a-business-process-flow) zawartej we wcześniejszej części tego tematu.
  
**Aktywowanie**  
Aby umożliwić innym osobom używanie przepływu procesów biznesowych, musisz go aktywować. Na pasku poleceń wybierz pozycję **Aktywuj**. Po potwierdzeniu aktywacji przepływ procesów biznesowych jest gotowy do użycia. Jeśli przepływ procesów biznesowych zawiera błędy, jego aktywowanie nie będzie możliwe do momentu usunięcia tych błędów.  

## <a name="add-an-on-demand-action-to-a-business-process-flow"></a>Dodawanie akcji na żądanie do przepływu procesów biznesowych
W usłudze Dynamics 365 (online) zaktualizowanej do wersji 9.0 wprowadzono nową funkcję przepływu procesów biznesowych — automatyzację przepływu procesów biznesowych za pomocą kroków akcji. Do przepływu procesów biznesowych można dodać przycisk umożliwiający wyzwolenie akcji lub przepływu pracy.

### <a name="add-on-demand-workflows-or-actions-using-an-action-step"></a>Dodawanie przepływów pracy lub akcji na żądanie przy użyciu kroku akcji
Załóżmy, że w ramach procesu kwalifikacji szans sprzedaży w firmie Contoso wszystkie szanse sprzedaży są sprawdzane przez wyznaczonego weryfikatora. Z tego względu w firmie Contoso utworzono akcję, która obejmuje następujące działania: 

- Tworzenie rekordu zadania przypisanego do weryfikatora szans sprzedaży. 
- Dołączanie tekstu „Gotowe do weryfikacji” do tematu szansy sprzedaży. 

Ponadto firma Contoso musi mieć możliwość uruchamiania tych akcji na żądanie. Aby zintegrować te zadania z procesem kwalifikacji szans sprzedaży, akcje muszą pojawić się w przepływie procesów biznesowych dotyczących szans sprzedaży. Aby włączyć tę funkcję, wybierz pozycję **Jako krok akcji przepływu procesów biznesowych**.
![Można uruchamiać jako przepływ procesów biznesowych](media/action-available-to-run.png).

Krok akcji jest dodawany do przepływu procesów biznesowych szans sprzedaży w firmie Contoso. Następnie przepływ procesów jest weryfikowany i aktualizowany.

![Akcja dodana do przepływu procesów biznesowych dotyczących szans sprzedaży.](media/add-action-to-bpf.png)

Teraz sprzedawcy w firmie Contoso mogą uruchomić tę akcję na żądanie w kroku procesu biznesowego **Kwalifikowanie szans sprzedaży**, wybierając pozycję **Wykonaj**.

![Wykonywanie akcji.](media/action-execute.png)

> [!IMPORTANT]
> - Aby można było wykonać akcję lub przepływ pracy na żądanie, przepływ procesów biznesowych musi zawierać krok akcji. Jeśli krok akcji uruchamia przepływ pracy, ten przepływ pracy musi być skonfigurowany do uruchamiania na żądanie.
> - Z akcją lub przepływem pracy musi być skojarzona ta sama encja, która jest powiązana z przepływem procesów biznesowych.

### <a name="limitation-of-using-action-steps-in-a-business-process-flow"></a>Ograniczenie dotyczące używania kroków akcji w przepływie procesów biznesowych

- Akcji nie można używać jako kroków akcji, jeśli typ parametrów wejściowych lub wyjściowych to Entity, EntityCollection bądź OptionSet (lista wyboru). Akcje, które zawierają więcej niż jeden parametr wyjściowy typu EntityReference lub dowolną liczbę parametrów wejściowych typu EntityReference, nie mogą być używane jako kroki akcji. Akcje, które nie są skojarzone z encją podstawową (akcją globalną), nie mogą być używane jako kroki akcji.

  
## <a name="next-steps"></a>Następne kroki  
 [Business process flows overview (Omówienie przepływów procesów biznesowych)](business-process-flows-overview.md) </br>   
 [Enhance business process flows with branching (Rozszerzanie przepływów procesów biznesowych za pomocą rozgałęziania)](enhance-business-process-flows-branching.md)

