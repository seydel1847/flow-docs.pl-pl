---
title: Podsumowanie dotyczące żądań podmiotów danych RODO w przypadku kont Microsoft (MSA)| Microsoft Docs
description: Dowiedz się, jak reagować na żądania podmiotów danych w usłudze Microsoft Flow.
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
ms.openlocfilehash: 3742ac7afed24b0a1523a6038978589d293ba00b
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688495"
---
# <a name="respond-to-gdpr-data-subject-rights-dsrs-requests"></a>Reagowanie na żądania praw podmiotów danych RODO

W tym artykule opisano obowiązujące w Unii Europejskiej Ogólne rozporządzenie o ochronie danych (RODO) oraz przedstawiono kroki, jakie należy wykonać w celu zapewnienia zgodności z przepisami RODO dla użytkowników usługi Microsoft Flow, którzy uwierzytelniają się za pomocą konta Microsoft (MSA).

## <a name="prerequisites"></a>Wymagania wstępne

Aby wykonać czynności opisane w tym artykule, musisz mieć konto MSA z [bezpłatną licencją usługi Microsoft Flow](https://flow.microsoft.com/pricing/).

>[!TIP]
> Informacje o zgodności z przepisami RODO są również dostępne dla użytkowników, którzy uwierzytelniają się za pomocą [kont usługi Azure Active Directory](gdpr-dsr-summary.md).
>
>

## <a name="respond-to-dsrs-for-microsoft-flow-customer-data"></a>Reagowanie na żądania praw podmiotów danych dotyczące danych klientów usługi Microsoft Flow

Formalne żądanie podmiotu danych skierowane do kontrolera i dotyczące podjęcia akcji związanej z jego danymi nosi nazwę żądania praw podmiotu danych (DSR, Data Subject Rights). Dane osobowe są zdefiniowane w rozporządzeniu RODO jako **wszystkie dane powiązane ze zidentyfikowaną lub możliwą do zidentyfikowania osobą fizyczną**. Rozporządzenie RODO nadaje osobom (określanym jako podmioty danych) prawa do zarządzania danymi osobowymi zebranymi przez pracodawcę, agencję lub organizację (określanymi jako kontroler danych lub kontroler). Prawa te obejmują:

* Uzyskiwanie kopii danych osobowych.
* Żądanie poprawek do danych osobowych.
* Ograniczanie przetwarzania danych osobowych.
* Usuwanie danych osobowych.
* Otrzymywanie danych osobowych w formie elektronicznej w celu przenoszenia ich do innego kontrolera.

Firma Microsoft udostępnia produkty, usługi i narzędzia, które ułatwiają kontrolerom wyszukiwanie danych osobowych i wykonywanie związanych z nimi akcji w przypadku reagowania na żądania praw podmiotów danych przechowywanych w chmurze.

Oto omówienie procesów przedstawionych w tym przewodniku:

1. **Odnajdowanie**: używanie narzędzi do wyszukiwania i odnajdywania w celu łatwego znajdowania danych klienta, które mogą być przedmiotem żądania praw podmiotu danych. Jeśli stwierdzisz, że dokumenty, które zbierasz, spełniają wytyczne kontrolera wymagające podjęcia akcji, możesz wykonać co najmniej jedną z akcji praw podmiotów danych opisanych w poniższych krokach. Dowiedz się więcej z [dokumentacji wykrywania praw podmiotów danych usługi Microsoft Flow w przypadku kont Microsoft](gdpr-dsr-discovery-msa.md). Alternatywnie możesz stwierdzić, że żądanie nie spełnia wytycznych kontrolera dotyczących reagowania na żądania praw podmiotów danych.

1. **Uzyskiwanie dostępu**: pobieranie danych osobowych, które znajdują się w chmurze firmy Microsoft, i jeśli tego zażądano, wykonywanie kopii do udostępnienia osobie, której dane dotyczą.

1. **Korygowanie**: wprowadzanie zmian lub implementowanie innych żądanych akcji związanych z danymi osobowymi, jeśli mają zastosowanie.

1. **Ograniczanie**: ograniczanie przetwarzania danych osobowych przez usunięcie licencji różnych usług online albo wyłączenie żądanych usług, jeśli jest to możliwe. Można również usunąć dane z chmury firmy Microsoft i przechowywać je lokalnie lub w innej lokalizacji.

1. **Usuwanie**: trwałe usuwanie danych osobowych, które znajdują się w chmurze firmy Microsoft. Dowiedz się więcej o [usuwaniu danych osobowych w przypadku kont Microsoft](gdpr-dsr-delete-msa.md). Dowiedz się więcej o [zamykaniu konta Microsoft](gdpr-dsr-accountclose-msa.md).

1. **Eksportowanie**: udostępnianie elektronicznej kopii danych osobowych (w formacie możliwym do odczytu maszynowego). [Dowiedz się więcej na temat eksportowania danych osobowych w przypadku kont Microsoft](gdpr-dsr-export-msa.md).
