---
title: Używanie akcji | MicrosoftDocs
description: Za pomocą akcji można wykonywać takie operacje jak tworzenie, aktualizacja, usuwanie, przypisywanie lub wykonywanie. Wewnętrznie akcja powoduje utworzenie niestandardowego komunikatu
ms.custom: ''
ms.date: 08/07/2018
ms.reviewer: ''
ms.service: flow
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1475985f-d3c4-429d-beac-cb455965e792
caps.latest.revision: 20
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: aaa1d90368cbf513b46a939e7ea512a66b2c0a14
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688961"
---
# <a name="use-actions"></a>Używanie akcji

Akcje otwierają szeroką gamę możliwości tworzenia logiki biznesowej. Za pomocą akcji można wykonywać takie operacje jak tworzenie, aktualizacja, usuwanie, przypisywanie lub wykonywanie. Wewnętrznie akcja powoduje utworzenie niestandardowego komunikatu. Deweloperzy nazywają te akcje „komunikatami”. Każdy z tych komunikatów jest oparty na akcjach dotyczących rekordu jednostki. Jeśli celem procesu jest utworzenie rekordu, następnie zaktualizowanie go, a potem przypisanie, istnieją trzy oddzielne kroki. Każdy krok jest zdefiniowany przez możliwości jednostki — niekoniecznie konkretnego procesu biznesowego.  
  
Akcje umożliwiają zdefiniowanie jednego zlecenia (lub komunikatu) odpowiadającego operacji, którą należy wykonać dla Twojej firmy. Te nowe komunikaty są sterowane przez proces lub zachowanie, a nie to, co można zrobić z jednostką. Te komunikaty mogą odpowiadać takim zleceniom jak eskalowanie, konwertowanie, harmonogram, trasa lub zatwierdzenie — czegokolwiek potrzebujesz. Dodanie tych zleceń zapewnia bardziej rozbudowany zbiór zleceń umożliwiający bezproblemowe definiowanie procesów biznesowych. Można zastosować ten bogatszy zbiór zleceń z klientów lub integracji, zamiast pisać akcje w ramach klientów. Ponadto dzięki temu jest to łatwiejsze, ponieważ możesz zarządzać i rejestrować powodzenie lub niepowodzenie całej akcji jako pojedynczej jednostki.  
  
<a name="BKMK_ConfigurableMessages"></a>   
## <a name="configurable-messages"></a>Konfigurowalne komunikaty  
 Po zdefiniowaniu i aktywowaniu akcji deweloper może użyć tego komunikatu, podobnie jak innych dowolnych komunikatów dostarczonych przez platformę. Jednak istotną różnicą jest to, że teraz nowy użytkownik, który nie jest deweloperem, może zastosować zmiany do tego, co powinno być zrobione, gdy jest używany ten komunikat. Można skonfigurować akcję do modyfikowania kroków wraz ze zmianami procesów biznesowych. Niestandardowego kodu, który używa tego komunikatu, nie trzeba zmieniać, dopóki nie zmieniają się argumenty procesu.  
  
 Procesy przepływu pracy i wtyczki w dalszym ciągu zapewniają podobne możliwości definiowania automatyzacji. Procesy przepływu pracy nadal umożliwiają użytkownikom niebędącym deweloperami stosowanie zmian. Jednak różnica polega na tym, jak powstają procesy biznesowe i jak deweloper może napisać ich kod. Akcja jest komunikatem, który działa na tym samym poziomie, co komunikaty dostarczane przez platformę. Deweloperzy mogą rejestrować wtyczki dla akcji.  
  
<a name="BKMK_GlobalMessages"></a>   
## <a name="global-messages"></a>Globalne komunikaty 
 
 W przeciwieństwie do przepływów pracy lub [wtyczek](/powerapps/developer/common-data-service/apply-business-logic-with-code?branch=master#create-a-plug-in) usługi CDS for Apps, akcja nie musi być skojarzona z określoną jednostką. Można zdefiniować akcje „globalne”, które mogą być wywoływane samodzielnie.

## <a name="next-steps"></a>Następne kroki

[Tworzenie akcji niestandardowej](create-actions.md)  
  

