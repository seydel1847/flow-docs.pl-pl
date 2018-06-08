---
title: Udostępnianie przycisków innym osobom | Microsoft Docs
description: Udostępnij przyciski innym osobom, aby mogły z nich skorzystać i oszczędzić czas.
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/21/2017
ms.author: deonhe
ms.openlocfilehash: 2804c683defb94f87c40452a27382bc143c11f10
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "23442264"
---
# <a name="share-button-flows-in-microsoft-flow"></a>Udostępnianie przepływów przycisków w usłudze Microsoft Flow
W aplikacji mobilnej Microsoft Flow możesz udostępniać [przepływy przycisków](introduction-to-button-flows.md) (przyciski) innym użytkownikom lub grupom w swojej organizacji. Po udostępnieniu przycisku osoba lub grupa, której go udostępnisz, może uruchamiać Twój przycisk w taki sam sposób, jak własne przyciski. Możesz również [udostępnić link](share-buttons.md#re-share-a-button) do przycisków, które udostępniła Ci inna osoba. W dowolnym momencie możesz [zatrzymać udostępnianie](share-buttons.md#stop-sharing-a-button) przycisków.

> Zrzuty ekranu użyte w niniejszym dokumencie zostały pobrane z urządzenia z systemem Android. Jeśli używasz telefonu iPhone, obrazy mogą wyglądać inaczej, ale funkcjonalność jest taka sama.
> 
> 

Wykonaj [te kroki](share-buttons.md#use-shared-buttons), aby skorzystać z przycisku udostępnionego przez inną osobę.

## <a name="prerequisites"></a>Wymagania wstępne
Aby udostępnić przyciski, potrzebne są następujące elementy:

* Konto z dostępem do usługi [Microsoft Flow](https://flow.microsoft.com).
* Przepływ do udostępnienia.
* Urządzenie przenośne z aplikacją mobilną usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows).
* Grupa lub użytkownik w Twojej organizacji, którym ma zostać udostępniony przycisk.

## <a name="share-a-button"></a>Udostępnianie przycisku
Przycisk możesz udostępnić na karcie **Przyciski** w aplikacji mobilnej usługi Microsoft Flow.

1. Naciśnij małą ikonę obok przycisku, który chcesz udostępnić.
   
    ![udostępnianie przycisku](./media/share-buttons/share-button-flows-buttons-tab.png)
2. Naciśnij pozycję **Zaproś innych** na stronie **Użytkownicy przycisku**.
   
    ![udostępnianie przycisku](./media/share-buttons/share-button-flows-button-users.png)
3. Wyszukaj, a następnie wybierz grupę lub osobę, której chcesz udostępnić przycisk.
   
    ![udostępnianie przycisku](./media/share-buttons/share-button-flows-invite-others-select.png)
4. Naciśnij pozycję **WYŚLIJ** na stronie **Zapraszanie innych**.
   
    ![udostępnianie przycisku](./media/share-buttons/share-button-flows-invite-others-send.png)
5. Naciśnij pozycję **GOTOWE** na stronie informującej o pomyślnym zakończeniu operacji udostępniania przycisku.
   
    ![udostępnianie przycisku](./media/share-buttons/share-button-flows-invite-others-done.png)

## <a name="require-users-to-use-their-own-connections"></a>Wymaganie od użytkowników korzystania z własnych połączeń
> [!NOTE]
> Po udostępnieniu przycisku możesz zezwolić osobom, którym został on udostępniony, na używanie wszystkich połączeń używanych przez przycisk. Możesz także wymagać od nich, aby używały własnych połączeń. Jeśli zezwolisz innym użytkownikom na używanie Twoich połączeń, nie będą oni mogli uzyskać dostępu do poświadczeń w Twoim połączeniu ani użyć ich ponownie w innym przepływie.
> 
> 

Wykonaj następujące kroki, aby od osób, którym udostępniono przyciski, wymagać używania ich własnych połączeń.

1. Na ekranie wyświetlanym natychmiast po udostępnieniu przycisku wybierz pozycję **ZARZĄDZAJ POŁĄCZENIAMI**
2. Wybierz polecenie **EDYTUJ** dla przycisku, którym chcesz zarządzać.
3. Wybierz pozycję **Udostępniony przez użytkownika** lub swój adres e-mail.
   
    Twój wybór wskazuje, czyje połączenia mają być używane w udostępnionym przycisku.
   
    ![udostępnianie przycisku](./media/share-buttons/share-button-select-connection-provided-by-user.png)
   
    W dowolnym momencie możesz wyświetlić lub zmienić wybór. W tym celu wybierz kartę **Przepływy**, udostępniony przez siebie przepływ, pozycję **Użytkownicy i połączenia**, kartę **POŁĄCZENIA** i polecenie **EDYTUJ** dla przycisku, którym chcesz zarządzać.
   
    ![udostępnianie przycisku](./media/share-buttons/share-button-flows-conn-provided-by-user.png)

## <a name="view-the-list-of-button-users"></a>Wyświetlanie listy użytkowników przycisku
Wykonując następujące kroki na karcie **Przyciski**, możesz wyświetlić wszystkie grupy i wszystkich użytkowników, którym udostępniono przycisk:

1. Naciśnij małą ikonę obok przycisku, który Cię interesuje.
2. Na stronie **Użytkownicy przycisku** przejrzyj wszystkie grupy i wszystkich użytkowników, którym udostępniono przycisk.
   
    ![Wyświetlanie użytkowników przycisku](./media/share-buttons/share-button-flows-button-users-list.png)

## <a name="stop-sharing-a-button"></a>Zatrzymywanie udostępniania przycisku
Aby zatrzymać udostępnianie przycisku, wykonaj następujące kroki na karcie **Przyciski**:

1. Naciśnij małą ikonę obok przycisku, którego nie chcesz już udostępniać.
2. Na stronie **Użytkownicy przycisku** naciśnij użytkownika lub grupę, którym przycisk nie ma być już udostępniany.
   
    ![Zatrzymywanie udostępniania przycisku](./media/share-buttons/share-button-flows-remove-user-list.png)
3. Po wyświetleniu strony użytkownika naciśnij pozycję **Usuń użytkownika**.
   
    ![Zatrzymywanie udostępniania przycisku](./media/share-buttons/share-button-flows-remove-user.png)
4. Poczekaj na zakończenie operacji usuwania. Zwróć uwagę, że lista **Użytkownicy przycisku** zostanie odświeżona i usuniętego użytkownika lub grupy nie będzie już na liście.
   
    ![Zatrzymywanie udostępniania przycisku](./media/share-buttons/share-button-flows-remove-user-result.png)

## <a name="monitor-the-run-history"></a>Monitorowanie historii przebiegów
Cała historia przebiegów, obejmująca przebiegi zainicjowane przez osobę, której przycisk został udostępniony, jest widoczna tylko na karcie **Działanie** w aplikacji mobilnej usługi Microsoft Flow twórcy przycisku.

## <a name="use-shared-buttons"></a>Korzystanie z udostępnionych przycisków
Przed uruchomieniem przycisku udostępnionego przez inną osobę musisz dodać go do karty **Przyciski** z poziomu strony **Dodawanie przycisków**.

1. Naciśnij pozycję **UZYSKAJ WIĘCEJ** (lub baner **Są dostępne nowe przyciski**, jeśli jest wyświetlany) na karcie **Przyciski**.
   
    ![nowy przycisk udostępniony mnie](./media/share-buttons/share-button-flows-banner.png)
2. Naciśnij przycisk, którego chcesz użyć.
   
    Naciśnięty przycisk zostanie natychmiast dodany do karty **Przyciski** aplikacji Microsoft Flow. Możesz wtedy używać przycisku z karty **Przyciski** tak samo jak wszystkich innych widocznych na niej przycisków.
   
    ![nowy przycisk udostępniony mnie](./media/share-buttons/share-button-flows-buttons-shared-with-me.png)

## <a name="re-share-a-button"></a>Ponowne udostępnianie przycisku
Udostępnić możesz link do przycisku, który został udostępniony Tobie.

1. Wybierz pozycję **...** obok przycisku, który chcesz udostępnić.
2. Wybierz polecenie **Udostępnij link do przycisku**.
   
    ![ponowne udostępnianie linku do przycisku](./media/share-buttons/re-share-button.png)
3. Wybierz aplikację, której chcesz użyć do udostępnienia przycisku, a następnie wykonaj kroki, aby wysłać przycisk do osoby, której chcesz go udostępnić.

## <a name="stop-using-a-shared-button"></a>Kończenie korzystania z udostępnionego przycisku
Jeśli nie chcesz już korzystać z udostępnionego Ci przycisku, usuń go z karty **Przyciski**, wykonując następujące kroki:

1. Na karcie **Przyciski** naciśnij pozycję **...** obok przycisku, którego nie chcesz już używać.
   
    ![Usuwanie przycisku](./media/share-buttons/share-button-flows-added-shared-button.png)
2. Naciśnij pozycję **Usuń** w wyświetlonym menu.

To wszystko. Przycisk nie jest już wyświetlany na karcie **Przyciski** w aplikacji Microsoft Flow.

> [!NOTE]
> Usunięty udostępniony przycisk możesz dodać ponownie, wybierając pozycję **UZYSKAJ WIĘCEJ** na karcie **Przyciski**.
> 
> 

