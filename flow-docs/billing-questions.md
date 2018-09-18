---
title: Pytania dotyczące rozliczeń oraz metod pomiarów | Microsoft Docs
description: Odpowiedzi na często zadawane pytania dotyczące rozliczeń oraz metod pomiarów w usłudze Microsoft Flow
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: aftowen
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/21/2017
ms.author: deonhe
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: 65f2776af5b0219ea887302d5cfa9e101f62c309
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690289"
---
# <a name="billing-and-metering-questions"></a>Pytania dotyczące rozliczeń oraz metod pomiarów

W tym artykule znajdują się odpowiedzi na często zadawane pytania dotyczące rozliczeń oraz metod pomiarów w usłudze Microsoft Flow

## <a name="where-can-i-find-out-what-pricing-plans-are-available"></a>Gdzie mogę sprawdzić, jakie plany cenowe są dostępne?

Zobacz [stronę z cennikiem](https://flow.microsoft.com/pricing/).

## <a name="where-can-i-find-out-what-my-plan-is"></a>Gdzie mogę sprawdzić, jaki jest mój plan?

Zobacz [stronę z cennikiem](https://flow.microsoft.com/pricing/).

## <a name="how-do-i-switch-plans"></a>W jaki sposób można przełączać plany?

W górnym menu nawigacji wybierz pozycję **Dowiedz się** > **Ceny**, a następnie wybierz plan, na który chcesz się przełączyć.

![Dowiedz się > Ceny](./media/billing-questions/learn-pricing.png)

## <a name="how-do-i-know-how-much-ive-used"></a>W jaki sposób mogę sprawdzić użycie?

Jeśli korzystasz z planu bezpłatnego lub próbnego, kliknij lub naciśnij ikonę koła zębatego na górnym pasku nawigacyjnym, aby wyświetlić bieżące użycie względem planu. 

![Przycisk Ustawienia](./media/billing-questions/settings.png)

Jeśli korzystasz z planu płatnego, liczba przebiegów jest wspólna dla wszystkich użytkowników w organizacji. Pracujemy nad funkcjami umożliwiającymi wyświetlanie dostępnego przydziału i użycia w całej organizacji.

## <a name="what-happens-if-my-usage-exceeds-the-limits"></a>Co się stanie, jeśli użycie przekroczy limity?

Microsoft Flow ograniczy przebiegi przepływu.

## <a name="where-can-i-find-more-information-regarding-the-usage-limits"></a>Gdzie mogę znaleźć więcej informacji na temat limitów użycia?

Na [stronie z cennikiem](https://flow.microsoft.com/pricing/) w sekcji **Często zadawane pytania**.

## <a name="what-happens-if-i-try-to-execute-runs-too-frequently"></a>Co się stanie, jeśli przebiegi będą uruchamiane zbyt często?

Częstotliwość uruchamiania przebiegów zależy od planu. Jeśli na przykład korzystasz z planu bezpłatnego, przepływy można uruchamiać co 15 minut. Jeśli przepływ zostanie wyzwolony przed upływem 15 minut od ostatniego przebiegu, zostanie on umieszczony w kolejce do chwili, gdy upłynie 15 minut.

## <a name="what-counts-as-a-run"></a>Co jest liczone jako przebieg?

Każde wyzwolenie przepływu, zarówno za pomocą wyzwalacza automatycznego, jak i w sposób ręczny, jest uznawane za przebieg. Sprawdzenia, czy istnieją nowe dane, nie są traktowane jako przebiegi.

## <a name="are-there-differences-between-microsoft-accounts-and-work-or-school-accounts-for-billing"></a>Czy w przypadku rozliczeń istnieją różnice między kontami Microsoft a kontami służbowymi?

Tak. Jeśli zalogujesz się przy użyciu konta Microsoft (czyli konta, którego nazwa kończy się na @outlook.com lub @gmail.com), możesz używać tylko planu bezpłatnego. Aby móc korzystać z funkcji planu płatnego, zaloguj się przy użyciu służbowego adresu poczty e-mail.

## <a name="im-trying-to-upgrade-but-im-told-my-account-isnt-eligible"></a>Podczas próby uaktualnienia wyświetlany jest komunikat z informacją, że moje konto nie jest uprawnione

Aby przeprowadzić uaktualnienie, użyj konta służbowego lub utwórz [konto próbne usługi Office 365](https://powerbi.microsoft.com/documentation/powerbi-admin-signing-up-for-power-bi-with-a-new-office-365-trial/).

## <a name="why-did-i-run-out-of-runs-when-my-flow-only-ran-a-few-times"></a>Dlaczego został wyczerpany limit przebiegów, jeśli mój przepływ został uruchomiony tylko kilka razy?

Niektóre przepływy mogą być uruchamiane częściej niż jest to oczekiwane. Możesz na przykład utworzyć przepływ, który wysyła powiadomienie wypychane za każdym razem, gdy kierownik wysyła Ci wiadomość e-mail Ten przepływ musi być uruchamiany za każdym razem, gdy otrzymujesz wiadomość e-mail (od dowolnej osoby), ponieważ przepływ musi sprawdzić, czy wiadomość została wysłana przez kierownika. Ta akcja jest liczona jako przebieg.

Ten problem można obejść, przeprowadzając całe wymagane filtrowanie w ramach wyzwalacza. W przykładzie powiadomienia push rozwiń menu **Opcje zaawansowane**, a następnie podaj adres e-mail kierownika w polu **Od**.

## <a name="other-limits-and-caveats"></a>Inne limity i zastrzeżenia

* Każde konto może mieć maksymalnie:
  * 250 przepływów.
  * 15 łączników niestandardowych.
  * 20 połączeń na interfejs API i łącznie 100 połączeń
* Bramę można zainstalować tylko w środowisku domyślnym.
* Niektóre łączniki zewnętrzne, takie jak usługa Twitter, implementują ograniczanie przepływności połączenia w celu kontrolowania jakości usługi. Gdy ograniczanie przepływności jest włączone, przepływy zakończą się niepowodzeniem. Jeśli Twoje przepływy kończą się niepowodzeniem, przejrzyj szczegóły przebiegu zakończonego niepowodzeniem w historii uruchamiania przepływu.
