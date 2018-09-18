---
title: Uruchamianie przepływów za pomocą przycisków Flic | Microsoft Docs
description: Łatwe uruchamianie przepływów za pomocą przycisków fizycznych Flic firmy Shortcut Labs.
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
ms.date: 05/19/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: bbcb6c8950e8ac5959880727604e0355b3150c6f
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690485"
---
# <a name="run-your-flows-by-pressing-a-flic-smart-button-preview"></a>Uruchamianie przepływów przez naciśnięcie przycisku inteligentnego Flic (wersja zapoznawcza)
Wyzwalaj przepływy, naciskając przycisk fizyczny Flic firmy Shortcut Labs. Przez naciśnięcie przycisku Flic możesz na przykład śledzić godziny pracy, zablokować kalendarz, policzyć gości na imprezie lub zapisać lokalizacje geograficzne.

> [!IMPORTANT]
> Wszystkie właściwości przycisku Flic konfiguruje się przed utworzeniem przepływu przy użyciu aplikacji mobilnej Flic dla systemu [Android](https://play.google.com/store/apps/details?id=io.flic.app) lub [iOS](https://itunes.apple.com/us/app/flic-app/id977593793?ls=1&mt=8).
> 
> 

## <a name="prerequisites"></a>Wymagania wstępne
Aby móc korzystać z przycisków Flic w usłudze Microsoft Flow, konieczne jest spełnienie następujących wymagań:

* Należy mieć dostęp do usługi [Microsoft Flow](https://flow.microsoft.com).
* Należy pobrać aplikację mobilną Flic dla systemu [Android](https://play.google.com/store/apps/details?id=io.flic.app) lub [iOS](https://itunes.apple.com/us/app/flic-app/id977593793?ls=1&mt=8) i zestawić ją w parę z co najmniej jednym przyciskiem Flic.

## <a name="configure-flic-properties"></a>Konfigurowanie właściwości przycisku Flic
Użyj aplikacji mobilnej Flic, aby zaprogramować zdarzenia przycisku Flic. Dostępne są następujące zdarzenia:

* Kliknięcie (jedno szybkie naciśnięcie)
* Dwukrotne kliknięcie (dwa szybkie naciśnięcia)
* Przytrzymanie (jedno długie naciśnięcie)

Na tym zrzucie ekranu pokazano przykład procesu konfiguracji przycisku Flic:

![konfigurowanie przycisków Flic](./media/flic-button-flows/configure-flic-actions.png)

Po połączeniu zdarzenia przycisku Flic z usługą Microsoft Flow można wybrać ten przycisk Flic jako wyzwalacz przepływów. Wyzwalacze będą wybierane w dalszej części tego przewodnika.

## <a name="create-a-flow-thats-triggered-by-a-flic"></a>Tworzenie przepływu wyzwalanego przez przycisk Flic
W tym przewodniku przycisk Flic jest używany do uruchomienia przepływu rejestrującego czas obsługi poszczególnych klientów przez konsultanta. Konsultant naciska przycisk Flic raz po przybyciu do klienta, a następnie naciska go ponownie tuż przed opuszczeniem klienta. Każde naciśnięcie przycisku Flic uruchamia przebieg przepływu, z którym jest połączony. Przepływ zapisuje bieżący czas w Arkuszach Google, a następnie wysyła powiadomienie e-mail. W wiadomości e-mail znajdują się szczegółowe informacje o przebiegu przepływu.

Uwaga: Należy pamiętać o użyciu aplikacji mobilnej Flic do zestawienia w parę i skonfigurowania co najmniej jednej akcji **kliknięcia** w celu wyzwolenia usługi Microsoft Flow. Na tym zrzucie ekranu skonfigurowano akcję **kliknięcia** do wyzwolenia usługi Microsoft Flow. W dalszej części tego przewodnika przepływ zostanie skonfigurowany w taki sposób, aby był wyzwalany po jednokrotnym naciśnięciu (kliknięciu) przycisku Flic.

   ![konfigurowanie przycisku Flic](./media/flic-button-flows/flic-configured-for-flow.png)

Rozpocznijmy tworzenie przepływu.

### <a name="start-with-a-template"></a>Rozpoczynanie od szablonu
1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com).
   
    ![logowanie](./media/flic-button-flows/sign-into-flow.png)
2. Na pasku wyszukiwania wpisz **flic**, a następnie wybierz ikonę wyszukiwania.
   
    ![wyszukiwanie ciągu flic](./media/flic-button-flows/search-flic.png)
3. Wybierz szablon **Track your working hours with Flic smart button** (Śledzenie godzin pracy za pomocą przycisku inteligentnego Flic).
   
    ![wybieranie szablonu](./media/flic-button-flows/flic-templates.png)

### <a name="create-a-spreadsheet-in-google-sheets"></a>Tworzenie arkusza kalkulacyjnego w Arkuszach Google
1. Przejrzyj szczegóły szablonu i zauważ, że ten szablon wymaga arkusza kalkulacyjnego w Arkuszach Google.
   
   ![przeglądanie szczegółów szablonu](./media/flic-button-flows/flic-template-details.png)
2. W Arkuszach Google utwórz arkusz kalkulacyjny zawierający arkusz z kolumnami o nazwie **ClickType** i **TimeStamp**.
   
      Porada: Aby nazwać kolumny w Arkuszach Google, wprowadź nazwę kolumny w jej górnej części. Arkusz powinien więc wyglądać podobnie jak na tym zrzucie ekranu:
   
   ![Arkusz Google](./media/flic-button-flows/flic-google-sheet.png)
   
   Uwaga: Ten arkusz zostanie użyty dalszej części tego przewodnika.

### <a name="add-the-flic-trigger-to-your-flow"></a>Dodawanie wyzwalacza przycisku Flic do przepływu
1. Zaloguj się do usługi szablonu, a następnie wybierz pozycję **Kontynuuj**.
   
     Pozycja **Kontynuuj** zostanie włączona po zalogowaniu do wszystkich wymaganych usług dla szablonu.
   
    ![podawanie poświadczeń](./media/flic-button-flows/flic-template-services-sign-in.png)
2. Wprowadź ciąg **flic** do pola wyszukiwania, a następnie wybierz wyzwalacz **Flic - When a Flic is pressed** (Flic — po naciśnięciu przycisku Flic).
   
    ![wyszukiwanie wyzwalacza przycisku flic](./media/flic-button-flows/flic-search-trigger.png)
3. Wybierz przycisk Flic, którego chcesz użyć, z listy **Flic button** (Przycisk Flic) na karcie **Flic - When a Flic is pressed** (Flic — po naciśnięciu przycisku Flic).
4. Wybierz pozycję **click** (kliknięcie) z listy **Events** (Zdarzenia), aby wskazać, że chcesz wyzwolić przepływ po jednokrotnym naciśnięciu przycisku Flic.
   
    ![wybieranie akcji przycisku flic](./media/flic-button-flows/select-flic.png)
   
   Opcjonalnie można wybrać pozycję **any** (dowolny), aby wskazać, że każde zdarzenie przycisku Flic (kliknięcie, dwukrotne kliknięcie lub przytrzymanie) ma wyzwolić przepływ.
   
   Pozycja **double-click** (dwukrotne kliknięcie) wskazuje, że przepływ zostanie wyzwolony po szybkim dwukrotnym naciśnięciu przycisku Flic. Pozycja **hold** (przytrzymanie) wskazuje, że przepływ zostanie wyzwolony po długim naciśnięciu przycisku Flic.
   
   Możesz utworzyć inne przepływy i wyzwalać je za pomocą innych zdarzeń z listy **Events** (Zdarzenia). Na przykład możesz użyć zdarzenia **double-click** (dwukrotne kliknięcie) do zarejestrowania czasu opuszczenia klienta.

### <a name="configure-the-sheet"></a>Konfigurowanie arkusza
   Na karcie **Insert row** (Wstawianie wiersza):

1. Z listy **File** (Plik) wybierz utworzony wcześniej arkusz kalkulacyjny.
2. Z listy **Worksheet** (Arkusz) wybierz arkusz.
   
   Uwaga: Po wybraniu arkusza na karcie **Insert row** (Wstawianie wiersza) zostaną wyświetlone dwa dodatkowe pola. Te pola reprezentują dwie kolumny utworzonego wcześniej arkusza.
3. Wybierz pole **ClickType**, a następnie wybierz token **Click type** (Rodzaj kliknięcia).
4. Wybierz pole **Timestamp**, a następnie wybierz token **Click time** (Czas kliknięcia).
   
    ![konfigurowanie danych z Arkuszy Google](./media/flic-button-flows/flick-insert-row-card.png)

### <a name="confirm-the-email-settings-are-correct"></a>Potwierdzanie poprawności ustawień adresu e-mail
1. Sprawdź, czy karta **Send me an email notification** (Wysyłanie powiadomienia e-mail) wygląda podobnie do tego zrzutu ekranu.
   
    ![potwierdzanie powiadomienia e-mail](./media/flic-button-flows/email-settings.png)

### <a name="save-your-flow-and-test-it"></a>Zapisywanie przepływu i jego testowanie
1. Nadaj nazwę przepływowi i zapisz go.
   
    ![zapisywanie przepływu](./media/flic-button-flows/save.png)

Po wykonaniu opisanych czynności jednokrotne naciśnięcie przycisku Flic wyzwoli przepływ. Przepływ rejestruje rodzaj kliknięcia i bieżący czas w arkuszu, a następnie wysyła do Ciebie wiadomość e-mail.

1. Naciśnij jeden raz przycisk Flic.
2. Otwórz swój arkusz w Arkuszach Google. W kolumnie **ClickType** powinna znajdować się wartość „click” (kliknięcie), a w kolumnie **Timestamp** godzina zdarzenia.
   
    ![wyświetlanie wyników przebiegu](./media/flic-button-flows/flic-google-sheet-after-run.png)
3. Wyniki przebiegu można również wyświetlić w witrynie internetowej usługi Microsoft Flow lub w aplikacji mobilnej Microsoft Flow. Oto zrzut ekranu mojego przebiegu testowego.
   
    ![zapisywanie przepływu](./media/flic-button-flows/flic-test-run-results-portal.png)
4. Oto przykładowa treść powiadomienia e-mail otrzymanego w wyniku uruchomienia przepływu.
   
    ![zapisywanie przepływu](./media/flic-button-flows/flic-email-body.png)

Jako dodatkowe ćwiczenie można rozważyć rozszerzenie przepływu w taki sposób, aby automatycznie rejestrował lokalizację (współrzędne geograficzne) po naciśnięciu przycisku Flic.

## <a name="more-information"></a>Więcej informacji
* [Udostępnianie przepływów przycisków](share-buttons.md).
* Dowiedz się, jak używać [tokenów wyzwalacza przycisku](introduction-to-button-trigger-tokens.md) do wysyłania bieżących danych, gdy są wykonywane przepływy przycisku.
* Zainstaluj aplikację mobilną usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows).

