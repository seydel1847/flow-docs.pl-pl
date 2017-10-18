---
title: "Dodawanie warunku do przepływu | Microsoft Docs"
description: "Ustal, że przepływ wykonuje co najmniej jedno zadanie, ale tylko wtedy, gdy spełniony jest konkretny warunek."
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
ms.date: 10/22/2016
ms.author: stepsic
ms.openlocfilehash: 1291b32f001be211acddbf1c83f3b1bdf03f2ac3
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="add-a-condition-to-a-flow"></a>Dodawanie warunku do przepływu
Ustal, że przepływ wykonuje co najmniej jedno zadanie, ale tylko wtedy, gdy spełniony jest konkretny warunek. Na przykład ustal, że otrzymasz wiadomość e-mail tylko wtedy, gdy tweet zawierający słowo kluczowe zostanie przesłany dalej co najmniej 10 razy.

**Wymagania wstępne**

* [Utworzenie przepływu](get-started-logic-template.md) na podstawie szablonu — w tym samouczku [ten przepływ będzie używany](https://flow.microsoft.com/galleries/public/templates/e78571e5c70e4806a18eeacba5a897c8/) jako przykładowy

## <a name="add-a-condition"></a>Dodawanie warunku
1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) wybierz pozycję **Moje przepływy** znajdującą się na górnym pasku nawigacyjnym.
2. Na liście przepływów wybierz utworzony przepływ. W tym samouczku używany jest przykład z wyzwalaczem usługi Twitter i akcją programu SharePoint.
3. W obszarze ostatniej akcji wybierz przycisk **Nowy krok**.
4. Wybierz opcję **Dodaj warunek**.
   
    ![Przycisk warunku](./media/add-a-condition/add-condition.png)
5. Wybierz pusty obszar w polu **Nazwa obiektu** i wybierz opcję **Dodaj zawartość dynamiczną**, aby otworzyć menu zawartości dynamicznej.
6. Wybierz parametr **Liczba tweetów przesłanych dalej**, aby dodać go do pola.
7. W polu **Relacja** wybierz **jest większe lub równe**.
8. W polu **Wartość** wpisz **10**.
   
    ![Pole NAZWA OBIEKTU z parametrem](./media/add-a-condition/specify-condition.png)
9. Kliknij nagłówek akcji, którą chcesz umieścić w warunku (na przykład **Utwórz element**) i przeciągnij ją do pola poniżej tekstu **JEŚLI TAK**. Po zwolnieniu przycisku myszy akcja powinna zostać umieszczona w tym polu.
   
    ![Przeciąganie akcji](./media/add-a-condition/drag-action.png)
10. Zapisz przepływ.

## <a name="edit-in-advanced-mode"></a>Edytowanie w trybie zaawansowanym
Można również wybrać link **Edytuj w trybie zaawansowanym**, aby utworzyć bardziej zaawansowane warunki. Możesz użyć dowolnego wyrażenia z *języka definicji programu Workflow*. [Dowiedz się więcej o](https://msdn.microsoft.com/library/azure/mt643789.aspx) dostępnych funkcjach.

