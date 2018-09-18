---
title: Łatwa automatyzacja przepływów pracy zatwierdzania | Microsoft Docs
description: Zautomatyzuj przepływy pracy zatwierdzania integrowane z usługami SharePoint, Dynamics CRM, Salesforce, OneDrive dla Firm, Zendesk lub WordPress.
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
ms.date: 07/20/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 0d948cdf5bce01aa5c18955645774dbcf455ba1b
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690875"
---
# <a name="create-and-test-an-approval-workflow-with-microsoft-flow"></a>Tworzenie i testowanie przepływu pracy zatwierdzania za pomocą usługi Microsoft Flow

Dzięki usłudze Microsoft Flow możesz zarządzać zatwierdzaniem dokumentów lub procesów w kilku usługach, w tym SharePoint, Dynamics CRM, Salesforce, OneDrive dla Firm, Zendesk lub WordPress.

Aby utworzyć przepływ pracy zatwierdzania, dodaj akcję **Zatwierdzenia — Uruchom zatwierdzanie** do dowolnego przepływu. Po dodaniu tej akcji Twój przepływ może zarządzać zatwierdzaniem dokumentów i procesów. Możesz na przykład utworzyć przepływy zatwierdzania dokumentów służące do zatwierdzania faktur, zleceń pracy i ofert sprzedaży. Możesz też utworzyć przepływy zatwierdzania procesów do zatwierdzania wniosków urlopowych, pracy w nadgodzinach lub planów podróży.

