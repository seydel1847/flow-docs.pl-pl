---
title: Usługa Common Data Service | Microsoft Docs
description: Utwórz przepływ w celu importowania danych, eksportowania danych lub budowania zatwierdzeń przy użyciu usługi Common Data Service.
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
ms.date: 10/22/2016
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: b2cf6c52a2cbaf06fc638fe8fc898689e6d523c4
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690837"
---
# <a name="create-a-flow-that-uses-the-common-data-service"></a>Tworzenie przepływu, który używa usługi Common Data Service
Popraw wydajność operacyjną za pomocą ujednoliconego widoku danych biznesowych, tworząc przepływ, który używa usługi [Common Data Service](https://powerapps.microsoft.com/tutorials/data-platform-intro/). Wdróż w swojej organizacji tę bezpieczną biznesową bazę danych, która obejmuje dobrze sformułowane jednostki biznesowe, takie jak Sales (Dział sprzedaży), Purchase (Dział zakupów), Customer Service (Dział obsługi klienta) i Productivity (Dział produktywności). Przechowuj dane organizacyjne w co najmniej jednej [jednostce niestandardowej](https://powerapps.microsoft.com/tutorials/data-platform-create-entity/), które mają kilka zalet w porównaniu z zewnętrznymi źródłami danych, takimi jak program Microsoft Excel i usługa Salesforce.

Oto przykłady wykorzystania usługi Common Data Service w usłudze Microsoft Flow:

* Utwórz przepływ, aby importować dane, eksportować dane lub wykonać działania względem tych danych (takie jak wysyłanie powiadomień). Pamiętaj, że takie podejście nie jest równoważne z pełną synchronizacją — po prostu umożliwia przenoszenie danych do pojedynczych jednostek i poza nie.
  
    Aby uzyskać szczegółowy opis kroków, zapoznaj się z procedurami w dalszej części tego tematu.
* Zamiast [tworzyć pętlę zatwierdzania za pośrednictwem poczty e-mail](wait-for-approvals.md), utwórz przepływ, który zapisuje stan zatwierdzenia w jednostce, a następnie utwórz aplikację niestandardową, w której użytkownicy będą mogli zatwierdzać lub odrzucać elementy.
  
    Aby uzyskać szczegółowy opis kroków, zobacz temat [Tworzenie pętli zatwierdzania za pomocą usługi Common Data Service](common-data-model-approve.md).

**Wymagania wstępne**

* Zarejestruj się w programie [Microsoft Flow](https://flow.microsoft.com) oraz w usłudze [PowerApps](https://web.powerapps.com).
  
    Jeśli masz problemy, sprawdź, czy program [Microsoft Flow](sign-up-sign-in.md) i usługa [PowerApps](https://powerapps.microsoft.com/tutorials/signup-for-powerapps/) obsługuje typ konta, którego używasz, a Twoja organizacja nie zablokowała rejestrowania się.
* Jeśli usługa Common Data Service nie była jeszcze używana, otwórz kartę **Jednostki** w witrynie [powerapps.com](https://web.powerapps.com/#/entities), a następnie kliknij lub naciśnij pozycję **Utwórz moją bazę danych**.

## <a name="sign-in-to-your-environment"></a>Logowanie się do środowiska
1. Otwórz [portal Microsoft Flow](https://flow.microsoft.com), a następnie kliknij lub naciśnij przycisk **Zaloguj** w prawym górnym rogu.
   
    **Uwaga**: w celu wyświetlenia przycisku **Zaloguj** może być konieczne otwarcie menu w lewym górnym rogu.
   
    ![Logowanie](./media/common-data-model-intro/signin-flow.png)
2. W prawym górnym menu wybierz środowisko, w którym utworzono bazę danych w witrynie powerapps.com.
   
    **Uwaga**: jeśli nie zostanie wybrane to samo środowisko, odpowiednie jednostki nie będą widoczne.
   
    ![Wybieranie środowiska](./media/common-data-model-intro/select-environment.png)

## <a name="open-a-template"></a>Otwieranie szablonu
1. Do pola **Wyszukaj szablony** u góry ekranu wpisz lub wklej słowo **common**, a następnie naciśnij klawisz Enter.
   
    ![Wyszukiwanie szablonów](./media/common-data-model-intro/template-search.png)
2. Na liście szablonów kliknij lub naciśnij szablon, który importuje dane z żądanego źródła do jednostki (lub *obiektu*).
   
    Na przykład kliknij lub naciśnij szablon, który kopiuje informacje o kontaktach z usługi Dynamics 365 do usługi Common Data Service.
   
    ![Wybieranie szablonu](./media/common-data-model-intro/choose-template.png)
3. Kliknij lub naciśnij pozycję **Użyj tego szablonu**.
   
    ![Używanie szablonu](./media/common-data-model-intro/use-template.png)
4. Jeśli połączenie z usługi Microsoft Flow do usługi Dynamics 365 nie zostało jeszcze utworzone, kliknij lub naciśnij pozycję **Zaloguj**, a następnie podaj swoje poświadczenia (jeśli pojawi się monit).
   
    ![Logowanie do usługi Dynamics 365](./media/common-data-model-intro/dynamics-signin.png)
5. Kliknij lub naciśnij pozycję **Kontynuuj**.
   
    ![Potwierdzanie kont](./media/common-data-model-intro/confirm-accounts.png)

## <a name="build-your-flow"></a>Budowanie przepływu
1. Na pierwszej karcie określ zdarzenie, które wyzwoli przepływ.
   
    Można na przykład zbudować przepływ, który skopiuje nowe kontakty z wystąpienia programu Dynamics 365 do usługi Common Data Service. W obszarze **When a record is created** (Kiedy tworzony jest rekord) określ wystąpienie, klikając lub naciskając strzałkę w dół, a następnie kliknij lub naciśnij opcję na wyświetlonej liście.
   
    ![Określenie wystąpienia programu Dynamics 365](./media/common-data-model-intro/specify-instance.png)
2. (opcjonalnie) W pobliżu górnej części ekranu podaj inną nazwę dla tworzonego przepływu.
   
    **Uwaga**: jeśli okno przeglądarki nie jest zmaksymalizowane, interfejs użytkownika może wyglądać trochę inaczej.
   
    ![Nazywanie przepływu](./media/common-data-model-intro/name-flow.png)
3. Kliknij lub naciśnij pozycję **Utwórz przepływ**.
   
    **Uwaga**: jeśli okno przeglądarki nie jest zmaksymalizowane, możliwe, że widoczny będzie tylko znacznik wyboru.
   
    ![Tworzenie przepływu](./media/common-data-model-intro/create-flow.png)

Od teraz za każdym razem, gdy ten obiekt zostanie utworzony w systemie źródłowym, zostanie on zaimportowany do usługi Common Data Service. Jeśli nie można odnaleźć szablonu, który wykonuje potrzebne operacje, możesz [od podstaw utworzyć przepływ](get-started-logic-flow.md), który będzie wykonywał operacje względem usługi Common Data Service.

Po wystąpieniu zmian w bazie danych mogą być wykonywane określone akcje. Na przykład można wysyłać wiadomość e-mail z powiadomieniem przy każdorazowej zmianie danych.

