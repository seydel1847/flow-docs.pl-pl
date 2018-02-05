---
title: "Łącznik interfejsu API — często zadawane pytania | Microsoft Docs"
description: "Odpowiedzi na pytania dotyczące wymagań, wyzwalaczy i innych obszarów."
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
ms.date: 09/19/2017
ms.author: astay
ms.openlocfilehash: 1715700fa6a94bb35733865556a2c9be0ba3ce9f
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2018
---
# <a name="api-connector-faq-microsoft-flow"></a>Łącznik interfejsu API — często zadawane pytania (Microsoft Flow)
## <a name="requirements"></a>Wymagania
**Pytanie:** Czy mogę utworzyć łącznik bez interfejsów API REST? </br>
**Odpowiedź:** Nie. Aby utworzyć łącznik, Twoja usługa musi obsługiwać stabilne interfejsy API REST dla protokołu HTTP. 

**Pytanie:** Jakich narzędzi mogę użyć do utworzenia łącznika? </br>
**Odpowiedź:** Platforma Azure dostarcza funkcje i usługi, których można użyć do udostępniania dowolnej usługi jako interfejsu API, takie jak usługa Azure App Service do hostingu, API Management i nie tylko.

**Pytanie:** Jakie typy uwierzytelniania są obsługiwane? </br>
**Odpowiedź:** Można użyć następujących obsługiwanych standardów uwierzytelniania:

* uwierzytelnianie [OAuth 2.0](https://oauth.net/2/), w tym usługa [Azure Active Directory](https://azure.microsoft.com/develop/identity/), lub specjalne usługi, takie jak Dropbox, GitHub czy SalesForce
* Ogólne uwierzytelnianie OAuth 2.0
* [Uwierzytelnianie podstawowe](https://swagger.io/docs/specification/authentication/basic-authentication/)
* [Klucz interfejsu API](https://swagger.io/docs/specification/authentication/api-keys/)

## <a name="triggers"></a>Wyzwalacze
**Pytanie:** Czy można utworzyć wyzwalacze bez elementów webhook? </br>
**Odpowiedź:** Nie. Łączniki niestandardowe dla usługi Azure Logic Apps i Microsoft Flow obsługują wyłącznie wyzwalacze oparte na elementach webhook. Jeśli chcesz otrzymać inne wzorce wdrażania, skontaktuj się z [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com), przekazując więcej szczegółów na temat Twojego interfejsu API.

## <a name="certification"></a>Certyfikacja
**Pytanie**: Nie jestem partnerem firmy Microsoft ani niezależnym dostawcą oprogramowania. Czy mimo to mogę tworzyć łączniki? </br>
**Odpowiedź**: Tak. Możesz zarejestrować te łączniki do użytku wewnętrznego w Twojej organizacji, ale jeśli chcesz uzyskać certyfikację łącznika i publicznie go wydać, musisz być właścicielem bazowej usługi lub przedstawić jawne prawa do użycia interfejsu API.

## <a name="other"></a>Inne
**Pytanie:** Moje interfejsy API używają dynamicznego hosta. Jak mogę je zaimplementować zgodnie ze standardem OpenAPI? </br>
**Odpowiedź:** Łączniki niestandardowe nie obsługują dynamicznych hostów. Zamiast tego użyj statycznego hosta na potrzeby opracowywania i testowania. Jeśli chcesz uzyskać certyfikację swojego łącznika, poproś osobę kontaktową w firmie Microsoft o informacje na temat implementacji dynamicznej.

**Pytanie:** Czy kolekcje Postman Collection w wersji 2 są obsługiwane? </br>
**Odpowiedź:** Nie. Obecnie są obsługiwana wyłącznie kolekcje Postman Collection w wersji 1.

**Pytanie:** Czy standard OpenAPI 3.0 jest obsługiwany? </br>
**Odpowiedź:** Nie. Obecnie jest obsługiwany wyłącznie standard OpenAPI 2.0.

