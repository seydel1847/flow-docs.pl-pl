---
title: Omówienie przepływów procesów biznesowych | MicrosoftDocs
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
ms.assetid: 4469877e-bb95-481a-bc52-c9746f937ce5
caps.latest.revision: 16
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: baefae21e605b0e54e32b09dfaee8f2980d73c13
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690324"
---
# <a name="business-process-flows-overview"></a>Omówienie przepływów procesów biznesowych

Możesz pomóc w zapewnieniu, że ludzie wprowadzają dane spójnie i wykonują te same kroki za każdym razem, gdy pracują z klientem, tworząc przepływ procesów biznesowych. Na przykład możesz utworzyć przepływ procesów biznesowych, aby wszyscy obsługiwali żądania obsługi klientów w ten sam sposób lub aby wymagać uzyskania zatwierdzenia faktury przed przesłaniem zamówienia. Przepływy procesów biznesowych używają tej samej podstawowej technologii co inne procesy, ale zapewniane możliwości różnią się od innych funkcji korzystających z procesów. Aby dowiedzieć się więcej o tworzeniu lub edytowaniu przepływu procesów biznesowych, zobacz [Tworzenie przepływu procesów biznesowych](create-business-process-flow.md).  
  
 [Obejrzyj krótkie wideo (4:49) dotyczące przepływów procesów biznesowych.](https://go.microsoft.com/fwlink/p/?linkid=842226)  
  
<a name="BKMK_Why"></a>   
## <a name="why-use-business-process-flows"></a>Dlaczego warto używać przepływów procesów biznesowych?  
Przepływy procesów biznesowych przekazują pracownikom wytyczne dotyczące sposobu wykonywania pracy. Zapewniają one uproszczone środowisko użytkownika, które kieruje ludzi przez procesy zdefiniowane w organizacji, obejmujące interakcje wymagane do przeprowadzenia w celu osiągnięcia pewnego rodzaju konkluzji. To środowisko użytkownika można dostosować, aby zapewnić osobom o różnych rolach zabezpieczeń środowisko dopasowane do wykonywanych zadań.  
  
 Użyj przepływów procesów biznesowych, aby zdefiniować zestaw kroków, które osoby muszą wykonać, aby uzyskać żądany rezultat. Te kroki zapewniają wizualny wskaźnik, który informuje ludzi o tym, gdzie znajdują się w procesie biznesowym. Przepływy procesów biznesowych redukują potrzebę szkolenia, ponieważ nowi użytkownicy nie muszą skupiać się na tym, jakiej jednostki powinni używać. Mogą polegać na wskazówkach zapewnianych przez proces. Możesz skonfigurować przepływy procesów biznesowych, aby obsługiwać typowe metodologie sprzedażowe, które pomagają grupom sprzedażowym w osiąganiu lepszych wyników. W przypadku grup obsługowych przepływy procesów biznesowych mogą pomóc nowym pracownikom w szybszym wdrożeniu i unikaniu błędów, które mogą powodować spadek zadowolenia klientów.  
  
<a name="BKMK_What"></a>   
## <a name="what-can-business-process-flows-do"></a>Co mogą zrobić przepływy procesów biznesowych?  
 Przy użyciu przepływów procesów biznesowych możesz określić zestaw *etapów* i *kroków*, które następnie są wyświetlane w kontrolce w górnej części formularza.  
  
 ![Etapy procesu biznesowego](media/business-process-stages.png "Etapy procesu biznesowego")  
  
 Każdy etap zawiera grupę kroków. Każdy krok reprezentuje pole, w którym można wprowadzić dane. Ludzie przechodzą do następnego etapu, korzystając z przycisku **Następny etap**. Możesz ustawić krok jako wymagany. Dzięki temu ludzie będą musieli wprowadzić dane w odpowiednim polu, zanim będą w stanie przejść do kolejnego etapu. Takie rozwiązanie często jest zwane „kontrolą etapową”.  
  
 Przepływy procesów biznesowych wydają się być względnie proste w porównaniu do innych typów procesów, ponieważ nie zapewniają żadnej warunkowej logiki biznesowej ani automatyzacji, poza usprawnionym środowiskiem wprowadzania danych i kontrolowania wpisów w rozbiciu na etapy. Jednak w przypadku połączenia ich z innymi procesami i formami dostosowywania mogą odegrać ważną rolę w oszczędzaniu czasu ludzi, redukowaniu kosztów szkoleń oraz zwiększaniu rozpowszechnienia wśród użytkowników.  

<a name="BKMK_BPFwithOtherCustomizations"></a>   
### <a name="business-process-flows-integrated-with-other-customizations"></a>Przepływy procesów biznesowych zintegrowane z innymi formami dostosowywania  
 Gdy użytkownik wprowadza dane przy użyciu przepływów procesów biznesowych, zmiany w danych są również stosowane wobec pól formularza. Dzięki temu wszelkie automatyzacje zapewniane przez reguły biznesowe lub skrypty formularzy mogą być stosowane natychmiast. Można dodać kroki ustawiające wartości dla pól, które nie są obecne w formularzu, a te pola zostaną dodane do modelu obiektów `Xrm.Page` używanego w przypadku skryptów formularza. Wszelkie przepływy pracy inicjowane przez zmiany wprowadzane w polach zawarte w przepływie procesów biznesowych zostaną zastosowane w momencie zapisana danych w formularzu. Jeśli automatyzacja zostanie zastosowana przez przepływ pracy w czasie rzeczywistym, zmiany będą natychmiast widoczne dla użytkownika, gdy dane w formularzu zostaną odświeżone po zapisaniu rekordu.  
  
 Chociaż kontrolka przepływu procesów biznesowych w formularzu nie zapewnia żadnej możliwości programowania po stronie klienta, zmiany zastosowane przez reguły biznesowe lub skrypty formularza będą automatycznie stosowane do kontrolek przepływów procesów biznesowych. Jeśli ukryjesz pole w formularzu, to pole również zostanie ukryte w kontrolce przepływu procesów biznesowych. Jeśli ustawisz wartość przy użyciu reguł biznesowych lub skryptów formularza, ta wartość zostanie ustawiona w przepływie procesów biznesowych.  
  
### <a name="concurrent-process-flows"></a>Współbieżne przepływy procesów  
 Współbieżne przepływy procesów biznesowych umożliwiają skonfigurowanie wielu procesów biznesowych i skojarzenie ich z tym samym rekordem początkowym. Użytkownicy mogą przełączać się pomiędzy wieloma procesami biznesowymi uruchomionymi jednocześnie, a także wznawiać pracę na danym etapie w procesie.  
  
<a name="BKMK_SystemBPF"></a>   
### <a name="system-business-process-flows"></a>Systemowe przepływy procesów biznesowych  
 Uwzględniono następujące przepływy procesów biznesowych. Aby dowiedzieć się, jak działają przepływy procesów biznesowych, przejrzyj te systemowe przepływy procesy biznesowe:  
  
-   Proces Od potencjalnego klienta do szansy sprzedaży  
  
-   Proces Szansa sprzedaży  
  
-   Proces Od telefonu do sprawy  
  
<a name="BKMK_multipleEntities"></a>   
## <a name="multiple-entities-in-business-process-flows"></a>Wiele jednostek w przepływach procesów biznesowych  
 Możesz użyć przepływu procesów biznesowych dla jednej jednostki lub wielu jednostek. Przykładowo możesz mieć proces, który rozpoczyna się szansą sprzedaży, przechodzi do oferty, zamówienia, a następnie faktury, aby zakończyć się zamknięciem szansy sprzedaży.  
  
 Możesz zaprojektować przepływy procesów biznesowych, które integrują ze sobą rekordy nawet pięciu różnych jednostek w jednym procesie. Dzięki temu ludzie pracujący z aplikacją mogą skupić się na przepływie swojego procesu, a nie jednostki, w której pracują. Użytkownicy mogą łatwiej przechodzić pomiędzy powiązanymi rekordami jednostki.  
  
<a name="BKMK_MultipleBPF"></a>   
## <a name="multiple-business-process-flows-are-available-per-entity"></a>Dla danej jednostki dostępnych jest wiele przepływów procesów biznesowych  
 Nie wszyscy użytkownicy w organizacji mogą przechodzić ten sam proces. Ponadto różne warunki mogą wymagać zastosowania różnych procesów. Możesz mieć do 10 aktywnych przepływów procesów biznesowych na jednostkę, aby zapewniać odpowiednie procesy dostosowane do różnych sytuacji.  
  
<a name="BPF_controlsWhichBPF"></a>   
### <a name="control-which-business-process-flow-will-be-applied"></a>Kontrolowanie stosowanego przepływu procesów biznesowych  
 Istnieje możliwość kojarzenia przepływów procesów biznesowych z rolami zabezpieczeń, aby tylko osoby z tymi rolami zabezpieczeń mogły je wyświetlać i ich używać. Można również ustawić kolejność przepływów procesów biznesowych, aby kontrolować, który przepływ procesów biznesowych zostanie ustawiony domyślnie. Działa to w taki sam sposób, jak definiowanie wielu formularzy dla jednostki.  
  
 Gdy ktoś utworzy nowy rekord jednostki, lista dostępnych aktywnych definicji procesów biznesowych zostanie odfiltrowana według roli zabezpieczeń użytkownika. Pierwsza aktywna definicja procesu biznesowego dostępna dla roli zabezpieczeń użytkownika zgodnie z listą kolejności procesów to definicja stosowana domyślnie. Jeśli dostępnych jest więcej aktywnych definicji procesów biznesowych, użytkownicy mogą załadować inną definicję z poziomu okna dialogowego Przełącz proces. Za każdym razem, gdy procesy zostaną przełączone, proces obecnie renderowany zostanie przeniesiony do tła i zastąpiony wybranym procesem, ale zachowa swój stan i może być ponownie przełączony. Każdy rekord może mieć skojarzonych wiele wystąpień procesów (każdy dla innej definicji przepływu procesów biznesowych, maksymalnie 10). Podczas ładowania formularza renderowany jest tylko jeden przepływ procesów biznesowych. Kiedy dowolny użytkownik zastosuje inny proces, ten proces może być ładowany domyślnie tylko dla tego konkretnego użytkownika.  
  
 Aby upewnić się, że proces biznesowy jest ładowany domyślnie dla wszystkich użytkowników (zachowanie odpowiadające procesowi „przypinania”), można dodać niestandardowy skrypt interfejsu API klienta (zasób internetowy) dla ładowania formularza, który będzie ładować istniejące wystąpienie procesu biznesowego w oparciu o identyfikator definicji procesu biznesowego. 
 
  
<a name="BKMK_Considerations"></a>   
## <a name="business-process-flow-considerations"></a>Zagadnienia dotyczące przepływu procesów biznesowych  
 Przepływy procesów biznesowych możesz zdefiniować tylko dla jednostek, które je obsługują. Należy również pamiętać o limitach dotyczących liczby możliwych do dodania procesów, etapów i kroków.  
  
### <a name="business-process-flows-that-call-a-workflow"></a>Przepływy procesów biznesowych, które wywołują przepływ pracy  
 Istnieje możliwość wywołania przepływów pracy na żądanie z poziomu przepływu procesów biznesowych. Możesz skonfigurować tę opcję w projektancie przepływu procesów biznesowych, przeciągając składnik przepływu pracy do etapu procesu lub sekcji globalnych przepływów pracy. Aby uzyskać więcej informacji o używaniu przepływów pracy w przepływach procesów biznesowych, zobacz [Blog: Business process flow automation in Dynamics 365 (Automatyzacja przepływu procesów biznesowych w usłudze Dynamics 365)](https://blogs.msdn.microsoft.com/crm/2017/03/28/business-process-flow-automation-in-dynamics-365/).  
  
 Jeżeli uwzględnisz przepływ pracy, który chcesz wyzwolić w przypadku zakończenia etapu w przepływie procesów biznesowych, a ten etap jest ostatnim etapem w przepływie, projektant sprawia wrażenie, że przepływ pracy zostanie wyzwolony w przypadku zakończenia etapu. Jednak przepływ pracy nie zostanie wyzwolony, ponieważ nie dochodzi do przejścia pomiędzy etapami. Użytkownik nie zobaczy ostrzeżenia ani błędu, który uniemożliwiałby dodanie przepływu pracy na tym etapie. Gdy użytkownik wejdzie w interakcję z przepływem procesów biznesowych, zakończenie lub porzucenie procesu nie będzie skutkować przejściem etapu, a więc przepływ pracy nie zostanie wyzwolony. Weź pod uwagę następujące przykłady:  
  
-   Tworzysz przepływ procesów biznesowych z dwoma etapami, etap S1 łączy się z etapem S2, przepływ pracy znajduje się na etapie S2 oraz wyzwalacz jest ustawiony na **zakończenie etapu**.  
  
-   Tworzysz przepływ procesów biznesowych z trzema etapami, etap S1 łączy się z etapem S2, a następnie etap S2 rozgałęzia się do etapu S3. Uwzględniasz przepływ pracy na etapie S2 i ustawiasz wyzwalacz na **zakończenie etapu**.  
  
 W obu przypadkach przepływ pracy nie będzie wyzwalany. Aby obejść ten problem, możesz dodać globalny przepływ pracy i dodać do niego przepływ pracy, który chcesz wyzwolić, aby był on wyzwalany dla procesu biznesowego, a nie etapu procesu. Możesz ustawić wyzwalacz dla globalnego przepływu pracy na porzucenie procesu lub ukończenie procesu, aby wyzwolić przepływ pracy, gdy użytkownik porzuci lub ukończy proces biznesowy.  
  
<a name="BKMK_Entities"></a>   
### <a name="entities-that-can-use-business-process-flows"></a>Jednostki, które mogą używać przepływów procesów biznesowych  
 Wszystkie jednostki niestandardowe mogą używać przepływów procesów biznesowych. Następujące jednostki standardowe również mogą używać przepływów procesów biznesowych:  
  
-   Konto  
-   Termin  
-   Kampania  
-   Działanie w ramach kampanii  
-   Odpowiedź w ramach kampanii  
-   Konkurent  
-   Kontakt  
-   Adres e-mail  
-   Uprawnienie  
-   Faks  
-   Przypadek  
-   Faktura  
-   Potencjalny klient  
-   List  
-   Lista marketingowa  
-   Szansa sprzedaży  
-   Połączenie telefoniczne  
-   Produkt  
-   Element cennika  
-   Oferta  
-   Termin cykliczny  
-   Materiały sprzedażowe  
-   Działanie społecznościowe  
-   Zamówienie  
-   Użytkownik  
-   Zadanie  
-   Zespół  
  
 Aby włączyć jednostkę niestandardową do przepływów procesów biznesowych, zaznacz pole wyboru **Przepływy procesów biznesowych (pola zostaną utworzone)** w definicji jednostki. Należy pamiętać, że nie można cofnąć tej akcji.  
  
> [!NOTE]
>  Jeśli przejdziesz do etapu przepływu procesów biznesowych, który zawiera jednostkę `Social Activity`, i wybierzesz przycisk **Następny etap**, zobaczysz opcję **Utwórz**. Po wybraniu opcji **Utwórz** zostanie załadowany formularz **Działanie społecznościowe**. Jednak ponieważ jednostka `Social Activity` nie jest prawidłowa dla opcji `Create` z poziomu interfejsu użytkownika aplikacji, nie będziesz w stanie zapisać formularza i zobaczysz komunikat o błędzie: „Nieoczekiwany błąd”.  
  
<a name="BPF_MaxNumbers"></a>   
### <a name="maximum-number-of-processes-stages-and-steps"></a>Maksymalna liczba procesów, etapów i kroków  
 Aby zapewnić akceptowalną wydajność i użyteczność interfejsu użytkownika, istnieją pewne ograniczenia, o których należy pamiętać podczas planowania użycia przepływów procesów biznesowych:  
  
-   Może istnieć maksymalnie 10 aktywowanych procesów przepływów procesów biznesowych na jednostkę.  
  
-   Każdy proces może zawierać maksymalnie 30 etapów.  
  
-   Procesy obejmujące wiele jednostek mogą zawierać maksymalnie pięć jednostek.
  
## <a name="business-process-flow-entity-customization-support"></a>Obsługa dostosowywania jednostki przepływu procesów biznesowych 

Począwszy od aktualizacji wersji 9.0 usługi Dynamics 365 (online), jednostki przepływu procesów biznesowych mogą pojawiać się w systemie, dzięki czemu można udostępniać dane rekordu jednostki w siatkach, widokach, wykresach i pulpitach nawigacyjnych. 

### <a name="use-business-process-flow-entity-records-with-grids-views-charts-and-dashboards"></a>Użycie rekordów jednostek przepływu procesów biznesowych w siatkach, widokach, wykresach i pulpitach nawigacyjnych

W przypadku przepływów procesów biznesowych dostępnych w formie jednostek możesz teraz używać zaawansowanego wyszukiwania, wykresów i pulpitów nawigacyjnych pozyskanych z danych przepływu procesów biznesowych dla danej jednostki, np. potencjalnego klienta lub szansy sprzedaży. Administratorzy systemu i osoby odpowiedzialne za dostosowywanie mogą tworzyć niestandardowe siatki, widoki, wykresy i pulpity nawigacyjne przepływu procesów biznesowych podobne do tych utworzonych za pomocą dowolnej innej jednostki.

Przepływy procesów biznesowych, takie jak **Proces Od potencjalnego klienta do szansy sprzedaży**, są wyświetlane jako jednostki z możliwością dostosowania w Eksploratorze rozwiązań.

![Eksplorator rozwiązań z jednostką procesu Od potencjalnego klienta do szansy sprzedaży](media/bpf-lead-solution-explorer.png)

Aby uzyskać dostęp do domyślnego widoku przepływu procesów biznesowych, otwórz eksplorator rozwiązań, rozwiń pozycję **Jednostki** > rozwiń żądany proces, np. **Proces Od potencjalnego klienta do szansy sprzedaży**, wybierz opcję **Widoki**, a następnie wybierz żądany widok.

Dostępnych jest kilka widoków domyślnych, które możesz wyświetlić jako wykres, np. widok **Proces Aktywna szansa sprzedaży**. 

![Widok procesu Aktywna szansa sprzedaży](media/bpf-default-view.png)

### <a name="interact-with-the-business-process-flow-entity-from-a-workflow"></a>Interakcja z jednostką przepływu procesów biznesowych z poziomu przepływu pracy
Istnieje też możliwość wejścia w interakcję z jednostką przepływu procesów biznesowych z poziomu przepływu pracy. Na przykład możesz utworzyć przepływ pracy z rekordu jednostki przepływu procesów biznesowych, aby zmienić aktywny etap, gdy zostanie zaktualizowane pole w rekordzie jednostki Szansa sprzedaży. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Automatyzacja etapów przepływu procesów biznesowych przy użyciu przepływów pracy](https://blogs.msdn.microsoft.com/crminthefield/2017/12/18/automate-business-process-flow-stages-using-workflows).


### <a name="limitations-of-using-business-process-flow-entities"></a>Ograniczenia dotyczące korzystania z jednostki przepływów procesów biznesowych

- Obecnie nie można tworzyć formularzy niestandardowych dla jednostek opartych na przepływie procesów biznesowych.
- Jeśli rozwiązanie obejmuje jednostkę przepływu procesów biznesowych, to jednostkę tę należy ręcznie dodać do rozwiązania przed jego wyeksportowaniem. W przeciwnym razie jednostka przepływu procesów biznesowych nie będzie uwzględniona w pakiecie rozwiązania. Więcej informacji: [Dodawanie składników rozwiązania](/powerapps/maker/model-driven-apps/create-solution#add-solution-components)

### <a name="next-steps"></a>Następne kroki  
 [Obejrzyj krótkie wideo (4:49) dotyczące przepływów procesów biznesowych](https://go.microsoft.com/fwlink/p/?linkid=842226)   
 [Tworzenie przepływu procesów biznesowych](create-business-process-flow.md)   
 [Rozszerzanie przepływów procesów biznesowych za pomocą rozgałęziania](enhance-business-process-flows-branching.md) <br/>
 [Oficjalny dokument: Włączanie procesu za pomocą usługi Dynamics 365](http://download.microsoft.com/download/C/3/B/C3B46E35-9445-43B9-800B-474E022EE352/Process%20Enablement%20with%20Microsoft%20Dynamics%20CRM%202013.pdf)</br>
