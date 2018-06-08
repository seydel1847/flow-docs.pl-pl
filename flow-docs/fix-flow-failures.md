---
title: Rozwiązywanie problemów z przepływem | Microsoft Docs
description: Usuwanie najczęstszych przyczyn, dla których przepływy kończą się niepowodzeniem
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/17/2017
ms.author: stepsic
ms.openlocfilehash: 7f4e41437fa19f58c08e2ecd1fb65a3a30092ef8
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "23439546"
---
# <a name="troubleshooting-a-flow"></a>Rozwiązywanie problemów z przepływem
## <a name="identify-the-error"></a>Identyfikowanie błędu
Zanim będzie można naprawić przepływ, musisz ustalić przyczynę niepowodzenia. Kliknij lub naciśnij ikonę powiadomień w górnej części portalu sieci Web (lub otwórz kartę **Działanie** w aplikacji mobilnej), a następnie kliknij lub naciśnij przepływ na wyświetlonej liście.

![Powiadomienia](./media/fix-flow-failures/notifications-toolbar.png)

Zostaną wyświetlone szczegółowe informacje na temat przepływu, a co najmniej jeden krok będzie oznaczony ikoną czerwonego wykrzyknika. Otwórz ten krok i zapoznaj się z komunikatem o błędzie.

![Komunikat o błędzie](./media/fix-flow-failures/flow-run-failure.png)

## <a name="authentication-failures"></a>Błędy uwierzytelniania
W wielu przypadkach przyczyną niepowodzenia przepływów jest błąd uwierzytelniania. Jeśli wystąpi tego typu błąd, komunikat o błędzie będzie zawierać ciąg **Brak autoryzacji** bądź zostanie wyświetlony kod błędu **401** lub **403**. Błąd uwierzytelniania można zazwyczaj naprawić, aktualizując połączenie:

1. W górnej części portalu sieci Web kliknij lub naciśnij ikonę koła zębatego, aby otworzyć menu **Ustawienia**, a następnie kliknij lub naciśnij pozycję **Połączenia**.
2. Przewiń do połączenia, dla którego wystąpił komunikat o błędzie **Brak autoryzacji**.
3. Obok połączenia kliknij lub naciśnij link **Weryfikuj hasło**, który znajduje się w komunikacie o nieuwierzytelnionym połączeniu.
4. Zweryfikuj swoje poświadczenia, postępując zgodnie z wyświetlonymi instrukcjami, wróć do zakończonego niepowodzeniem przebiegu przepływu, a następnie kliknij lub naciśnij pozycję **Prześlij ponownie**.
   
    Teraz przepływ powinien działać zgodnie z oczekiwaniami.

## <a name="action-configuration"></a>Konfiguracja akcji
Przepływy mogą również zakończyć się niepowodzeniem, jeśli ustawienie akcji przepływu nie działa zgodnie z oczekiwaniami. W takim przypadku komunikat o błędzie zawiera ciąg **Nieprawidłowe żądanie** lub **Nie znaleziono** bądź zostaje wyświetlony kod błędu **400** lub **404**.

Komunikat o błędzie powinien również określać sposób naprawy błędu. Kliknij lub naciśnij przycisk **Edytuj**, a następnie rozwiąż problem w definicji przepływu. Zapisz zaktualizowany przepływ, a następnie kliknij lub naciśnij pozycję **Prześlij ponownie**, aby ponowić próbę uruchomienia z użyciem zaktualizowanej konfiguracji.

## <a name="other-failures"></a>Inne błędy
Wyświetlenie kodu błędu **500** lub **502** oznacza, że błąd jest tymczasowy lub przejściowy. Kliknij przycisk **Prześlij ponownie**, aby ponownie spróbować uruchomić przepływ.

Jeśli wystąpi inny problem, [zadaj pytanie naszej społeczności](https://go.microsoft.com/fwlink/?LinkID=787467), ponieważ podobny problem mógł dotyczyć innych użytkowników.

