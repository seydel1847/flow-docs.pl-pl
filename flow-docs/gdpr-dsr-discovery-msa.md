---
title: 'Microsoft Flow: RODO — żądania podmiotów danych dotyczące odnajdywania w przypadku kont Microsoft (MSA) | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych RODO dotyczące odnajdywania przy użyciu usługi Microsoft Flow w przypadku kont Microsoft.
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: KFile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 5/16/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: 9a7031780ed6582d9f881571c3d07ce8aece074d
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690740"
---
# <a name="respond-to-gdpr-data-subject-discovery-requests"></a>Reagowanie na żądania podmiotów danych RODO dotyczące odnajdywania 

Pierwszym krokiem wykonywanym w odpowiedzi na żądanie praw podmiotu danych jest znalezienie danych osobowych stanowiących przedmiot tego żądania.
Poniżej przedstawiono zestawienie zasobów usługi Microsoft Flow zawierających dane osobowe użytkownika, który uwierzytelnia się za pomocą swojego konta Microsoft (MSA).

|Zasób|Cel|
|-----|-----|
|Historia uruchamiania|Zawiera historię wykonania każdego przepływu w ciągu ostatnich 28 dni. Te dane obejmują czas rozpoczęcia, czas zakończenia, stan i wszystkie informacje o danych wejściowych/wyjściowych dla każdego przebiegu przepływu. Dowiedz się więcej o [historii przebiegów przepływu](https://flow.microsoft.com/blog/download-history-recurrence/).|
|Źródło działań| Zawiera podsumowanie działań każdego przepływu, w tym stan przebiegu, błędy oraz powiadomienia.|
|Przepływy|Logika przepływu pracy dotycząca [przepływu](https://docs.microsoft.com/flow/get-started-logic-flow).|
|Połączenia|Używane przez łączniki i umożliwiające łączność z interfejsami API, systemami, bazami danych itp. Dowiedz się więcej o [połączeniach](add-manage-connections.md).|

