---
title: Rozpoczynanie tworzenia | Microsoft Docs
description: "Utwórz łącznik niestandardowy, udostępnij go, osadź w przepływie i skorzystaj z wielu innych możliwości"
services: 
suite: flow
documentationcenter: na
author: bbarath
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/22/2016
ms.author: barathb
ms.openlocfilehash: d22193ac40b6eb8f90abf2ae5ced91b39c2faad9
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="start-to-build-with-microsoft-flow"></a>Rozpocznij tworzenie z usługą Microsoft Flow
Aplikację możesz rozszerzyć za pomocą usługi Microsoft Flow między innymi na następujące sposoby:

* Utworzenie łącznika niestandardowego i nawiązanie z nim połączenia
* Udostępnienie tego interfejsu API wszystkim użytkownikom usługi Microsoft Flow
* Osadzenie środowiska przepływu w aplikacji
* Wykorzystanie wszystkich interfejsów API deweloperów, aby użytkownicy mogli korzystać z usługi Microsoft Flow w najwygodniejszy dla siebie sposób

## <a name="prerequisites"></a>Wymagania wstępne
* Konto w witrynie [flow.microsoft.com](https://flow.microsoft.com)

## <a name="create-a-custom-connector"></a>Tworzenie łącznika niestandardowego
Jeśli masz usługę sieci Web, którą chcesz zautomatyzować za pomocą usługi Microsoft Flow, musisz najpierw utworzyć łącznik niestandardowy. Rejestrując łącznik niestandardowy, przekazujesz usłudze Microsoft Flow informacje o właściwościach interfejsu API sieci Web, w tym o wymaganym uwierzytelnianiu, obsługiwanych wyzwalaczach i akcjach oraz parametrach i danych wyjściowych dla każdej z tych akcji.

Postępuj zgodnie z [tym samouczkiem](https://powerapps.microsoft.com/tutorials/register-custom-api/), aby zarejestrować łącznik niestandardowy. Po zarejestrowaniu możesz go udostępnić wewnątrz organizacji, aby inni pomogli go przetestować.

## <a name="share-a-custom-connector-with-all-microsoft-flow-users"></a>Udostępnianie łącznika niestandardowego wszystkim użytkownikom usługi Microsoft Flow
Po pełnym przetestowaniu łącznika niestandardowego rozpocznij proces recenzowania zgodnie z tym [wpisem w blogu](https://flow.microsoft.com/blog/calling-all-saas-apps-now-you-can-build-your-own-connector-for-flow-and-logic-apps/):

* Plik w standardzie OpenAPI reprezentujący interfejs API i wszelkie informacje uwierzytelniania
* Ikona Twojego łącznika
* Opis Twojego interfejsu API
* Około 10 pomysłów na to, jak ten interfejs API może przynieść korzyści innym użytkownikom dzięki szablonom

Po przesłaniu tych informacji firma Microsoft rozpocznie ocenianie działania interfejsu API w usłudze Microsoft Flow i Microsoft PowerApps.

## <a name="embed-the-flow-experience-in-your-website-or-app"></a>Osadzanie środowiska przepływu w witrynie sieci Web lub aplikacji
Na koniec możesz osadzić usługę Microsoft Flow w aplikacji, aby umożliwić głęboką, kontekstową integrację swojej aplikacji i wszystkich innych usług obsługiwanych przez usługę Microsoft Flow. Na przykład możesz wykonywać następujące działania:

* Przeglądanie wszystkich szablonów związanych z usługą i umożliwienie użytkownikom wyboru szablonu
* Zarządzanie przepływami, które użytkownicy powiązali z daną aplikacją

Postępuj zgodnie z [tym samouczkiem](embed-flow-dev.md), aby uzyskać więcej informacji o sposobie osadzania usługi Microsoft Flow w aplikacji.

