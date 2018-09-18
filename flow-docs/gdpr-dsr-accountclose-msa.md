---
title: 'Microsoft Flow: RODO — żądania podmiotów danych dotyczące zamykania konta w przypadku kont Microsoft (MSA) | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych RODO dotyczące zamykania konta przy użyciu usługi Microsoft Flow w przypadku kont Microsoft.
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
ms.date: 5/25/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: be12491490cac51a0b91906b1a663522c2a7658f
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688771"
---
# <a name="responding-to-gdpr-data-subject-account-close-requests-for-microsoft-flow"></a>Reagowanie na żądania podmiotów danych RODO dotyczące zamykania konta przy użyciu usługi Microsoft Flow

**Prawo do bycia zapomnianym** to kluczowa metoda ochrony stosowana w rozporządzeniu RODO. To prawo obejmuje usunięcie wszystkich danych, z wyjątkiem informacji z dzienników inspekcji. Gdy użytkownik decyduje się zamknąć swoje konto Microsoft (MSA), usuwane są także jego dane bazowe.

Te zasoby zawierają dane osobowe, które są automatycznie usuwane, gdy użytkownik zamyka konto MSA:

|Zasoby zawierające dane osobowe|
|------|
|Działania produktów i usług|
|Historia uruchamiania|
|Przepływy|
|Kanał aktywności|
|Szczegóły użytkownika|
|Połączenia|

## <a name="account-close-requests"></a>Żądania zamknięcia konta

Te kroki opisują, jak samodzielnie obsłużyć żądania zamknięcia konta dla rozporządzenia RODO.

1. Zaloguj się do witryny [Microsoft Account Close Portal](http://go.microsoft.com/fwlink/?LinkId=523898), używając swojego konta Microsoft, a następnie wybierz pozycję **Dalej**.

    > [!NOTE]
    > Otrzymasz przypomnienie o konieczności anulowania istniejących subskrypcji lub wyeksportowania danych z istniejących usług, które możesz subskrybować.
    >
    >

    ![Anulowanie subskrypcji](./media/gdpr-dsr-delete-msa/accountclose.png)

1. Potwierdź, że rozumiesz skutki zamknięcia konta MSA, a następnie wybierz pozycję **Oznacz konto do zamknięcia**.

    Pojawi się powiadomienie z informacją, że Twoje konto zostanie zamknięte za 30 dni. W dowolnym momencie tego 30-dniowego okresu możesz ponownie otworzyć to konto.

    ![Konto zamknięte](./media/gdpr-dsr-delete-msa/accountclosed.png)

    Po upływie tego 30-dniowego okresu rozpocznie się proces usuwania wszystkich zasobów usługi Microsoft Flow dla tego konta MSA.

## <a name="learn-more"></a>Dowiedz się więcej

* Wprowadzenie do usługi [Microsoft Flow](getting-started.md)
* Dowiedz się, [co nowego](release-notes.md) w usłudze Microsoft Flow
