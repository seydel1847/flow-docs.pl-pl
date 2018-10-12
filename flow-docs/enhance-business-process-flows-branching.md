---
title: Rozszerzanie przepływów procesów biznesowych za pomocą rozgałęziania przy użyciu usługi PowerApps | Microsoft Docs
description: Dowiedz się, jak używać rozgałęziania w ramach przepływu procesów biznesowych
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 62cfac6b-0d78-48de-9364-0287454aa2a0
caps.latest.revision: 9
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: a7e1dc8d366ac9f23682362c8a673eb67df65975
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690519"
---
# <a name="tutorial-enhance-business-process-flows-with-branching"></a>Samouczek: rozszerzanie przepływów procesów biznesowych za pomocą rozgałęziania

Przepływy procesów biznesowych prowadzą Cię przez różne etapy procesów sprzedaży, marketingu i usług w kierunku ukończenia. W prostych przypadkach liniowy przepływ procesu biznesowego jest dobrym rozwiązaniem. Jednak w przypadku bardziej złożonych scenariuszy, możesz rozszerzyć przepływ procesów biznesowych za pomocą rozgałęziania. Jeśli masz uprawnienia do tworzenia przepływów procesów biznesowych, możesz utworzyć przepływ procesów biznesowych z wieloma gałęziami przy użyciu logiki `If-Else`. Warunek rozgałęziania może składać się z wielu wyrażeń logicznych używających kombinacji operatorów `AND` lub `OR`. Wybór gałęzi odbywa się automatycznie, w czasie rzeczywistym, na podstawie reguł zdefiniowanych podczas definiowania procesu. Na przykład w przypadku sprzedaży samochodów możesz skonfigurować pojedynczy przepływ procesów biznesowych, który po wspólnym etapie kwalifikacji dzieli się na dwie oddzielne gałęzie na podstawie reguły (czy klient preferuje zakup nowego samochodu, czy samochodu używanego, czy dysponuje budżetem powyżej, czy poniżej 20 000 USD itd. ) — jedna gałąź dotyczy sprzedaży nowych samochodów, a druga używanych. Aby uzyskać więcej informacji na temat przepływów procesów biznesowych, zobacz [Omówienie przepływów procesów biznesowych](business-process-flows-overview.md).  
  
 Na poniższym diagramie przedstawiono przepływ procesów biznesowych z gałęziami.  
  
 ![Schemat blokowy przedstawiający kroki w procesie sprzedaży samochodu](media/example-car-sales-flow-chart.png "Schemat blokowy przedstawiający kroki w procesie sprzedaży samochodu")  
  
<a name="Points"></a>   
## <a name="what-you-need-to-know-when-designing-business-process-flows-with-branches"></a>Co należy wiedzieć podczas projektowania przepływów procesów biznesowych z gałęziami  
 Podczas projektowania przepływu procesów biznesowych z gałęziami zwróć uwagę na następujące kwestie:  
  
-   Proces może obejmować maksymalnie 5 unikatowych jednostek.  
  
-   Każdy proces może składać się z maksymalnie 30 etapów, a każdy etap może zawierać maksymalnie 30 kroków.  
  
-   Każda gałąź nie może mieć więcej niż 5 poziomów głębokości.  
  
-   Reguła rozgałęziania musi bazować na krokach w etapie bezpośrednio ją poprzedzającym.  
  
-   Wiele warunków możesz połączyć w regułę za pomocą operatora `AND` lub `OR`, ale nie obu tych operatorów jednocześnie.  
  
-   Podczas definiowania przepływu procesów możesz opcjonalnie wybrać relację jednostek. Ta relacja musi być relacją jednostki 1:N (jeden do wielu).  
  
-   Dla danego rekordu danych może jednocześnie działać więcej niż jeden aktywny proces.  
  
-   Układ kafelków (etapy, kroki, warunki itp.) dla przepływu procesów możesz zmienić, przeciągając i upuszczając.  
  
-   Podczas scalania gałęzi wszystkie gałęzie równorzędne muszą być scalane w jeden etap. Gałęzie równorzędne muszą być scalane w jeden etap lub każda gałąź równorzędna musi kończyć proces. Gałąź równorzędna nie może być scalana z innymi gałęziami i jednocześnie kończyć proces.  
  
