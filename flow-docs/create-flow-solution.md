---
title: Informacje o tworzeniu przepływów obsługujących rozwiązania| Microsoft Docs
description: Informacje o tworzeniu przepływów obsługujących rozwiązania.
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: kvivek
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/05/2018
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: cbc6e3a8ffe50eb7ad27e80eba044957647a1da3
ms.sourcegitcommit: b41b45f6fa29a22e9a9a4d3c726a2321b2ff3cbf
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025776"
---
# <a name="create-a-flow-in-a-solution"></a>Tworzenie przepływu w rozwiązaniu

Przepływy, które tworzy się w rozwiązaniu, są znane jako przepływy *obsługujące rozwiązania*. Wykonaj następujące kroki, aby utworzyć przepływ obsługujący rozwiązania.

## <a name="prerequisites"></a>Wymagania wstępne

Aby można było utworzyć przepływ obsługujący rozwiązania, musisz mieć co najmniej jedno rozwiązanie.

## <a name="create-the-flow"></a>Tworzenie przepływu 

1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com).
1. Wybierz pozycję **Rozwiązania** na pasku nawigacyjnym.

   ![](./media/create-flow-solution/select-solutions-from-left-nav.png)

1. Wybierz rozwiązanie, w którym utworzysz przepływ.

   ![](./media/create-flow-solution/new-solution-created.png)

1. Wybierz pozycję **+ Nowy**, a następnie wybierz pozycję **Przepływ**.

   ![](./media/create-flow-solution/select-new-flow.png)

   Zostanie otwarta usługa Microsoft Flow.

1. Użyj dostępnych łączników i wyzwalaczy w celu utworzenia własnego przepływu.

   W tym przykładzie utworzymy prosty przepływ, który wysyła powiadomienie po nadejściu wiadomości e-mail do skrzynki odbiorczej.
1. Wyszukaj, a następnie wybierz pozycję **Office 365 Outlook**.
1. Wybierz wyzwalacz **Po nadejściu nowej wiadomości e-mail**.
1. Wybierz pozycję **+ Nowy krok**.
1. Wybierz akcję **Wyślij mi powiadomienie na urządzenie przenośne**.
1. Dodaj dynamiczny token **Temat** do pola **Tekst** w obszarze **Wyślij mi powiadomienie na urządzenie przenośne**.
1. Nadaj przepływowi nazwę i zapisz go.

   Twój przepływ powinien wyglądać następująco:

   ![](./media/create-flow-solution/new-email-notification-flow.png)
   
1. Wybierz pozycję **Rozwiązania**, aby zobaczyć swój przepływ w rozwiązaniu:

   ![](./media/create-flow-solution/new-flow-inside-solution.png)

## <a name="learn-more"></a>Dowiedz się więcej

* [Tworzenie rozwiązania](./overview-solution-flows.md)
* [Eksportowanie rozwiązania](./export-flow-solution.md)
* [Importowanie rozwiązania](./import-flow-solution.md)
* [Edytowanie przepływu obsługującego rozwiązania](./edit-solution-aware-flow.md)
* [Usuwanie przepływu obsługującego rozwiązania](./remove-solution-aware-flow.md)
