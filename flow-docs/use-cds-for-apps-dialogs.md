---
title: Używanie sesji dialogowych usługi CDS for Apps dla procesów z przewodnikiem (przestarzałe) | MicrosoftDocs
description: Sesje dialogowe są synchronicznymi lub interaktywnymi procesami, które zbierają i przetwarzają informacje za pomocą skryptów krok po kroku, aby prowadzić użytkowników przez proces
ms.custom: ''
ms.date: 10/31/2017
ms.reviewer: ''
ms.topic: article
ms.assetid: d17f8ae2-854b-4f67-a115-5a03d4f0b8ce
caps.latest.revision: 25
author: msftman
ms.author: deonhe
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: f8b2e87bdb9aed63e9f180d446349779cd37c25c
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689668"
---
# <a name="use-cds-for-apps-dialogs-for-guided-processes-deprecated"></a>Używanie sesji dialogowych usługi CDS for Apps dla procesów z przewodnikiem (przestarzałe)

[Sesje dialogowe są przestarzałe](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#dialogs-are-deprecated). Należy zastępować sesje dialogowe przepływami procesów biznesowych lub aplikacjami kanwy. Więcej informacji: [Zastępowanie sesji dialogowych za pomocą przepływów procesów biznesowych lub aplikacji kanwy](replace-dialogs.md) 

Sesje dialogowe są synchronicznymi lub interaktywnymi procesami w usłudze Common Data Service (CDS) for Apps, które zbierają i przetwarzają informacje za pomocą skryptów krok po kroku, aby prowadzić użytkowników przez proces. Na przykład można utworzyć sesje dialogowe, by pełniły rolę przewodnika dla przedstawicieli działu obsługi klienta przy rozwiązywaniu i eskalacji sprawy. Podobnie można utworzyć sesje dialogowe w celu standaryzacji procesów sprzedaży, takich jak kwalifikacja szansy sprzedaży i ocenianie potencjalnych klientów. Aby uzyskać więcej informacji, zobacz artykuł [Use dialogs for guided processes (Używanie sesji dialogowych dla procesów z przewodnikiem)](/dynamics365/customer-engagement/developer/use-dialogs-guided-processes) w podręczniku dewelopera usługi Dynamics 365 Customer Engagement.

## <a name="differences-between-workflows-and-dialogs"></a>Różnice między przepływami pracy a sesjami dialogowymi

Poniższa tabela zawiera informacje o różnicach między przepływami pracy i sesjami dialogowymi usługi CDS for Apps.  


| Przepływy pracy     |    Sesje dialogowe      |
|---------------|--------------|
|                                                                                                  Mogą być uruchamiane przez użytkownika lub mogą być zautomatyzowane.                                                                                                   |                                                                                          Muszą być uruchamiane przez użytkownika.                                                                                          |
|                                  Są procesami asynchronicznymi lub w czasie rzeczywistym i nie wymagają danych wejściowych użytkownika do pełnego wykonania. Procesy asynchroniczne są uruchamiane w tle, podczas gdy procesy w czasie rzeczywistym są uruchamiane natychmiastowo.                                   | Są procesami w czasie rzeczywistym, które wymagają danych wejściowych użytkownika do pełnego wykonania. Po uruchomieniu tych procesów wyświetlany jest interfejs przypominający kreatora, dzięki któremu można wybrać odpowiednie opcje do uruchamiania procesów. |
|                                                    Jednostka, która przechowuje szczegółowe informacje o uruchomionym asynchronicznym przepływie pracy, to jednostka `AsyncOperation`, podczas gdy jednostka `Process` jest używana dla przepływów pracy w czasie rzeczywistym.                                                     |                                                       Jednostka, która przechowuje informacje generowane przez uruchomioną sesję dialogową, to jednostka `ProcessSession`.                                                       |
|                  Wyzwalacze są obsługiwane w przypadku przepływów pracy. Aby uzyskać listę obsługiwanych wyzwalaczy, zobacz artykuł [Supported Types, Triggers, and Entities for Processes (Obsługiwane typy, wyzwalacze i jednostki dla procesów)](/dynamics365/customer-engagement/developer/supported-types-triggers-entities-actions-processes).                   |                                                                                   Wyzwalacze nie są obsługiwane w przypadku sesji dialogowych.                                                                                    |
  
### <a name="see-also"></a>Zobacz także
[Zastępowanie sesji dialogowych za pomocą przepływów procesów biznesowych lub aplikacji kanwy](replace-dialogs.md)
