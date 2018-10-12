---
title: Dodawanie przepływu pracy na żądanie do przepływu procesów biznesowych
description: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 07/12/2018
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 26c79c20-2987-476e-983a-406e0db13034
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: aa061d5e2f668e8950a6cdab89992996f64c6fe8
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689622"
---
# <a name="add-an-on-demand-workflow-to-a-business-process-flow"></a>Dodawanie przepływu pracy na żądanie do przepływu procesów biznesowych

Istnieje możliwość wyzwolenia przepływów pracy na żądanie z poziomu przepływu procesów biznesowych. Na przykład można dodać przepływ pracy na żądanie do przepływu procesów biznesowych, tak aby przy każdym zakończeniu etapu było tworzone działanie, takie jak zadanie lub wiadomość e-mail. 

Przepływ pracy jest aktywowany w oparciu o to, gdzie zostanie upuszczony przepływ pracy w projektancie przepływu procesów biznesowych.
- Procesy etapów na żądanie. Gdy przepływ pracy zostaje upuszczony na etap przepływu procesów biznesowych, przepływ pracy jest wyzwalany na początku lub na końcu etapu. 
- Globalne procesy na żądanie. Gdy przepływ pracy zostaje upuszczony na obszar **Globalne przepływy pracy**, przepływ pracy jest wyzwalany przy aktywacji procesu lub archiwizowaniu procesu (podczas przejścia do stanu „zastosowany”, „zakończony”, „ponownie aktywowany” lub „porzucony”). 

Podczas dodawania przepływu pracy do przepływu procesów biznesowych należy zwrócić uwagę na następujące wymagania.
- W przypadku przepływów pracy dodanych do etapu: można używać tylko aktywnych przepływów pracy na żądanie utworzonych dla tej samej jednostki etapu, gdzie dodano przepływ pracy.  
- W przypadku globalnych przepływów pracy: można używać tylko aktywnych przepływów pracy na żądanie utworzonych dla podstawowej jednostki przepływu procesów biznesowych.

## <a name="add-an-on-demand-workflow-to-a-business-process-flow-stage"></a>Dodawanie przepływu pracy na żądanie do etapu przepływu procesów biznesowych

Przepływ pracy na żądanie można dodać w projektancie przepływu procesów biznesowych, przeciągając składnik przepływu pracy do etapu procesu lub sekcji globalnych przepływów pracy. 

W witrynie [PowerApps](https://web.powerapps.com) wybierz pozycję **Oparty na modelu** (lewa dolna część okienka nawigacji). 

Otwórz projektanta przepływu procesów biznesowych. Można to zrobić na dwa sposoby.
- Jeśli przepływ procesów biznesowych został już dodany do aplikacji, przejdź do strony **Aplikacje**, następnie do aplikacji, którą chcesz wybrać **...**, a na koniec wybierz pozycję **Edytuj**. W projektancie aplikacji wybierz przepływ procesów biznesowych, a następnie wybierz pozycję ![Otwórz projektanta przepływu procesów biznesowych](media/dynamics365-open-designer.PNG).  
- W przeciwnym razie otwórz [eksplorator rozwiązań](/powerapps/maker/model-driven-apps/advanced-navigation.md#solution-explorer), w okienku nawigacji po lewej stronie wybierz pozycję **Procesy**, a następnie wybierz żądany przepływ procesów biznesowych. 

Zdecyduj, czy chcesz, aby przepływ pracy na żądanie był wyzwalany przez jedno z następujących zdarzeń przepływu procesów biznesowych. 
- Procesy etapów na żądanie. Wyzwala przepływ pracy na początku lub na końcu etapu. 
- Globalne procesy na żądanie. Wyzwala przepływ pracy przy aktywacji procesu lub archiwizowaniu procesu (podczas przejścia do stanu „stosowany”, „zakończony”, „ponownie aktywowany” lub „porzucony”). 

W poniższym przykładzie przepływ pracy na żądanie o nazwie **Mój przepływ pracy na żądanie** jest dodawany do **Etapu 1** przepływu procesów biznesowych. 

1. Rozwiń etap 1, aby wyświetlić sekcję **Wyzwolony proces**. 
2. Wybierz kartę **Składniki**, a następnie przeciągnij składnik **Przepływ pracy** do sekcji **Wyzwolony proces**.
    ![Dodawanie przepływu pracy do etapu](media/add-workflow-to-bpf-1.png) Ewentualnie możesz przeciągnąć składnik **Przepływ pracy** do sekcji **Globalne przepływy pracy**, która wyzwala przepływ pracy przy aktywacji lub archiwizacji procesu.
 ![Dodawanie przepływu pracy do aktywacji lub archiwizacji procesu](media/add-workflow-to-bpf-global.png)
3. W polu wyszukiwania karty **Właściwości** wprowadź i wyszukaj nazwę przepływu pracy na żądanie, który chcesz dodać do etapu przepływu procesów biznesowych, a następnie wybierz polecenie **Zastosuj**.
    ![Wprowadzanie nazwy i wybór polecenia Zastosuj](media/add-workflow-to-bpf-2.png)
4. Na karcie **Właściwości** w obszarze **Wyzwalacz** wybierz opcję **Rozpoczęcie etapu** lub **Zakończenie etapu**.  
    ![Wybór wyzwalacza przepływu pracy](media/workflow-trigger.png)
   
    Ewentualnie po upuszczeniu przepływu pracy w sekcji **Globalne przepływy pracy** dostępne są następujące opcje wyzwalacza: **Proces zastosowany**, **Proces aktywowany ponownie**, **Proces porzucony** i **Proces zakończony**.

5. Wybierz pozycję **Aktualizuj** na pasku narzędzi projektanta przepływu procesów biznesowych.
 
## <a name="next-steps"></a>Następne kroki
[Używanie procesów przepływu pracy do automatyzowania procesów, które nie wymagają interakcji użytkownika](workflow-processes.md) <br/>
[Samouczek: tworzenie przepływu procesów biznesowych umożliwiającego standaryzowanie procesów](create-business-process-flow.md) <br/>
[Automatyzacja przepływu procesów biznesowych w usłudze Dynamics 365](https://blogs.msdn.microsoft.com/crm/2017/03/28/business-process-flow-automation-in-dynamics-365/)