> [!NOTE]
> - Jednostkę użytą w procesie możesz odwiedzić ponownie wiele razy (wiele zamkniętych pętli jednostki).  
> - Proces może przejść z powrotem do poprzedniego etapu niezależnie od typu jednostki. Jeśli na przykład aktywny etap dla rekordu oferty to **Dostarczanie oferty**, użytkownicy procesu mogą zmienić aktywny etap dla rekordu szansy sprzedaży na **Propozycja**.  
>   
>   W kolejnym przykładzie załóżmy, że proces jest obecnie na etapie **Przedstawianie propozycji** naszego przepływu procesów: **Kwalifikowanie potencjalnego klienta** > **Identyfikowanie potrzeb** > **Tworzenie propozycji** > **Przedstawianie propozycji** > **Zamykanie**. Jeśli przedstawiona klientowi propozycja wymaga dokładniejszej analizy w celu zidentyfikowania potrzeb klienta, użytkownicy mogą po prostu wybrać etap **Identyfikowanie potrzeb** naszego procesu i wybrać pozycję **Ustaw jako aktywny**.  
  
<a name="CarSelling365"></a>   
## <a name="dynamics-365-customer-engagement-example-car-selling-process-flow-with-two-branches"></a>Przykład usługi Dynamics 365 Customer Engagement: przepływ procesów sprzedaży samochodu z dwoma gałęziami
 
Spójrzmy na przykład przepływu procesów biznesowych z dwoma gałęziami dotyczący sprzedaży samochodów nowych i używanych.  
  
 Najpierw utworzymy nowy proces o nazwie **Proces sprzedaży samochodu**.  
  
1.  [Otwórz eksploratora rozwiązań](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer), a następnie w okienku nawigacji po lewej stronie wybierz pozycję**Procesy**.  
  
2.  Wybierz pozycję **Nowy**, aby utworzyć nowy proces.  
  
3.  W polu **Kategoria** wybierz wartość **Przepływ procesów biznesowych**, a w polu **Jednostka podstawowa** — **Potencjalny klient**.  
  
4.  Dodaj pierwszy etap procesu o nazwie **Kwalifikowanie** oraz dodaj kroki **Przedział czasu zakupu** i **Preferencje dotyczące samochodu**.  
  
5.  Po wspólnym etapie **Kwalifikowanie** możemy podzielić proces na dwie oddzielne gałęzie za pomocą kafelka **Warunek**.  
  
    1.  Skonfiguruj kafelek warunku przy użyciu reguł spełniających Twoje wymagania biznesowe  
  
    2.  Aby dodać pierwszą gałąź etapu, dodaj kafelek etapu na ścieżce „Tak” kafelka warunku  
  
    3.  Aby dodać drugą gałąź, która jest wykonywana, gdy warunek nie jest spełniony, dodaj kafelek etapu na ścieżce „Nie” kafelka warunku  
  
> [!TIP]
>  Na ścieżce „Nie” istniejącego kafelka warunku możesz dodać kolejny warunek, aby rozgałęzianie było bardziej złożone.  
  
 ![Obraz przedstawiający utworzony etap Kwalifikowanie](media/example-car-sales-qualify-stage.JPG "Obraz przedstawiający utworzony etap Kwalifikowanie")  
  
 Jeśli **Preferencje dotyczące samochodu** = **Nowy**, proces przechodzi do etapu **Sprzedaż nowego samochodu**. W przeciwnym razie rozpoczyna etap **Sprzedaż używanego samochodu** w drugiej gałęzi, jak pokazano poniżej.  
  
 ![Obraz przedstawiający etap Sprzedaż nowego samochodu](media/example-car-sales-new-stage-1.JPG "Obraz przedstawiający etap Sprzedaż nowego samochodu")  
  
 ![Etap Sprzedaż używanego samochodu](media/example-car-sales-pre-owned-stage.JPG "Etap Sprzedaż używanego samochodu")  
  
 Po wykonaniu wszystkich kroków w etapie **Sprzedaż nowego samochodu** lub **Sprzedaż używanego samochodu** proces wraca ponownie do głównego przepływu w ramach etapu **Dostarczanie oferty**.  
  
 ![Etap Dostarczanie oferty](media/example-car-sales-deliver-quote-stage.JPG "Etap Dostarczanie oferty")  
  
