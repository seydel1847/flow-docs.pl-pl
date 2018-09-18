---
title: Tworzenie przepływu na telefonie | Microsoft Docs
description: Utwórz przepływ na podstawie szablonu, który, na przykład, wysyła powiadomienie wypychane po otrzymaniu wiadomości e-mail z określonego adresu
services: ''
suite: flow
documentationcenter: na
author: adiregev
manager: erikre
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/18/2016
ms.author: adiregev
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: f87320c61427957c02ff75675e4e15b938ac99f4
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688334"
---
# <a name="create-a-flow-from-your-phone-by-using-microsoft-flow"></a>Tworzenie przepływu na telefonie przy użyciu usługi Microsoft Flow
Utwórz przepływ na telefonie za pomocą szablonu, który można znaleźć, przeszukując listę usług, przeglądając kategorie lub określając słowa kluczowe. Wykonaj instrukcje zawarte w tym temacie, aby utworzyć przepływ wysyłający powiadomienie wypychane na telefon po otrzymaniu wiadomości e-mail od kierownika.

Jeśli nie znasz usługi Microsoft Flow, [zapoznaj się z omówieniem](getting-started.md).

## <a name="prerequisites"></a>Wymagania wstępne
* [Konto usługi Microsoft Flow](sign-up-sign-in.md).
* Aplikacja mobilna usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows) na [obsługiwanym urządzeniu](getting-started.md#use-the-mobile-app). Grafiki w tym temacie przedstawiają wersję aplikacji dla telefonu iPhone, ale interfejs na urządzeniu z systemem Android lub Windows Phone jest podobny.
* Aby użyć szablonu przedstawionego w tym temacie, wymagane są również:
  
  * Poświadczenia usługi Office 365.
  * Powiadomienia wypychane włączone na telefonie.

## <a name="find-a-template"></a>Znajdowanie szablonu
1. Otwórz aplikację mobilną, a następnie naciśnij przycisk **Przeglądaj** u dołu ekranu.
   
    ![Ikona Przeglądaj](./media/mobile-create-flow/browse-icon.png)
   
    Szablon można znaleźć w jeden z następujących sposobów:
   
   * W polu wyszukiwania w górnej części ekranu określ słowo kluczowe.
   * Naciśnij opcję na liście usług.
   * Przewiń w dół w celu wyświetlenia różnych kategorii, a następnie naciśnij szablon w dowolnej kategorii.
     
       ![Karta Przeglądanie](./media/mobile-create-flow/browse-tab.png)
     
     W tym samouczku otworzysz szablon wysyłający powiadomienie wypychane po otrzymaniu wiadomości e-mail od kierownika.
2. Na liście usług naciśnij pozycję **Zobacz wszystkie**.
   
    ![Wyświetlanie listy usług](./media/mobile-create-flow/list-services.png)
3. Naciśnij ikonę **Powiadomienie wypychane**.
   
    ![Powiadomienia wypychane](./media/mobile-create-flow/push-notifications.png)
4. Na pasku wyszukiwania wpisz ciąg **e-mail**, a następnie naciśnij szablon, aby wysłać powiadomienie wypychane po otrzymaniu wiadomości od kierownika.
   
    ![Wybieranie szablonu](./media/mobile-create-flow/choose-template.png)
5. Na ekranie zawierającym szczegóły dotyczące wybranego szablonu naciśnij pozycję **Użyj tego szablonu**.
   
    ![Potwierdzanie szablonu](./media/mobile-create-flow/confirm-template.png)

## <a name="finish-the-flow"></a>Kończenie przepływu
1. Jeśli zostanie wyświetlony monit, naciśnij przycisk **Zaloguj** i podaj swoje poświadczenia usługi Office 365 Outlook i/lub użytkowników usługi Office 365.
   
    ![Logowanie do usługi Office 365](./media/mobile-create-flow/office-signin.png)
   
    Podczas tworzenia innych przepływów możesz użyć tych samych połączeń.
2. W prawym górnym rogu naciśnij przycisk **Dalej**.
   
    ![Naciskanie przycisku Dalej](./media/mobile-create-flow/next.png)
   
    Następny ekran pokazuje zdarzenie wyzwalacza i wszystkie akcje wynikowe.
   
    ![Zdarzenie wyzwalacza i akcje](./media/mobile-create-flow/flow-structure.png)
   
    W przypadku tego szablonu nowa wiadomość e-mail wyzwala przepływ pobierający informacje (łącznie z adresem kierownika) i wysyłający do Ciebie powiadomienie wypychane po otrzymaniu wiadomości e-mail z tego adresu. Niektóre szablony wymagają dostosowania, aby działały poprawnie, ale ten szablon nie.
3. (opcjonalnie) W pobliżu górnej części ekranu wpisz inną nazwę przepływu.
   
    ![Zmienianie nazwy przepływu](./media/mobile-create-flow/rename-flow.png)
4. W prawym górnym rogu naciśnij przycisk **Utwórz**.
   
    ![Tworzenie przepływu](./media/mobile-create-flow/create-flow.png)
   
    Przepływ zostanie utworzony i będzie oczekiwać na wiadomości e-mail od Twojego kierownika do chwili jego wstrzymania lub usunięcia.

## <a name="next-steps"></a>Następne kroki
* [Monitor your flow activity](mobile-monitor-activity.md) (Monitorowanie działań przepływu).
* [Manage your flows](mobile-manage-flows.md) (Zarządzanie przepływami).

