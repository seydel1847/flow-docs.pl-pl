---
title: Tworzenie przepływu zadań dla urządzeń przenośnych za pomocą usługi PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 046480e6-f2ff-4c56-9e03-f642c982ff7d
caps.latest.revision: 12
author: Mattp123
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: ba48fe37c0effe75f5dafec5e62a39ae21758c10
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689760"
---
# <a name="create-a-mobile-task-flow"></a>Tworzenie przepływu zadań dla urządzeń przenośnych

Zaprojektuj przepływ w usłudze Dynamics 365 dla telefonów lub Dynamics 365 dla tabletów w oparciu o typowe zadania wykonywane przez użytkowników. Przepływ zadań możesz na przykład utworzyć, gdy użytkownicy muszą po spotkaniach z klientami regularnie wykonywać szereg kolejnych czynności. Gdy użytkownicy nacisną nowe zadanie w aplikacji mobilnej, przeprowadzi ich ono przez cały proces, od początku do końca, nie zapomną więc o żadnym ważnym kroku.  
  
 Przepływy zadań mogą wykorzystywać logikę i formularze z wieloma jednostkami, a także mogą mieć logikę formularza działającą na różnych stronach przepływu zadań.  
  
## <a name="create-a-task-flow"></a>Tworzenie przepływu zadań
  
1. Upewnij się, że masz rolę zabezpieczeń Administrator systemu lub Konfigurator systemu albo równoważne uprawnienia. Jeśli używasz usługi Dynamics 365 Customer Engagement, przepływy zadań dla urządzeń przenośnych mogą też tworzyć osoby z rolami Menedżer, Wiceprezes lub Prezes zarządu. 
  
2. Otwórz [eksploratora rozwiązań](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer) i wybierz pozycję **Procesy**.  
  
3.  Na pasku narzędzi **Akcje** wybierz pozycję **Nowa**.  
  
4.  W oknie dialogowym **Tworzenie procesu** wypełnij wymagane pola:  
  
    -   Wprowadź nazwę procesu.  
  
    -   Na liście **Kategoria** wybierz pozycję **Przepływ procesów biznesowych**.  
  
    -   Z listy **Jednostka** wybierz żądaną jednostkę.  
  
5.  Wybierz opcję **Uruchom proces jako przepływ zadań (online dla urządzeń przenośnych)**.  
  
6.  Wybierz przycisk **OK**.
  
     W nowym oknie zostanie otwarty projektant przepływu zadań.  
  
     ![Okno projektanta przepływu zadań](media/task-flow-designer-window.png "Okno projektanta przepływu zadań") 
  
7.  Jeśli użytkownicy będą przechodzić z jednej strony do drugiej w kolejności, przeciągnij składnik **Strony** z karty **Składniki** po prawej stronie ekranu i upuść go na znak + w odpowiednim miejscu. Aby dodać nazwę strony, wybierz stronę, wybierz kartę **Właściwości**, wpisz nową nazwę, a następnie wybierz polecenie **Zastosuj**.  
  
8.  Aby dodać gałąź do przepływu zadań, przeciągnij składnik **Warunek** z karty **Składniki** i upuść go na znak + w odpowiednim miejscu. Aby ustawić właściwości warunku, wybierz warunek, ustaw właściwości na karcie **Właściwości**, a następnie wybierz polecenie **Zastosuj**.  
  
    > [!NOTE]
    >  W miarę dodawania stron i warunków do przepływu zadań zobaczysz minimapę w lewym dolnym rogu okna, która zawiera wszystkie strony i warunki przepływu zadań.  
  
9. Aby dodać pole, etykietę lub etykietę sekcji do strony, przeciągnij składnik **Pole**, **Etykieta** lub **Etykieta sekcji** z karty **Składniki** na odpowiednią stronę. Aby zmienić właściwości jednego z tych elementów, wybierz element, ustaw właściwości na karcie **Właściwości**, a następnie wybierz polecenie **Zastosuj**.  
  
10. Aby zweryfikować przepływ zadań, wybierz pozycję **Weryfikuj** na pasku akcji.  
  
11. Aby zapisać proces jako wersję roboczą, wybierz polecenie **Zapisz** w górnej części ekranu. (Tak długo, jak proces jest w wersji roboczej, inne osoby nie mogą z niego korzystać).  
  
12. Aby aktywować przepływ zadań, tak aby mogły go używać inne osoby, wybierz polecenie **Aktywuj**.  
  
> [!TIP]
>  Oto garść porad, o których warto pamiętać podczas pracy nad przepływem zadań w oknie projektanta:  
>   
> -  Aby zrobić migawkę wszystkich elementów widocznych w oknie przepływu zadań, wybierz pozycję **Migawka** na pasku akcji.  
> -  Aby połączyć prawidłowy składnik z innym prawidłowym składnikiem w projektancie, wybierz pozycję **Łącznik** na pasku akcji.  
> -  Możesz powiększać lub pomniejszać obrazy na ekranie, wybierając przycisk **Zwiększ poziom powiększenia** lub **Zmniejsz poziom powiększenia** w prawym górnym rogu ekranu. Wybierz przycisk **Dopasuj do kanwy**, aby powiększyć obrazy do największego rozmiaru, który mieści się na ekranie.  
  
## <a name="next-steps"></a>Następne kroki  
 [Tworzenie przepływu procesów biznesowych](create-business-process-flow.md)   

