---
title: Tworzenie nowoczesnego przepływu pracy zatwierdzania z wieloma osobami zatwierdzającymi | Microsoft Docs
description: 'Tworzenie nowoczesnego przepływu pracy zatwierdzania z wieloma osobami zatwierdzającymi '
services: ''
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/08/2017
ms.author: deonhe
ms.openlocfilehash: 8620cd49f9e19f6641909fcab3103568d148e565
ms.sourcegitcommit: f0202f74ba9a2282a670a1751462f598a5ea0ce5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="manage-sequential-approvals-with-microsoft-flow"></a>Zarządzanie zatwierdzeniami sekwencyjnymi za pomocą usługi Microsoft Flow
Niektóre przepływy pracy wymagają wstępnego zatwierdzenia, zanim będzie wymagane zatwierdzenie przez osobę ostatecznie zatwierdzającą. Firma może mieć na przykład zasady zatwierdzania sekwencyjnego, które wymagają wstępnego zatwierdzenia faktur powyżej 1000,00 zł przed zatwierdzeniem przez dział finansowy.

W ramach tego przewodnika zostanie utworzony przepływ zatwierdzania sekwencyjnego, który zarządza wnioskami urlopowymi pracowników.

## <a name="detailed-steps-in-the-flow"></a>Szczegółowy opis kroków przepływu
Przepływ:

