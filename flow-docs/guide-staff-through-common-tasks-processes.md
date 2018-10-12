---
title: Tworzenie niestandardowej logiki biznesowej za pośrednictwem procesów przy użyciu usługi PowerApps | MicrosoftDocs
description: Dowiedz się więcej na temat różnych typów logiki biznesowej do użycia w aplikacji
ms.custom: ''
ms.date: 05/01/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: b6cf8c2bc5e7499e7eaf5feb367c07a3aa94b3f7
ms.sourcegitcommit: f7985b96afe68b079b7fd4a6d04cd0a042d893e0
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47188598"
---
# <a name="create-custom-business-logic-through-processes"></a>Tworzenie niestandardowej logiki biznesowej za pośrednictwem procesów

Definiowanie i wymuszanie spójnych procesów biznesowych jest jednym z głównych powodów korzystania z aplikacji opartych na modelu. Dzięki spójnym procesom użytkownicy systemu mogą skoncentrować się na pracy i nie muszą pamiętać o ręcznym wykonywaniu zestawu czynności. Procesy mogą być proste lub złożone i mogą zmieniać się wraz z upływem czasu.  
  
Usługa PowerApps oferuje kilka typów procesów, z których każdy jest przeznaczony do innych celów:  
  
-   Przepływy procesów biznesowych  
  
-   Przepływy zadań mobilnych  
  
-   Przepływy pracy  
  
-   Akcje  
  
 Podobnie jak w przypadku procesów, można również tworzyć reguły biznesowe i rekomendacje. Aby uzyskać więcej informacji, zobacz [Tworzenie reguł biznesowych i rekomendacji do stosowania logiki w formularzu](/powerapps/maker/model-driven-apps/create-business-rules-recommendations-apply-logic-form)  

> [!NOTE]
>  Używanie procesów może mieć wpływ na wymagania licencyjne dotyczące usług PowerApps i przepływów. Aby uzyskać więcej informacji, zobacz [Wymagania licencyjne dla jednostek](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-entity-licenses). 


<a name="BKMK_BP"></a>   
## <a name="when-to-use-business-process-flows"></a>Kiedy należy używać przepływów procesów biznesowych  
 Przepływu procesów biznesowych należy użyć, jeśli personel ma przechodzić przez te same etapy i wykonywać te same czynności podczas interakcji z klientem. Na przykład utwórz przepływ procesów biznesowych, aby wszyscy obsługiwali żądania obsługi klientów w ten sam sposób lub aby wymagać od personelu uzyskania zatwierdzenia faktury przed przesłaniem zamówienia.  
  
 Środowisko oferuje kilka gotowych do użycia przepływów procesów biznesowych związanych z typowymi zadaniami w zakresie sprzedaży, usług i marketingu. Można je stosować bez żadnych zmian lub wprowadzając niewielkie zmiany. Możesz również utworzyć własny przepływ. Zobacz następujący temat, aby uzyskać więcej informacji o przepływach procesów biznesowych:  
  
-   [Tworzenie przepływu procesów biznesowych](create-business-process-flow.md)  
  
<a name="BKMK_WF"></a>   
## <a name="when-to-use-workflows"></a>Kiedy należy używać przepływów pracy  
 Przepływów pracy należy używać w celu automatyzowania procesów biznesowych w tle. Przepływy pracy są zwykle inicjowane przez zdarzenia systemowe, dlatego użytkownik nie musi wiedzieć, że zostały uruchomione. Przepływy pracy działające w tle są „asynchroniczne”. Przepływy pracy można również konfigurować tak, aby użytkownicy inicjowali je ręcznie, gdy zajdzie potrzeba automatyzacji typowych zadań, takich jak automatyczne wysyłanie wiadomości e-mail z potwierdzeniem do klienta po wysłaniu zamówienia. Przepływy pracy działające w czasie rzeczywistym są „synchroniczne”. Aby uzyskać więcej informacji na temat przepływów pracy, zobacz [Workflow processes (Procesy przepływu pracy)](workflow-processes.md).  

<a name="BKMK_Actions"></a>   
## <a name="when-to-use-actions"></a>Kiedy należy używać akcji  
 Akcji należy używać, aby zautomatyzować serię poleceń w systemie. Akcje rozszerzają słownictwo dla deweloperów umożliwiające wyrażanie procesów biznesowych. Akcje umożliwiają użycie podstawowych czasowników, takich jak Create (Utwórz), Update (Zaktualizuj), Delete (Usuń) i Assign (Przypisz) oferowanych przez system, do tworzenia bardziej ekspresyjnych czasowników, takich jak Approve (Zatwierdź), Escalate (Eskaluj), Route (Skieruj) lub Schedule (Zaplanuj). Jeśli definicja procesu biznesowego ulegnie zmianie, osoba niebędąca deweloperem może edytować akcję niestandardową, aby nie trzeba było zmieniać kodu.  Aby uzyskać więcej informacji na temat akcji, zobacz [Akcje](create-actions.md)  
  