Osoby zatwierdzające mogą odpowiadać na żądania z poziomu skrzynki odbiorczej poczty e-mail, [centrum zatwierdzeń](https://flow.microsoft.com/manage/approvals/received/) w witrynie internetowej usługi Microsoft Flow lub aplikacji Microsoft Flow.

## <a name="create-an-approval-flow"></a>Tworzenie przepływu zatwierdzenia
Poniżej przedstawiono omówienie przepływu, który utworzymy i przetestujemy:

   ![przegląd przepływu](./media/modern-approvals/create-flow-overview.png)

Przepływ wykonuje następujące kroki:

1. Przepływ rozpoczyna się w wyniku utworzenia przez kogoś wniosku urlopowego na liście usługi SharePoint Online.
2. Wniosek urlopowy zostaje dodany do centrum zatwierdzania, a następnie wysłany w wiadomości e-mail do osoby zatwierdzającej.
3. Decyzja osoby zatwierdzającej zostaje wysłana w wiadomości e-mail do osoby, która wnioskowała o urlop.
4. Lista usługi SharePoint Online zostaje zaktualizowana o komentarze osoby zatwierdzającej do decyzji.

## <a name="prerequisites"></a>Wymagania wstępne
Aby wykonać czynności przedstawione w tym przewodniku, musisz mieć dostęp do tych zasobów:

[!INCLUDE [prerequisites-for-modern-approvals](includes/prerequisites-for-modern-approvals.md)]

Utwórz następujące kolumny na liście usługi SharePoint Online:

   ![Kolumny na liście w usłudze SharePoint Online](./media/modern-approvals/sharepoint-list-fields.png)

Zanotuj nazwę i adres URL listy usługi SharePoint Online. Te informacje będą potrzebne później, podczas konfigurowania wyzwalacza **SharePoint — Po utworzeniu elementu**.

## <a name="create-your-flow-from-the-blank-template"></a>Tworzenie przepływu na podstawie pustego szablonu
[!INCLUDE [sign-in-and-create-flow-from-blank-template](includes/sign-in-and-create-flow-from-blank-template.md)]

## <a name="add-a-trigger"></a>Dodawanie wyzwalacza

[!INCLUDE [add-trigger-when-sharepoint-item-created](includes/add-trigger-when-sharepoint-item-created.md)]

Ustawienia **Adres witryny** i **Nazwa listy** to informacje zanotowane we wcześniejszej części tego przewodnika.

![Informacje programu SharePoint](./media/modern-approvals/select-sharepoint-site-info.png)

## <a name="add-a-profile-action"></a>Dodawanie akcji profilu

1. Wybierz pozycję **Nowy krok**, a następnie wybierz pozycję **Dodaj akcję**.
   
    ![nowy krok](./media/modern-approvals/select-sharepoint-add-action.png)
2. Wprowadź tekst **profil** w polu wyszukiwania **Wybierz akcję**.
   
    ![wyszukiwanie profilu](./media/modern-approvals/search-for-profile.png)
3. Znajdź, a następnie wybierz akcję **Użytkownicy usługi Office 365 — Pobierz mój profil**.
   
    ![wybieranie użytkowników pakietu office](./media/modern-approvals/select-my-profile.png)
4. Nadaj nazwę przepływowi, a następnie wybierz pozycję **Utwórz przepływ**, aby zapisać wyniki dotychczasowej pracy.
   
    ![zapisywanie przepływu](./media/modern-approvals/save.png)

## <a name="add-an-approval-action"></a>Dodawanie akcji zatwierdzenia

[!INCLUDE [add-an-approval-action](includes/add-an-approval-action.md)]

> [!NOTE]
> Ta akcja spowoduje wysłanie żądania zatwierdzenia na adres e-mail podany w polu **Przypisano do**.
>
>

## <a name="add-a-condition"></a>Dodawanie warunku

[!INCLUDE [add-approval-condition-response](includes/add-approval-condition-response.md)]

## <a name="add-an-email-action-for-approvals"></a>Dodawanie akcji poczty e-mail dla zatwierdzeń

Wykonaj następujące czynności, aby wysłać wiadomość e-mail, jeśli wniosek urlopowy zostanie zatwierdzony:

[!INCLUDE [add-action-to-send-email-when-vacation-approved](includes/add-action-to-send-email-when-vacation-approved.md)]

   ![konfigurowanie szablonu wiadomości e-mail informującej o zatwierdzeniu](./media/sequential-modern-approvals/yes-email-config.png)

## <a name="add-an-update-action-for-approved-requests"></a>Dodawanie akcji aktualizacji dla zatwierdzonych wniosków

[!INCLUDE [add-action-to-update-sharepoint-with-approval](includes/add-action-to-update-sharepoint-with-approval.md)]

> [!NOTE]
> Pola **Adres witryny**, **Nazwa listy**, **Identyfikator** i **Tytuł** są wymagane.
>
>

![konfigurowanie aktualizacji elementu](./media/modern-approvals/configure-update-item.png)

## <a name="add-an-email-action-for-rejections"></a>Dodawanie akcji poczty e-mail dla odrzuceń

[!INCLUDE [add-action-to-send-email-when-vacation-rejected](includes/add-action-to-send-email-when-vacation-rejected.md)]

![konfiguracja dla odrzuconych wniosków](./media/modern-approvals/configure-rejected-email.png)

## <a name="add-update-action-for-rejected-requests"></a>Dodawanie akcji aktualizacji dla odrzuconych wniosków

[!INCLUDE [add-action-to-update-sharepoint-with-rejection](includes/add-action-to-update-sharepoint-with-rejection.md)]

   > [!NOTE]
   > Pola **Adres witryny**, **Nazwa listy**, **Identyfikator** i **Tytuł** są wymagane.
   >
   >

![karta aktualizuj element](./media/modern-approvals/configure-update-item-no.png)

1. Wybierz pozycję **Aktualizuj przepływ**, aby zapisać wyniki dotychczasowej pracy.
   
    ![wybieranie akcji aktualizacji](./media/modern-approvals/update.png)

Po wykonaniu tych czynności przepływ powinien wyglądać podobnie do przedstawionego na poniższym zrzucie ekranu:

![przegląd przepływu](./media/modern-approvals/completed-flow.png)

Po utworzeniu przepływu należy go przetestować.

## <a name="request-an-approval"></a>Wysyłanie wniosku o zatwierdzenie

[!INCLUDE [request-vacation-approval](includes/request-vacation-approval.md)]

Teraz, po utworzeniu i przetestowaniu przepływu, pamiętaj, aby poinstruować innych, jak z niego korzystać.

## <a name="learn-more"></a>Dowiedz się więcej

* Wyświetlanie [oczekujących żądań zatwierdzenia](approve-reject-requests.md) i zarządzanie nimi
* Utwórz [sekwencyjne przepływy zatwierdzania.](sequential-modern-approvals.md)
* Utwórz [równoległe przepływy zatwierdzania.](parallel-modern-approvals.md)
* Zainstaluj aplikację mobilną usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows).
