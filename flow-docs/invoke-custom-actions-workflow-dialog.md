---
title: Wywoływanie akcji niestandardowych z przepływu pracy | MicrosoftDocs
description: Informacje na temat wywoływania akcji niestandardowej z przepływu pracy
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 1fd5d39e-3dc8-4d1a-8b4b-ccaa303f4bbb
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 8b2904632f4b3bf097275906d917e686cace67ba
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688524"
---
# <a name="invoke-custom-actions-from-a-workflow"></a>Wywoływanie akcji niestandardowych z przepływu pracy

Przepływy pracy mają wiele możliwości obsługi scenariuszy biznesowych. Wywoływanie w ramach przepływu pracy podstawowych akcji zestawu SDK dla rekordu, takich jak tworzenie, aktualizacja i usuwanie, pozwala obsłużyć sporą liczbę scenariuszy biznesowych. Jeśli jednak połączysz możliwości przepływów pracy z mocą akcji niestandardowych wywoływanych bezpośrednio z poziomu przepływu pracy, dodajesz do swojej aplikacji cały szereg nowych scenariuszy biznesowych bez konieczności pisania kodu.  
  
 Przyjrzyjmy się scenariuszowi, w którym akcja niestandardowa jest wywoływana z przepływu pracy. Wywołamy akcję niestandardową polegającą na żądaniu zgody menedżera, gdy zniżka dla konkretnej szansy sprzedaży przekroczy 20%.  
  
<a name="action"></a>   
## <a name="dynamics-365-customer-engagement-example-create-a-custom-action-using-the-opportunity-entity"></a>Przykład z usługi Dynamics 365 Customer Engagement: tworzenie akcji niestandardowej przy użyciu jednostki szansy sprzedaży
  
1. W [eksploratorze rozwiązań](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer) wybierz pozycję **Procesy**.  
  
2.  Na pasku nawigacji wybierz pozycję **Nowy**. Nadaj procesowi nazwę, a następnie wybierz kategorię **Akcja**.  
  
 Aby zażądać zatwierdzenia rabatu, użyjemy akcji niestandardowej o nazwie **Proces zatwierdzania**. Dodaliśmy parametr wejściowy **SpecialNotes** i krok **Wyślij wiadomość e-mail**, aby utworzyć nową wiadomość i wysłać żądanie zatwierdzenia przez menedżera, jak pokazano poniżej.  
  
 ![Dodawanie kroku &#45; Wyślij wiadomość e-mail](media/enable-custom-action-approval-proces-sadd-email.png "Dodawanie kroku — Wyślij wiadomość e-mail")  
  
 Aby skonfigurować wiadomość e-mail, wybierz pozycję **Ustaw właściwości**. Po otwarciu formularza użyj **Asystenta formularzy**, aby dodać specjalne uwagi i inne informacje do wiadomości e-mail, jak wyróżniono na zrzucie ekranu. Aby dodać specjalne uwagi, umieść kursor w miejscu, gdzie mają być widoczne w wiadomości, w **Asystencie formularzy** w obszarze **Szukaj** z pierwszej listy rozwijanej wybierz pozycję **Argumenty**, z drugiej listy rozwijanej wybierz pozycję **SpecialNotes**, a następnie wybierz przycisk **OK**.  
  
 ![Konfigurowanie wiadomości e-mail](media/enable-custom-action-approval-process-setup-email.png "Konfigurowanie wiadomości e-mail")  
  
 Zanim będzie możliwe wywołanie akcji z przepływu pracy, trzeba ją aktywować. Po aktywowaniu akcji można wyświetlić jej właściwości, wybierając pozycję **Wyświetl właściwości**.  
  
 ![Aktywowanie akcji niestandardowej &#45; proces zatwierdzania](media/enable-custom-action-approval-process-activate-action.png "Aktywowanie akcji niestandardowej — proces zatwierdzania")  
  
<a name="workflow"></a>   
## <a name="invoke-a-custom-action-from-a-workflow"></a>Wywoływanie akcji niestandardowej z przepływu pracy  
  
1. W [eksploratorze rozwiązań](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer) wybierz pozycję **Procesy**.   
  
2.  Na pasku nawigacji wybierz pozycję **Nowy**. Nadaj procesowi nazwę, a następnie wybierz kategorię **Przepływ pracy**.  
  
 Został utworzony przepływ pracy, który wywołuje akcję niestandardową **Proces zatwierdzania** zawsze wtedy, gdy wymagana jest zgoda menedżera na przyznanie zniżki w wysokości ponad 20% dla szansy sprzedaży.  
  
 ![Ustawianie właściwości akcji z przepływu pracy](media/enable-custom-action-from-workflow.png "Ustawianie właściwości akcji z przepływu pracy")  
  
 Właściwości wejściowe akcji można ustawić, wybierając pozycję **Ustaw właściwości**. Dodaliśmy nazwę konta związanego z szansą sprzedaży w specjalnych uwagach. W **Asystencie formularzy** w obszarze **Szukaj** z pierwszej listy rozwijanej wybierz pozycję **Konta**, z drugiej listy rozwijanej wybierz **Nazwa konta**, a następnie wybierz przycisk **OK**. Właściwość **docelowa** jest wymagana i jest wypełniana przez system. Element **{Opportunity(Opportunity)}** we właściwości **docelowej** jest tą samą szansą sprzedaży, na której działa wywołujący przepływ pracy. Ewentualnie możesz wybrać konkretną szansę sprzedaży dla właściwości docelowej przy użyciu wyszukiwania.  
  
 ![Ustawianie parametrów wejściowych dla akcji ApprovalProcess](media/enable-customaction-workflow-set-properties.png "Ustawianie parametrów wejściowych dla akcji ApprovalProcess")  
  