<a name="useMSFlow"></a>   
## <a name="when-to-use-microsoft-flow"></a>Kiedy należy używać usługi Microsoft Flow  
 Usługi Microsoft Flow należy używać do tworzenia zautomatyzowanych przepływów pracy, które wykonują akcje między środowiskiem i ulubioną aplikacją lub usługą, taką jak Dynamics 365, Twitter, Dropbox, usługi Google, Office 365 i SharePoint. Przepływ można wyzwolić na podstawie określonej akcji lub wywołać z poziomu aplikacji. Więcej informacji: [Używanie usługi Microsoft Flow w celu automatyzowania procesów w usługach](https://docs.microsoft.com/dynamics365/customer-engagement/basics/use-flow-automate-processes-across-services
)  
  
<a name="BKMK_Where"></a>   
## <a name="where-do-i-go-to-create-processes"></a>Gdzie można tworzyć procesy?  
 Istnieją dwie ścieżki przechodzenia do procesów:  
  
- Otwórz [Eksploratora rozwiązań](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer) i przejdź do pozycji **Składniki > Procesy**. Ta ścieżka zapewnia wygodny dostęp podczas wykonywania innych zadań dostosowywania przy użyciu narzędzi do dostosowywania.  

- **[Ustawienia](/powerapps/maker/model-driven-apps/advanced-navigation#settings) > Procesy**. Ta ścieżka umożliwia korzystanie z widoków zdefiniowanych dla jednostki Proces, w tym wszystkich widoków niestandardowych.  
  
 Poszczególne przepływy procesów biznesowych można również edytować za pomocą przycisku **Edytuj proces** na pasku poleceń formularza, w którym przepływ procesów biznesowych jest aktywny.  
  
<a name="BKMK_WhoCreate"></a>   
## <a name="who-can-create-processes"></a>Kto może tworzyć procesy?  
 Tylko osoby z rolą zabezpieczeń Administrator systemu, Konfigurator systemu lub Prezes zarządu mogą tworzyć procesy, które są stosowane w całym środowisku. Osoby z innymi rolami mogą tworzyć procesy przy użyciu dostępu na ograniczonym poziomie. Na przykład osoby z poziomem dostępu Użytkownik mogą tworzyć na własny użytek przepływy pracy z rekordami, które będą należeć do tych osób.  
  
 W poniższej tabeli przedstawiono poziom dostępu procesów w oparciu o domyślne role zabezpieczeń.  
  
|||  
|-|-|  
|**Rola zabezpieczeń**|**Poziom dostępu**|  
|Prezes zarządu|Organizacja|  
|Administrator systemu|Organizacja|  
|Konfigurator systemu|Organizacja|  
|Wiceprezes ds. marketingu|Element nadrzędny: podrzędne jednostki biznesowe|  
|Wiceprezes ds. sprzedaży|Element nadrzędny: podrzędne jednostki biznesowe|  
|Menedżer ds. usług|Jednostka biznesowa|  
|Menedżer ds. marketingu|Jednostka biznesowa|  
|Menedżer ds. sprzedaży|Jednostka biznesowa|  
|Menedżer ds. planowania|Jednostka biznesowa|  
|Przedstawiciel działu obsługi klienta|Użytkownik|  
|Specjalista ds. marketingu|Użytkownik|  
|Sprzedawca|Użytkownik|  
|Planista|Użytkownik|  
  
> [!NOTE]
>  Nawet jeśli określone osoby mogą tworzyć przepływy procesów biznesowych, przepływy pracy w czasie rzeczywistym lub procesy akcji, do ich aktywowania będą potrzebować uprawnień **Aktywowanie przepływów procesów biznesowych** lub **Aktywowanie procesów w czasie rzeczywistym**.  
  
<a name="BKMK_WhatCanProcessesDo"></a>   
## <a name="more-about-workflows-and-actions"></a>Więcej informacji na temat przepływów pracy i akcji  
 Procesy mogą sprawdzać warunki, stosować logikę rozgałęziania i wykonywać akcje. Akcje są wykonywane jako seria kroków. W poniższej tabeli opisano dostępne kroki procesów przepływu pracy i akcji. Więcej szczegółów można znaleźć w tematach dotyczących poszczególnych typów procesów.  
  
|Krok|Typ procesu|Opis|  
|----------|------------------|-----------------|  
|**Etap**|Przepływ pracy, akcja|Etapy zwiększają czytelność logiki przepływu pracy i stanowią jej objaśnienie. Jednak etapy nie wpływają na logikę ani zachowanie przepływów pracy. Jeśli proces ma etapy, wszystkie kroki w ramach procesu muszą znajdować się w etapach.|  
|**Sprawdzanie warunku**|Przepływ pracy, akcja|Instrukcja logiczna „if-\<warunek> then”.<br /><br /> Istnieje możliwość sprawdzenia wartości rekordu, którego dotyczy przepływ pracy, dowolnego rekordu połączonego z tym rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach. Na podstawie tych wartości możesz zdefiniować dodatkowe kroki wykonywane, jeśli warunek ma wartość `true`.|  
|**Gałąź warunkowa**|Przepływ pracy, akcja|Dla instrukcji logicznej „else-if-then” edytor używa tekstu „W przeciwnym przypadku if \<warunek> then:”<br /><br /> Wybierz zdefiniowany wcześniej warunek sprawdzania, aby można było dodać gałąź warunkową w celu zdefiniowania dodatkowych kroków wykonywanych, jeśli warunek sprawdzania zwróci wartość `false`.|  
|**Akcja domyślna**|Przepływ pracy, akcja|Instrukcja logiczna „else”. Edytor używa tekstu „W przeciwnym razie:”<br /><br /> Wybierz zdefiniowany wcześniej warunek sprawdzenia, gałąź warunkową, warunek oczekiwania lub gałąź równoległego oczekiwania, aby można było użyć akcji domyślnej do zdefiniowania kroków dla wszystkich przypadków niespełniających kryteriów zdefiniowanych w warunku lub elementach gałęzi.|  
|**Warunek oczekiwania**|Tylko przepływ pracy w tle|Umożliwia przepływowi pracy w tle samodzielne wstrzymanie się do momentu spełnienia kryteriów zdefiniowanych przez warunek. Przepływ pracy zostanie automatycznie uruchomiony ponownie po spełnieniu kryteriów warunku oczekiwania.|  
|**Równoległa gałąź oczekiwania**|Tylko przepływ pracy w tle|Umożliwia zdefiniowanie alternatywnego warunku oczekiwania dla przepływu pracy w tle przy użyciu odpowiadającego zestawu dodatkowych kroków wykonywanych tylko wtedy, gdy początkowe kryterium zostanie spełnione. Równoległych gałęzi oczekiwania możesz użyć do tworzenia limitów czasu w logice przepływu pracy. Umożliwiają one zapobieganie nieskończonemu oczekiwaniu przez przepływ pracy na spełnienie kryteriów zdefiniowanych w warunku oczekiwania.|  
|**Przypisywanie wartości**|Akcja|Ustawia wartość na zmienną lub parametr wyjściowy w procesie.|  
|**Tworzenie rekordu**|Przepływ pracy, akcja|Umożliwia utworzenie nowego rekordu dla jednostki i przypisanie wartości do atrybutów.|  
|**Aktualizowanie rekordu**|Przepływ pracy, akcja|Istnieje możliwość zaktualizowania rekordu, którego dotyczy przepływ pracy, dowolnego rekordu połączonego z tym rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Przypisywanie rekordu**|Przepływ pracy, akcja|Istnieje możliwość przypisania rekordu, którego dotyczy przepływ pracy, dowolnego rekordu połączonego z takim rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Wysyłanie wiadomości e-mail**|Przepływ pracy, akcja|Umożliwia wysłanie wiadomości e-mail. Istnieje możliwość utworzenia nowej wiadomości e-mail lub użycia szablonu wiadomości e-mail skonfigurowanego dla jednostki rekordu, której dotyczy przepływ pracy, dowolnej jednostki połączonej relacją N:1 z tą jednostką lub jednostki dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Uruchamianie podrzędnego przepływu pracy**|Przepływ pracy, akcja|Umożliwia uruchomienie procesu przepływu pracy skonfigurowanego jako podrzędny przepływ pracy.|  
|**Zmienianie stanu**|Przepływ pracy, akcja|Umożliwia zmianę stanu rekordu, którego dotyczy proces, dowolnego rekordu połączonego z tym rekordem relacją N:1 lub dowolnych rekordów utworzonych we wcześniejszych krokach.|  
|**Zatrzymywanie przepływu pracy**|Przepływ pracy, akcja|Umożliwia zatrzymanie bieżącego przepływu pracy lub akcji. Istnieje możliwość ustawienia stanu **Powodzenie** lub **Anulowano** i określenia komunikatu o stanie.|  
|**Krok niestandardowy**|Przepływ pracy, akcja|Umożliwia domyślne udostępnianie rozszerzeń dla elementów logicznych. Kroki mogą obejmować warunki, akcje, inne kroki lub kombinację tych elementów. Deweloperzy mogą tworzyć niestandardowe kroki przepływu pracy. Domyślnie kroki niestandardowe nie są dostępne.|

Aby uzyskać więcej informacji dla deweloperów, zobacz w przewodniku dla deweloperów temat [Automate your business processes in Customer Engagement](https://docs.microsoft.com/dynamics365/customer-engagement/developer/automate-business-processes-customer-engagement
) (Automatyzowanie procesów biznesowych na platformie Customer Engagement).
  