<a name="PreventInformation"></a>   
## <a name="prevent-information-disclosure"></a>Zapobieganie ujawnieniu informacji  
 Rozważ przepływ procesów biznesowych z gałęziami dotyczący przetwarzania wniosku o pożyczkę w banku, jak pokazano poniżej. Jednostki niestandardowe używane w poszczególnych etapach są wyświetlane w nawiasach.  
  
 ![Schemat blokowy przedstawiający kroki w przykładowym procesie dotyczącym zapobiegania ujawnieniu informacji](media/example-car-sales-flow-chart-process-prevent-information-disclosure.png "Schemat blokowy przedstawiający kroki w przykładowym procesie dotyczącym zapobiegania ujawnieniu informacji")  
  
 W tym scenariuszu specjalista ds. pożyczek w banku musi mieć dostęp do rekordu Wniosek, ale bez możliwości wglądu w badanie wniosku. Na pierwszy rzut oka wygląda na to, że możesz to łatwo osiągnąć, przypisując specjaliście ds. pożyczek rolę zabezpieczeń, która nie ma dostępu do jednostki Badanie. Przyjrzyjmy się jednak temu przykładowi bardziej szczegółowo i sprawdźmy, czy jest to faktycznie prawda.  
  
 Załóżmy, że klient składa w banku wniosek o pożyczkę na kwotę ponad 60 000 USD. Specjalista ds. pożyczek przegląda wniosek na pierwszym etapie. Jeśli jest spełniona reguła rozgałęziania sprawdzająca, czy kwota należności dla banku przekracza 50 000 USD, kolejnym etapem procesu jest sprawdzenie, czy wniosek nie jest próbą oszustwa. Jeśli okaże się, że to faktycznie przypadek oszustwa, proces przechodzi do podjęcia czynności prawnych w odniesieniu do osoby wnioskującej. Specjalista ds. pożyczek nie może mieć wglądu do dwóch etapów badania, ponieważ nie ma dostępu do jednostki Badanie.  
  
 Jeśli jednak specjalista ds. pożyczek otworzy rekord Wniosek, będzie tam widoczny cały szczegółowy proces. Nie tylko będzie mieć możliwość zobaczenia etapu badania pod kątem oszustwa, lecz także zidentyfikowania wyniku badania, dzięki możliwości wyświetlenia etapu Czynności prawne w ramach procesu. Ponadto będzie mieć możliwość podglądu kroków w ramach etapów badania, wybierając dany etap. Chociaż nie będzie mieć możliwości wyświetlenia danych ani stanu ukończenia kroku, może zidentyfikować potencjalne działania podjęte względem osoby wnioskującej w ramach etapów badania i czynności prawnych.  
  
 W ramach tego przepływu procesu specjalista ds. pożyczek będzie mógł wyświetlić etapy Badanie pod kątem oszustwa i Czynności prawne, co stanowi niewłaściwe ujawnienie informacji. Zaleca się zwrócenie szczególnej uwagi na informacje, które mogą zostać ujawnione na skutek rozgałęziania. W naszym przykładzie wystarczy podzielić proces na dwa oddzielne procesy — jeden dotyczący przetwarzania wniosku, a drugi badania pod kątem oszustwa, aby zapobiec ujawnieniu informacji. Proces dla specjalisty ds. pożyczek będzie wyglądać następująco:  
  
 ![Schemat blokowy przedstawiający dodatkowe kroki w procesie w celu zapobiegania ujawnieniu informacji](media/example-car-sales-flow-chart-additional-steps-prevent-information-disclosure.png "Schemat blokowy przedstawiający dodatkowe kroki w procesie w celu zapobiegania ujawnieniu informacji")  
  
 Proces badania będzie niezależny i będzie obejmować następujące etapy:  
  
 ![Schemat blokowy przedstawiający kroki w procesie badania dla przypadków ujawnienia informacji](media/example-car-sales-flow-chart-investigation-information-disclosure-case.png "Schemat blokowy przedstawiający kroki w procesie badania dla przypadków ujawnienia informacji")  
  
 Konieczne będzie przygotowanie przepływu pracy w celu synchronizacji decyzji Zatwierdź/Odrzuć między rekordami Badanie i Wniosek.  
  
### <a name="next-steps"></a>Następne kroki  
 [Tworzenie przepływu procesów biznesowych](create-business-process-flow.md)   
 [Tworzenie niestandardowej logiki biznesowej z użyciem procesów](guide-staff-through-common-tasks-processes.md)   
 
