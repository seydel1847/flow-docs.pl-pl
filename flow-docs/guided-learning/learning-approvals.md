---
title: "Żądania zatwierdzenia w usłudze Microsoft Flow | Microsoft Docs"
description: "Dowiedz się, jak zarządzać przepływem pracy zatwierdzania przy użyciu usługi Microsoft Flow."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: o-pgEBW3fOI
courseduration: 14m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 049b713ed653ab5555e5f48f63e46cce7f3207ee
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="approval-requests"></a>Żądania zatwierdzenia
Oprócz pomocy w **otrzymywaniu powiadomień**, **kopiowaniu plików** i **zbieraniu danych** usługa Microsoft Flow może także ułatwić **usprawnianie procesów zatwierdzania**.

## <a name="vacation-scenario"></a>Scenariusz dotyczący urlopów
Załóżmy, że **kierujesz** zespołem i prosisz pracowników o utworzenie **wniosków urlopowych** na **liście programu SharePoint**. Teraz chcesz utworzyć **proces zatwierdzania** obsługujący te elementy listy, dzięki któremu nowe wnioski urlopowe będą **szybko przetwarzane**, a osoba składająca wniosek będzie **powiadamiana automatycznie**.  

## <a name="sharepoint-and-microsoft-flow"></a>Program SharePoint i usługa Microsoft Flow
Program **SharePoint** ma **wbudowaną** usługę Microsoft Flow.  Na **liście programu SharePoint** kliknij przycisk listy rozwijanej **Przepływ**, a następnie wybierz pozycję **Utwórz przepływ**.

![Tworzenie przepływu](./media/learning-approvals/new-flow.png)   

W **menu po prawej stronie** wyszukaj **szablon** taki jak ten.

![Szablon zatwierdzenia](./media/learning-approvals/approval-template.png)

## <a name="using-the-template"></a>Korzystanie z szablonu
Wyzwalacz programu **SharePoint** w szablonie jest **wstępnie wypełniany** przy użyciu informacji z listy.  Musisz tylko dodać **adres e-mail** **osoby zatwierdzającej**.  Zauważ, że **oryginalny element programu SharePoint nie zmieni się**.  W tym celu należy dodać akcję **SharePoint — aktualizowanie elementu**.

![Aktualizowanie elementu](./media/learning-approvals/update-item.png)

A co z gałęzią **Jeśli nie** elementu *Zakres wysyłania wiadomości e-mail*?  Domyślnie nie wykonuje ona żadnych czynności.  Możesz dodać akcję, aby wysyłać do autora wiadomość o odrzuceniu jego wniosku. 

![Jeśli nie](./media/learning-approvals/if-no.png)

## <a name="next-lesson"></a>Następna lekcja
Teraz sprawdzimy, czego dowiedzieliśmy się z tej sekcji.