1. Przepływ rozpoczyna się w wyniku utworzenia przez pracownika wniosku urlopowego na [liście usługi SharePoint Online](https://support.office.com/article/Introduction-to-lists-0a1c3ace-def0-44af-b225-cfa8d92c52d7).
2. Wniosek urlopowy zostaje dodany do centrum zatwierdzania, a następnie wysłany w wiadomości e-mail do osoby wstępnie zatwierdzającej.
3. Decyzja o wstępnym zatwierdzeniu zostaje przesłana w wiadomości e-mail do pracownika.
4. Lista usługi SharePoint Online zostaje zaktualizowana o decyzję i komentarze osoby wstępnie zatwierdzającej.
   
   Uwaga: jeśli wniosek został wstępnie zatwierdzony, przepływ kontynuuje działanie, wykonując poniższe kroki:
5. Wniosek jest wysyłany do osoby ostatecznie zatwierdzającej.
6. Ostateczna decyzja zostaje przesłana w wiadomości e-mail do pracownika.
7. Lista programu SharePoint zostaje zaktualizowana o ostateczną decyzję.

Ten obraz zawiera podsumowanie powyższych kroków:

   ![diagram programu visio przepływu](./media/sequential-modern-approvals/visio-overview.png)

## <a name="prerequisites"></a>Wymagania wstępne
[!INCLUDE [prerequisites-for-modern-approvals](includes/prerequisites-for-modern-approvals.md)]

Na utworzonej liście usługi SharePoint Online muszą znajdować się następujące kolumny:

   ![Kolumny listy programu SharePoint](./media/sequential-modern-approvals/sharepoint-columns.png)

Zanotuj nazwę i adres URL listy usługi SharePoint Online. Te informacje będą potrzebne później, podczas konfigurowania wyzwalacza **SharePoint — Po utworzeniu nowego elementu**.

## <a name="create-your-flow-from-the-blank-template"></a>Tworzenie przepływu na podstawie pustego szablonu
[!INCLUDE [sign-in-and-create-flow-from-blank-template](includes/sign-in-and-create-flow-from-blank-template.md)]

## <a name="add-a-trigger"></a>Dodawanie wyzwalacza
[!INCLUDE [add-trigger-when-sharepoint-item-created](includes/add-trigger-when-sharepoint-item-created.md)]

   ![informacje programu sharepoint](./media/sequential-modern-approvals/select-sharepoint-site-info.png)

## <a name="get-the-manager-for-the-person-who-created-the-vacation-request"></a>Pobieranie menedżera osoby, która utworzyła wniosek urlopowy
[!INCLUDE [add-get-manager-action](includes/add-get-manager-action.md)]

1. Nadaj nazwę przepływowi, a następnie wybierz pozycję **Utwórz przepływ**, aby zapisać wyniki dotychczasowej pracy.
   
    ![zapisywanie przepływu](./media/sequential-modern-approvals/save.png)
   
   > [!NOTE]
   > Co jakiś czas wybierz pozycję **Aktualizuj przepływ** znajdującą się u góry ekranu, aby zapisać zmiany w przepływie.
   > 
   > 
   
    ![wybieranie akcji aktualizacji](./media/sequential-modern-approvals/update.png)

Po każdej operacji zapisywania wybierz pozycję **Edytuj przepływ** u góry ekranu, a następnie kontynuuj wprowadzanie zmian.

## <a name="add-an-approval-action-for-pre-approvals"></a>Dodawanie akcji zatwierdzenia dla wstępnych zatwierdzeń
[!INCLUDE [add-an-approval-action](includes/add-an-approval-action.md)]

Uwaga: ta akcja spowoduje wysłanie żądania wstępnego zatwierdzenia na adres e-mail podany w polu **Przypisano do**.

## <a name="add-a-condition"></a>Dodawanie warunku
[!INCLUDE [add-approval-condition-response](includes/add-approval-condition-response.md)]

> [!NOTE]
> Ten warunek sprawdza odpowiedź z akcji **Rozpocznij zatwierdzenie**.
> 
> 

## <a name="add-an-email-action-for-pre-approvals"></a>Dodawanie akcji poczty e-mail dla wstępnych zatwierdzeń
[!INCLUDE [add-action-to-send-email-when-vacation-approved](includes/add-action-to-send-email-when-vacation-approved.md)]

   ![konfigurowanie szablonu wiadomości e-mail informującej o wstępnym zatwierdzeniu](./media/sequential-modern-approvals/yes-email-config.png)

## <a name="add-an-update-action-for-pre-approved-requests"></a>Dodawanie akcji aktualizacji dla wstępnie zatwierdzonych wniosków
[!INCLUDE [add-action-to-update-sharepoint-with-approval](includes/add-action-to-update-sharepoint-with-approval.md)]

   ![konfigurowanie aktualizacji elementu](./media/sequential-modern-approvals/configure-update-item.png)

## <a name="get-the-pre-approvers-manager"></a>Pobieranie menedżera osoby wstępnie zatwierdzającej
1. Skorzystaj z kroków procedury [Pobieranie menedżera osoby, która utworzyła wniosek urlopowy](sequential-modern-approvals.md#get-the-manager-for-the-person-who-created-the-vacation-request), które były wykonywane wcześniej, aby dodać, a następnie skonfigurować kolejną akcję **Pobierz menedżera**. Tym razem zostanie pobrany menedżer osoby wstępnie zatwierdzającej.
2. Po zakończeniu karta **Pobierz menedżera 2** powinna przypominać przedstawioną na tej ilustracji. Należy użyć tokenu **Adres e-mail** z kategorii **Pobierz menedżera** na karcie **Dodaj zawartość dynamiczną z aplikacji i usług używanych w tym przepływie**.
   
   ![pobieranie menedżera osoby wstępnie zatwierdzającej](includes/media/modern-approvals/get-pre-approver-manager.png)

## <a name="add-the-final-approval-action"></a>Dodawanie akcji ostatecznego zatwierdzenia
1. Skorzystaj z kroków procedury [Dodawanie akcji zatwierdzenia dla wstępnych zatwierdzeń](sequential-modern-approvals.md#add-an-approval-action-for-pre-approvals), które były wykonywane wcześniej, aby dodać, a następnie skonfigurować kolejną akcję **Rozpocznij zatwierdzenie**. Ta akcja spowoduje wysłanie wiadomości e-mail z żądaniem ostatecznego zatwierdzenia.
2. Po zakończeniu karta powinna wyglądać podobnie jak na tej ilustracji:
   
    ![konfigurowanie zatwierdzenia](./media/sequential-modern-approvals/provide-approval-config-info.png)

## <a name="add-the-final-approval-condition"></a>Dodawanie warunku ostatecznego zatwierdzenia
1. Powtórz kroki procedury [dodawanie warunku](sequential-modern-approvals.md#add-a-condition), aby dodać, a następnie skonfigurować **Warunek**, który sprawdza decyzję osoby ostatecznie zatwierdzającej.

## <a name="send-email-with-final-approval"></a>Wysyłanie wiadomości e-mail z ostatecznym zatwierdzeniem
1. Skorzystaj z procedury [Dodawanie akcji poczty e-mail dla wstępnych zatwierdzeń](sequential-modern-approvals.md#add-an-email-action-for-pre-approvals), aby dodać, a następnie skonfigurować akcję, która spowoduje wysłanie wiadomości e-mail po zatwierdzeniu wniosku urlopowego.
2. Po zakończeniu karta powinna przypominać przedstawioną na tej ilustracji:
   
   ![szablon wiadomości e-mail z ostatecznym zatwierdzeniem](./media/sequential-modern-approvals/vacatioin-request-approved-email-template.png)

## <a name="update-sharepoint-with-approval"></a>Aktualizowanie programu SharePoint przy użyciu zatwierdzenia
1. Skorzystaj z procedury [Dodawanie akcji aktualizacji dla wstępnie zatwierdzonych wniosków](sequential-modern-approvals.md#add-an-update-action-for-pre-approved-requests), aby dodać, a następnie skonfigurować akcję, która spowoduje zaktualizowanie programu SharePoint po zatwierdzeniu wniosku urlopowego.
2. Po zakończeniu karta powinna wyglądać podobnie jak na poniższej ilustracji:
   
    ![konfigurowanie aktualizacji elementu](./media/sequential-modern-approvals/configure-update-item-approved.png)

## <a name="send-email-with-pre-approval-rejection"></a>Wysyłanie wiadomości e-mail z odrzuceniem dla wstępnego zatwierdzania
[!INCLUDE [add-action-to-send-email-when-vacation-rejected](includes/add-action-to-send-email-when-vacation-rejected.md)]

   ![konfiguracja dla odrzuconych wniosków](./media/sequential-modern-approvals/configure-rejected-email.png)

Uwaga: ta akcja musi zostać dodana do gałęzi **JEŚLI NIE, NIC NIE RÓB** poniżej karty **Warunek**.

## <a name="update-sharepoint-with-pre-approval-rejection"></a>Aktualizowanie programu SharePoint przy użyciu odrzucenia dla wstępnego zatwierdzania
[!INCLUDE [add-action-to-update-sharepoint-with-rejection](includes/add-action-to-update-sharepoint-with-rejection.md)]

   ![aktualizowanie programu sharepoint dla odrzuconych wniosków](./media/sequential-modern-approvals/update-sharepoint-with-rejection.png)

## <a name="send-email-with-final-rejection"></a>Wysyłanie wiadomości e-mail z ostatecznym odrzuceniem
1. Skorzystaj z procedury [Wysyłanie wiadomości e-mail z odrzuceniem dla wstępnego zatwierdzania](sequential-modern-approvals.md#send-email-with-pre-approval-rejection), aby dodać, a następnie skonfigurować akcję, która spowoduje wysłanie wiadomości e-mail po odrzuceniu wniosku urlopowego przez osobę ostatecznie zatwierdzającą.
   
    Uwaga: ta akcja musi zostać dodana do gałęzi **JEŚLI NIE, NIC NIE RÓB** poniżej karty **Warunek 2**.
2. Po zakończeniu karta powinna wyglądać podobnie jak na poniższej ilustracji:
   
   ![konfiguracja dla odrzuconych wniosków](./media/sequential-modern-approvals/final-rejection-email-card.png)

## <a name="update-sharepoint-with-final-rejection"></a>Aktualizowanie programu SharePoint przy użyciu ostatecznego odrzucenia
1. Skorzystaj z procedury [Aktualizowanie programu SharePoint przy użyciu odrzucenia dla wstępnego zatwierdzania](sequential-modern-approvals.md#update-sharepoint-with-pre-approval-rejection), aby dodać, a następnie skonfigurować akcję, która spowoduje zaktualizowanie programu SharePoint, jeśli osoba ostatecznie zatwierdzająca odrzuci wniosek urlopowy.
2. Po zakończeniu karta powinna wyglądać podobnie jak na poniższej ilustracji:
   
   ![karta aktualizuj element](./media/sequential-modern-approvals/final-rejection-update-sharepoint.png)
3. Wybierz pozycję **Aktualizuj przepływ**, aby zapisać wyniki dotychczasowej pracy.
   
   ![wybieranie akcji aktualizacji](./media/sequential-modern-approvals/update.png)

Po wykonaniu tych czynności przepływ powinien wyglądać podobnie jak przedstawiony na poniższej ilustracji:

![przegląd przepływu](./media/sequential-modern-approvals/completed-flow.png)

Teraz, kiedy przepływ został utworzony, można sprawdzić, jak działa.

## <a name="request-an-approval"></a>Wysyłanie wniosku o zatwierdzenie
[!INCLUDE [request-vacation-approval](includes/request-vacation-approval.md)]

Ten wniosek powinien przypominać przedstawiony na tej ilustracji:

![wniosek urlopowy](./media/sequential-modern-approvals/vacation-request.png)

## <a name="view-pending-approval-requests"></a>Wyświetlanie żądań oczekujących na zatwierdzenie
[!INCLUDE [view-pending-approvals](includes/view-pending-approvals.md)]

## <a name="pre-approve-a-request"></a>Wstępne zatwierdzanie wniosku
[!INCLUDE [approve-request-from-different-locations](includes/approve-request-from-different-locations.md)]

## <a name="approve-the-request"></a>Zatwierdzanie wniosku
Kroki procedury zatwierdzania wniosku są takie same jak kroki procedury [Wstępne zatwierdzanie wniosku](sequential-modern-approvals.md#pre-approve-a-request)

Uwaga: osoba ostatecznie zatwierdzająca otrzyma wniosek urlopowy tylko wtedy, gdy wniosek zostanie wstępnie zatwierdzony.

## <a name="reject-a-request"></a>Odrzucanie żądania
[!INCLUDE [reject-a-request](includes/reject-a-request.md)]

## <a name="more-information"></a>Więcej informacji
[Przewodnik dotyczący nowoczesnych zatwierdzeń z jedną osobą zatwierdzającą](modern-approvals.md)

