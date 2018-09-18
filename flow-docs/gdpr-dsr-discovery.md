---
title: 'Microsoft Flow: RODO — żądania podmiotów danych dotyczące odnajdowania | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych RODO dotyczące odnajdowania przy użyciu usługi Microsoft Flow.
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/17/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: 9ec66eefdbf2f6b6a9047678e9c29cb66900eda2
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688932"
---
# <a name="responding-to-gdpr-data-subject-discovery-requests-for-microsoft-flow"></a>Reagowanie na żądania podmiotów danych RODO dotyczące odnajdowania przy użyciu usługi Microsoft Flow

Pierwszym krokiem wykonywanym w odpowiedzi na żądanie podmiotu danych jest znalezienie danych osobowych stanowiących przedmiot tego żądania. Ten pierwszy etap ułatwi ustalenie, czy żądanie podmiotu danych spełnia wymagania organizacji, a w co za tym idzie, czy należy się do niego zastosować, czy też je odrzucić. Na przykład po znalezieniu i przejrzeniu właściwych danych osobowych można stwierdzić, że żądanie nie spełnia wymagań organizacji, ponieważ może ono niekorzystnie wpłynąć na prawa i swobody innych osób.

Poniżej znajduje się podsumowanie typów zasobów usługi Microsoft Flow, które zawierają dane osobowe określonego użytkownika.

|**Zasoby zawierające dane osobowe**|**Cel**|
|-----|-----|
|Dzienniki generowane przez system|Dane telemetryczne, który przechwytują zdarzenia systemowe i historię.|
|Historia uruchamiania|Historia każdego wykonania przepływu w ciągu ostatnich 28 dni. Te dane obejmują czas rozpoczęcia, czas zakończenia, stan i wszystkie informacje o danych wejściowych/wyjściowych dla przepływu. [Dowiedz się więcej](https://flow.microsoft.com/blog/download-history-recurrence/)|
|Źródło działań| Zawiera podsumowanie działań przepływu, w tym stan przebiegu, błędy oraz powiadomienia.|
|Zadania użytkownika|Niewidoczne dla użytkownika zadania systemowe uruchamiane w jego imieniu w celu wykonania przepływów.|
|Przepływy|Istniejąca logika przepływu pracy dotycząca przepływu. [Dowiedz się więcej](https://docs.microsoft.com/flow/get-started-logic-flow)|
|Uprawnienia przepływu|Przepływy można udostępniać i ponownie przypisywać do innych użytkowników. Listy uprawnień istnieją dla wszystkich przepływów. [Dowiedz się więcej](https://docs.microsoft.com/flow/frequently-asked-questions#can-i-share-the-flows-i-create)|
|Szczegóły użytkownika|Szczegóły niewidoczne dla użytkownika, które obsługują wykonywanie przepływu.|
|Połączenia|Używane przez łączniki i umożliwiające łączność z interfejsami API, systemami, bazami danych itp. [Dowiedz się więcej](https://docs.microsoft.com/flow/add-manage-connections)|
|Uprawnienia do połączenia|Uprawnienia dotyczące określonego połączenia. [Dowiedz się więcej](https://docs.microsoft.com/flow/add-manage-connections)|
|Łączniki niestandardowe|Niestandardowe łączniki utworzone i opublikowane przez użytkownika, które umożliwiają łączenie z systemami niestandardowymi lub innych firm. [Dowiedz się więcej](https://docs.microsoft.com/connectors/custom-connectors/)|
|Uprawnienia łącznika niestandardowego|Listy uprawnień łączników niestandardowych. [Dowiedz się więcej](https://docs.microsoft.com/connectors/custom-connectors/share)|
|Brama|Bramy to lokalne usługi danych, które mogą być instalowane przez użytkownika w celu szybkiego i bezpiecznego przesyłania danych między usługą Microsoft Flow i źródłem danych znajdującym się poza chmurą. [Dowiedz się więcej](https://docs.microsoft.com/flow/gateway-manage)|
|Uprawnienia do bramy|Bramy można udostępniać użytkownikom w organizacji. [Dowiedz się więcej](https://go.microsoft.com/fwlink/?linkid=872249)|
