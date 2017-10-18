---
title: "Przegląd regionów dla usługi Microsoft Flow | Microsoft Docs"
description: "Przegląd wraz z pytaniami i odpowiedziami dotyczącymi regionów w usłudze Microsoft Flow"
services: 
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/28/2017
ms.author: deonhe
ms.openlocfilehash: ec9b72e570c562c091aefd370f73d6862ff56f18
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="faq-for-regions-in-microsoft-flow"></a>Często zadawane pytania dotyczące regionów w usłudze Microsoft Flow
Ten dokument zawiera listę często zadawanych pytań o usługę Microsoft Flow.

## <a name="how-do-i-find-out-where-my-flow-is-deployed"></a>Jak sprawdzić, gdzie jest wdrożony przepływ?
Przepływ jest wdrożony w [regionie](https://azure.microsoft.com/regions/), w którym jest hostowane [środowisko](environments-overview-admin.md). Na przykład jeśli środowisko zostało utworzone w regionie Europa, przepływ jest wdrożony w europejskich centrach danych.

Administratorzy mogą zidentyfikować region po zalogowaniu się w [centrum administracyjnym](https://admin.flow.microsoft.com) usługi Microsoft Flow. Na karcie **Środowiska** znajduje się lista wszystkich istniejących środowisk i ich regionów.

![Wyświetlanie środowisk](media/regions-overview/environments-list.png)

## <a name="what-regions-are-available"></a>Jakie regiony są dostępne?
* Stany Zjednoczone
* Europa
* Azja
* Australia
* Indie
* Japonia
* Kanada

## <a name="what-features-are-specific-to-a-given-region"></a>Jakie funkcje są specyficzne dla danego regionu?
Środowiska można tworzyć w różnych regionach, z którymi są one później powiązane. Po utworzeniu przepływu w środowisku jest on wdrożony w centrach danych w tej lokalizacji geograficznej. Dotyczy to wszystkich elementów utworzonych w środowisku, w tym wspólnego modelu danych, przepływów, połączeń, bram, aplikacji i łączników niestandardowych.

W celu uzyskania optymalnej wydajności utwórz swoje środowisko w regionie najbliżej Twoich użytkowników. Przykładowo jeśli użytkownicy znajdują się w Europie, utwórz swoje środowiska w regionie Europa. Jeśli użytkownicy znajdują się w Stanach Zjednoczonych, utwórz swoje środowiska w regionie Stany Zjednoczone.

## <a name="gateways"></a>Bramy
Bramy:

* Nie są dostępne w regionie Indie.
* Są obsługiwane tylko w środowisku domyślnym — nie w środowiskach niestandardowych.

## <a name="is-microsoft-flow-available-in-national-clouds"></a>Czy usługa Microsoft Flow jest dostępna w chmurach narodowych?
Nie, usługa Microsoft Flow nie jest dostępna w chmurach narodowych. Obsługa chmur narodowych jest planowana na rok 2018.

## <a name="what-outbound-ip-addresses-are-used-in-each-region"></a>Jakie wychodzące adresy IP są używane w poszczególnych regionach?
Zobacz [Limity i konfiguracja](limits-and-config.md).

