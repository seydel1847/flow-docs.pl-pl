---
title: Uruchamianie przepływów za pomocą urządzeń bttn | Microsoft Docs
description: Dowiedz się, jak uruchamiać przepływy za pomocą urządzenia bttn
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: kvivek
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/30/2017
ms.author: deonhe
ms.openlocfilehash: 3387cc29bb088348634c4d97699f56a4a69ac434
ms.sourcegitcommit: 77aae180d972373d1f251fa6a5c8f484f08ffc15
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39718217"
---
# <a name="run-your-flows-with-physical-buttons-bttns-from-the-button-corporation-preview"></a>Uruchamianie przepływów za pomocą przycisków fizycznych (urządzeń bttn) firmy The Button Corporation (wersja zapoznawcza)
Możliwe jest uruchamianie przepływów przez naciśnięcie urządzenia bttn (przycisku fizycznego wyprodukowanego przez firmę [The Button Corporation](https://my.bt.tn/)). Za pomocą naciśnięcia urządzenia bttn wyzwalającego przepływ można na przykład wykonywać następujące zadania:

* skontaktować się z pomocą techniczną przy użyciu informacji o lokalizacji
* wysłać wiadomość e-mail do zespołu
* zablokować kalendarz
* ponownie zamówić materiały eksploatacyjne

> [!IMPORTANT]
> Aby móc korzystać z urządzenia bttn w przepływie, musisz je [zarejestrować](https://my.bt.tn/).
> 
> [!TIP]
> Przed utworzeniem przepływu skonfiguruj wszystkie właściwości urządzenia bttn, takie jak nazwa, lokalizacja i adres e-mail, w [witrynie internetowej urządzenia bttn](https://my.bt.tn/).
> 
> 

Przepływ można również wyzwalać przy użyciu [przycisku fizycznego Flic](flic-button-flows.md).

## <a name="prerequisites"></a>Wymagania wstępne
* Należy mieć dostęp do usługi [Microsoft Flow](https://flow.microsoft.com).
* Należy mieć co najmniej jedno [zarejestrowane urządzenie bttn](https://my.bt.tn/).

## <a name="create-a-flow-thats-triggered-from-a-bttn"></a>Tworzenie przepływu wyzwalanego za pomocą urządzenia bttn
W tym przewodniku skorzystamy z szablonu pomocy technicznej w celu utworzenia przepływu, który można wyzwolić jednym naciśnięciem [urządzenia bttn](https://my.bt.tn/). Po uruchomieniu przepływ generuje żądanie obsługi, a następnie wysyła je do pomocy technicznej. Żądanie obsługi udostępnia działowi pomocy technicznej informacje o lokalizacji, w której jest potrzebna pomoc. W tym przewodniku pokazano, jak utworzyć ten przepływ na podstawie szablonu, ale można użyć pustego szablonu, co zapewnia pełną kontrolę nad wszystkimi aspektami przepływu.

Możesz użyć dowolnego z tych szablonów, aby szybko utworzyć przepływy dla urządzenia bttn i połączyć się między innymi z usługami Zendesk, Google i SharePoint:

![szablony urządzenia bttn](./media/bttn-button-flows/bttn-templates.png)

Porada: Na potrzeby tego przewodnika nadaj urządzeniu bttn nazwę, która reprezentuje salę konferencyjną w typowym budynku biurowym.

Ustawienia urządzenia bttn powinny wyglądać podobnie jak w tym przykładzie (z witryny internetowej bttn):

![szablony urządzenia bttn](./media/bttn-button-flows/bttn-config.png)

Teraz, gdy masz zarejestrowane i skonfigurowane urządzenie bttn, rozpocznijmy tworzenie przepływu.

### <a name="sign-in-and-select-a-template"></a>Logowanie się i wybieranie szablonu
1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com).
   
    ![logowanie](./media/bttn-button-flows/sign-into-flow.png)
   
    Uwaga: alternatywnie możesz tworzyć przepływy w aplikacji mobilnej usługi Microsoft Flow dla systemów [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) i [Windows Phone](https://aka.ms/flowmobilewindows).
2. W polu wyszukiwania wpisz ciąg **bttn**, a następnie wybierz ikonę wyszukiwania.
   
    ![wyszukiwanie](./media/bttn-button-flows/bttn-search-template.png)
   
    Po wybraniu ikony wyszukiwania zostaną wyświetlone wszystkie szablony, których można używać z urządzeniami bttn.
3. Wybierz szablon **Use Bttn to call technical support for meeting room** (Użyj urządzenia bttn do skontaktowania się z pomocą techniczną dla sali konferencyjnej).
   
    ![szablon pomocy technicznej](./media/bttn-button-flows/bttn-select-template.png)

### <a name="authorize-microsoft-flow-to-connect-to-your-bttn"></a>Autoryzowanie usługi Microsoft Flow do nawiązywania połączenia z urządzeniem bttn
1. Jeśli zostanie wyświetlony monit, zaloguj się do usługi bttn i usługi Office 365 Outlook, co spowoduje włączenie przycisku **Kontynuuj**.
   
    ![poświadczenia](./media/bttn-button-flows/bttn-provide-credentials.png)
2. Po zalogowaniu się w usłudze bttn autoryzuj usługę Microsoft Flow do korzystania z urządzeń bttn.
   
    **Ważne**: jeśli usługa Microsoft Flow nie zostanie autoryzowana do korzystania z urządzeń bttn, nie będzie ich można wyświetlić ani nawiązać z nimi połączenia z poziomu usługi Microsoft Flow.
   
    ![autoryzacja](./media/bttn-button-flows/authorize-bttn.png)
3. Po zalogowaniu się do obu usług wybierz przycisk **Kontynuuj**.
   
    ![Kontynuuj](./media/bttn-button-flows/continue.png)

### <a name="select-the-bttn-that-triggers-the-flow"></a>Wybieranie urządzenia bttn wyzwalającego przepływ
1. Na karcie **Po naciśnięciu urządzenia bttn** otwórz listę identyfikatorów urządzeń bttn, a następnie wybierz urządzenie bttn, którego chcesz używać.
   
    ![wybieranie urządzenia bttn](./media/bttn-button-flows/bttn-id.png)
   
    Przepływ powinien teraz wyglądać podobnie do przedstawionego w tym przykładzie.
   
    ![przegląd przepływu](./media/bttn-button-flows/bttn-done.png)
2. Określ nazwę przepływu, a następnie wybierz pozycję **Utwórz przepływ**, aby go zapisać.
   
    ![zapisywanie przepływu](./media/bttn-button-flows/save.png)

## <a name="test-your-flow-and-confirm-results"></a>Testowanie przepływu i sprawdzanie wyników
1. Naciśnij przycisk na urządzeniu bttn.
2. Wyświetl historię przebiegów przepływu, aby upewnić się, że został uruchomiony pomyślnie.
   
    Historię przebiegów możesz sprawdzić w witrynie internetowej usługi Microsoft Flow lub na swoim urządzeniu przenośnym.
   
    Uwaga: stan przebiegu jest ustawiony na **uruchomiono**, dopóki ktoś nie wybierze przycisku **Potwierdzenie** w wiadomości e-mail z żądaniem obsługi.
3. Można również potwierdzić, że wiadomość e-mail została wysłana do zespołu pomocy technicznej.
   
    Po wykonaniu tych czynności przepływ powinien wyglądać podobnie do przedstawionego w poniższym przykładzie:
   
    ![](./media/bttn-button-flows/support-request-email.png)

## <a name="troubleshooting"></a>Rozwiązywanie problemów
* Jeśli przepływ nie został wywołany, zaloguj się do witryny firmy The Button Corporation i upewnij się, że działanie przycisku (naciśnięcia) jest rejestrowane.
* Możesz także przejść do działania przebiegu w witrynie usługi Microsoft Flow i sprawdzić komunikaty o błędach.

## <a name="more-information"></a>Więcej informacji
* [Udostępnianie przepływów przycisków](share-buttons.md).
* Dowiedz się, jak używać [tokenów wyzwalacza przycisku](introduction-to-button-trigger-tokens.md) do wysyłania bieżących danych, gdy są uruchamiane przepływy przycisku.
* [Instalowanie aplikacji Microsoft Flow dla systemu Android](https://aka.ms/flowmobiledocsandroid).
* [Instalowanie aplikacji Microsoft Flow dla systemu iOS](https://aka.ms/flowmobiledocsios).

