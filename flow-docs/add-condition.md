---
title: "Dodawanie warunku do przepływu | Microsoft Docs"
description: "Ustal, że przepływ wykonuje co najmniej jedno zadanie, ale tylko wtedy, gdy spełniony jest warunek."
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/17/2017
ms.author: stepsic
ms.openlocfilehash: 135b3509a9412f7674a1e9cb2ada86ebd2bb9f4f
ms.sourcegitcommit: 122870842a07183ab3b90e07d99b60d822d6c5ae
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="add-a-condition-to-a-flow"></a>Dodawanie warunku do przepływu

Ustal, że przepływ wykonuje co najmniej jedno zadanie, ale tylko wtedy, gdy spełniony jest warunek. Na przykład ustal, że otrzymasz wiadomość e-mail tylko wtedy, gdy tweet zawierający słowo kluczowe zostanie przesłany dalej co najmniej 10 razy.

## <a name="prerequisites"></a>Wymagania wstępne

* [Utworzenie przepływu](get-started-logic-template.md) na podstawie szablonu — w tym samouczku [ten szablon jest używany](https://flow.microsoft.com/galleries/public/templates/e78571e5c70e4806a18eeacba5a897c8/) jako przykładowy

## <a name="add-a-condition"></a>Dodawanie warunku

1. W usłudze [Microsoft Flow](https://flow.microsoft.com) wybierz pozycję **Moje przepływy** na górnym pasku nawigacji.

    Jeśli jeszcze nie zalogowano się do usługi, trzeba wykonać tę czynność.

1. Na liście przepływów wybierz jeden z utworzonych przepływów.

    W tym samouczku używany jest przykład z wyzwalaczem usługi Twitter i akcją programu SharePoint.

1. Wybierz pozycję **Edytuj przepływ**.

1. W obszarze ostatniej akcji wybierz pozycję **Nowy krok**.

1. Wybierz opcję **Dodaj warunek**.

    ![Przycisk warunku](./media/add-condition/add-condition.png)

1. Na karcie **Warunek** w polu po lewej stronie wybierz pusty obszar.

    Zostanie otwarta lista **Zawartość dynamiczna**.

1. Wybierz parametr **Liczba tweetów przesłanych dalej**, aby dodać go do pola.

1. W polu w środku karty **Warunek** wybierz pozycję **jest większe lub równe**.

1. W polu po prawej stronie wprowadź wartość **10**.

    ![Pole NAZWA OBIEKTU z parametrem](./media/add-condition/specify-condition.png)

1. Wybierz nagłówek akcji, której chcesz użyć w warunku (na przykład **Utwórz element**) i przeciągnij ją do pola poniżej tekstu **Jeśli tak**.

    Po zwolnieniu przycisku myszy akcja zostanie przeniesiona do tego pola.

    ![Przeciąganie akcji](./media/add-condition/drag-action.png)

1. Skonfiguruj akcję w wybrany sposób.

1. Zapisz przepływ.

## <a name="edit-in-advanced-mode"></a>Edytowanie w trybie zaawansowanym

Możesz również wybrać pozycję **Edytuj w trybie zaawansowanym**, aby utworzyć bardziej zaawansowane warunki. W trybie zaawansowanym możesz użyć dowolnego wyrażenia z *języka definicji programu Workflow*. Dowiedz się więcej na temat wszystkich dostępnych [wyrażeń](https://msdn.microsoft.com/library/azure/mt643789.aspx).

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak [używać wyrażeń](use-expressions-in-conditions.md) w warunkach w trybie zaawansowanym.
