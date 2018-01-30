---
title: "Łącznik interfejsu API — przegląd | Microsoft Docs"
description: "Niezależni dostawcy oprogramowania i właściciele usługi SaaS mogą tworzyć łączniki i certyfikować je w firmie Microsoft."
services: 
suite: flow
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 62f8f8d0af72292a61324d75bd46f53d559b46a3
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="api-connector-overview-microsoft-flow"></a>Łącznik interfejsu API — przegląd (Microsoft Flow)
**Łącznik interfejsu API** to otoka w standardzie OpenAPI (struktura Swagger) dla interfejsu API REST, która pozwala bazowej usłudze na komunikację z usługą [Microsoft Flow](https://flow.microsoft.com), usługą [PowerApps](https://powerapps.microsoft.com) i [aplikacjami Logic Apps](https://docs.microsoft.com/azure/logic-apps/). Udostępnia on użytkownikom metodę łączenia ich kont i możliwość korzystania z zestawu wstępnie skompilowanych **wyzwalaczy** i **akcji** do tworzenia aplikacji i przepływów pracy.

Jako **niezależny dostawca oprogramowania** lub **właściciel usługi SaaS** możesz tworzyć łączniki, aby obsługiwać szeroki zakres scenariuszy biznesowych i organizacji zadań na potrzeby użytkowników. Łącznik pomaga wyjść poza zdefiniowany zestaw integracji oraz zwiększyć zasięg, możliwości odnajdywania i wykorzystanie Twojej usługi.

## <a name="requirements"></a>Wymagania
Warunkiem utworzenia i przesłania łącznika jest spełnianie przez usługę następujących wymagań:

* Scenariusz użytkownika biznesowego, który dobrze pasuje do usług Microsoft Flow, PowerApps i Logic Apps
* Publicznie dostępna usługa ze stabilnymi interfejsami API REST

## <a name="build-your-connector"></a>Tworzenie łącznika
Pierwszym krokiem tworzenia łącznika interfejsu API jest utworzenie w pełni funkcjonalnego łącznika niestandardowego. Łącznik niestandardowy działa tak samo jak łącznik interfejsu API, lecz jego dostępność jest ograniczona do autora i określonych użytkowników w ramach jego dzierżawy.

Proces tworzenia łącznika obejmuje wiele kroków:

![Kroki tworzenia łącznika interfejsu API](./media/api-connectors-overview/authoring-steps.png)

[Dowiedz się więcej](api-connector-dev.md) o opracowywaniu łącznika interfejsu API.

## <a name="submit-for-certification"></a>Przesyłanie do certyfikacji
Po utworzeniu łącznika należy przesłać go do certyfikacji. W ramach procesu certyfikacji innych firm firma Microsoft przegląda łącznik przed opublikowaniem.

W ramach tego procesu jest weryfikowana funkcjonalność łącznika w usługach Microsoft Flow i PowerApps oraz jest on sprawdzany pod kątem zgodności technicznej i zawartości.

[Dowiedz się więcej](api-connector-submission.md) o procesie przesyłania łącznika do certyfikacji i publikowania.

## <a name="get-support"></a>Pomoc techniczna
Aby uzyskać pomoc techniczną dla dołączania i opracowywania, wyślij wiadomość e-mail na adres [condevhelp@microsoft.com ](mailto:condevhelp@microsoft.com). To konto jest aktywnie monitorowane i zarządzane. Pytania deweloperów i informacje o zdarzeniach szybko znajdują drogę do odpowiedniego zespołu.

