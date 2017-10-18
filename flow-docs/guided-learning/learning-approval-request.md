---
title: "Przetwarzanie żądania zatwierdzenia | Microsoft Docs"
description: "Dowiedz się, w jaki sposób zatwierdzić lub odrzucić żądanie zatwierdzenia."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: -0r5ZKVEIS4
courseduration: 7m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: 6ba7a2cf0fae481457f965627ebf523f063af50d
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="process-an-approval-request"></a>Przetwarzanie żądania zatwierdzenia
W poprzednim temacie pokazano, jak tworzyć proces zatwierdzania wokół tweetów, które są przechowywane na liście programu SharePoint.  W tym temacie zobaczysz, jak wygląda środowisko, gdy osoba zatwierdzająca otrzyma nowe żądanie zatwierdzenia. 

## <a name="create-and-process-a-request"></a>Tworzenie i przetwarzanie żądania
Najpierw musimy dodać element do naszej listy programu SharePoint, a następnie możemy przetworzyć żądanie zatwierdzenia dla tego elementu.

1. Otwórz listę programu SharePoint **Tweety Contoso** skonfigurowaną w ramach poprzedniego tematu.  Wybierz pozycję **Nowy**, aby utworzyć nowy tweet. 
   
    ![Lista programu SharePoint](./media/learning-approval-request/sharepoint-list-home.png)
2. Dodaj następujące wartości w polach, a następnie wybierz pozycję **Zapisz**.
   
   * **Tytuł** — Promocje
   * **Treść tweetu** — Sprawdź nową linię produktów Contoso Flooring #ohsocontoso
   * **Data tweetu** — dzisiejsza data
     
     ![Nowy element programu SharePoint](./media/learning-approval-request/sharepoint-new-tweet.png)
3. W usłudze **Microsoft Flow** wybierz pozycję **Moje przepływy**. 
4. Wybierz przepływ **Publikuj elementy listy w usłudze Twitter po zatwierdzeniu**, który został skonfigurowany w ramach poprzedniego tematu, a następnie wybierz uruchomiony przepływ w obszarze **HISTORIA URUCHAMIANIA**.
   
    ![Historia uruchamiania](./media/learning-approval-request/run-history.png)
5. Wybierz wyzwalacz **Po utworzeniu nowego elementu**. Sprawdź, czy jest wyświetlana informacja dla utworzonego elementu listy.
   
    ![Wyzwalacz przepływu](./media/learning-approval-request/approval-flow.png)
6. W programie **Outlook** otwórz automatyczną wiadomość e-mail dotyczącą zatwierdzenia w skrzynce odbiorczej, a następnie wybierz pozycję **Zatwierdź**. 
   
    ![Żądanie w programie Outlook](./media/learning-approval-request/outlook-mail.png)
7. W **Centrum zatwierdzania** wyświetl szczegóły żądania, dodaj komentarz, a następnie wybierz pozycję **Potwierdź**. 
   
    ![Centrum zatwierdzania](./media/learning-approval-request/approval-center.png)
8. W programie **SharePoint** odśwież listę **Tweety Contoso** i sprawdź, czy parametr **Stan zatwierdzenia** ma wartość **Tak** oraz czy wprowadzony komentarz jest wyświetlany. 
   
    ![Odświeżanie listy programu SharePoint](./media/learning-approval-request/sharepoint-list-approved.png)

W tym temacie przedstawiono środowisko z punktu widzenia osoby zatwierdzającej — począwszy od otrzymania wiadomości e-mail z żądaniem zatwierdzenia po przetworzenie żądania w Centrum zatwierdzania.

