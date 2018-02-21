---
title: "Tworzenie przepływu zatwierdzania wymagającego zatwierdzenia przez wszystkich użytkowników | Microsoft Docs"
description: "Utwórz przepływ zatwierdzania, który wymaga, aby wszystkie osoby zatwierdzające wyraziły zgodę lub jedna osoba odrzuciła żądanie."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/22/2017
ms.author: deonhe
ms.openlocfilehash: 6b152f0ec85558889970db2784fe8c2dcbf526ed
ms.sourcegitcommit: f3261717768177e03e825c0dd2e3ba736dc9b94d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2018
---
# <a name="create-an-approval-flow-that-requires-everyone-to-approve"></a>Tworzenie przepływu zatwierdzania wymagającego zatwierdzenia przez wszystkich użytkowników
W tym przewodniku przedstawiono sposób tworzenia przepływu pracy zatwierdzania, który wymaga, aby wszyscy (wszystkie przypisane osoby zatwierdzające) wyrazili zgodę na zatwierdzenie wniosku urlopowego i który może zostać w całości odrzucony przez jedną z osób zatwierdzających.

Ten rodzaj przepływu pracy zatwierdzania przydaje się w organizacji, w której do zatwierdzenia wniosku urlopowego wymaga się zgody zarówno menedżera danej osoby, jak i menedżera tego menedżera. Jednak każdy z menedżerów może odrzucić wniosek bez udziału drugiego.

## <a name="prerequisites"></a>Wymagania wstępne
* Dostęp do usług [Microsoft Flow](https://flow.microsoft.com), Office 365 Outlook oraz Użytkownicy usługi Office 365.
* [Lista](https://support.office.com/article/SharePoint-lists-I-An-introduction-f11cd5fe-bc87-4f9e-9bfe-bbd87a22a194) usługi SharePoint Online.
  
    W tym przewodniku przyjęto założenie, że utworzono już listę usługi SharePoint Online, która służy do tworzenia wniosków urlopowych. Zobacz przewodnik dotyczący [zatwierdzania równoległego](parallel-modern-approvals.md), aby dogłębnie zapoznać się ze szczegółowym przykładem tego, jak może wyglądać lista programu SharePoint.
* Znajomość podstaw tworzenia przepływów.
  
    Możesz przejrzeć informacje na temat dodawania [akcji, wyzwalaczy](multi-step-logic-flow.md#add-another-action) i [warunków](add-condition.md). W następujących krokach założono, że wiesz, jak wykonywać te akcje.

> [!NOTE]
> Mimo że w tym przewodniku używane są usługi SharePoint Online i Office 365 Outlook, można użyć innych usług, takich jak Zendesk, Salesforce, Gmail lub każdej z ponad [150 usług](https://flow.microsoft.com/connectors/) obsługiwanych przez usługę Microsoft Flow.
> 
> 

## <a name="create-the-flow"></a>Tworzenie przepływu
> [!NOTE]
> Jeśli wcześniej nie utworzono połączenia z programem SharePoint lub usługą Office 365, po pojawieniu się instrukcji postępuj zgodnie z nimi, aby się zalogować.
> 
> 

W tym przewodniku używane są tokeny. Aby wyświetlić listę tokenów, naciśnij lub kliknij dowolną kontrolkę wejściową, a następnie wyszukaj token na liście **zawartości dynamicznej**, która zostanie otwarta.

Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com), a następnie wykonaj następujące kroki, aby utworzyć przepływ.

1. Wybierz kolejno pozycje **Moje przepływy** > **Utwórz z pustego**.
2. Dodaj wyzwalacz **SharePoint — Po utworzeniu lub zmodyfikowaniu elementu**.
3. Wprowadź **adres witryny** dla witryny programu SharePoint, na której hostowana jest lista wniosków urlopowych, a następnie wybierz listę z pola **Nazwa listy**.
4. Dodaj akcję **Użytkownicy usługi Office 365 — Pobierz menedżera**, a następnie dodaj token **Utworzono za pomocą poczty e-mail** w polu **Użytkownik (główna nazwa użytkownika)**.
   
    Token **Utworzono za pomocą poczty e-mail** znajduje się w kategorii **Po utworzeniu lub zmodyfikowaniu elementu** na liście **zawartości dynamicznej**.
5. Dodaj kolejną akcję **Użytkownicy usługi Office 365 — Pobierz menedżera**, a następnie dodaj token **Adres e-mail**w polu **Użytkownik (główna nazwa użytkownika)**.
   
    Token **Adres e-mail** znajduje się w kategorii **Pobieranie menedżera** na liście **zawartości dynamicznej**.
   
    Można również zmienić nazwę karty **Pobieranie menedżera 2** na bardziej opisową nazwę, taką jak „Pomijanie poziomu menedżera”.
6. Dodaj akcję **Rozpocznij zatwierdzenie**, a następnie wybierz pozycję **Wszyscy z listy przypisanych** z listy **Typ zatwierdzenia**.
   
   > [!IMPORTANT]
   > Jeśli jedna z osób zatwierdzających odrzuci prośbę, prośba o zatwierdzenie jest uważana za odrzuconą dla wszystkich osób zatwierdzających.
   > 
   > 
7. Skorzystaj ze wskazówek w poniższej tabeli, aby uzupełnić kartę **Rozpoczynanie zatwierdzenia**.
   
   | Pole | Opis |
   | --- | --- |
   |  Typ zatwierdzenia |Użyj elementu **Każdy z listy przypisanych**, aby wskazać, że każda z osób zatwierdzających może zatwierdzić lub odrzucić żądanie. </p>Użyj elementu **Wszyscy z listy przypisanych**, aby wskazać, że żądanie zostanie zatwierdzone tylko wtedy, gdy wszyscy wyrażą zgodę, oraz zostanie odrzucone, jeśli jedna osoba je odrzuci. |
   |  Tytuł |Tytuł żądania zatwierdzenia. |
   |  Przypisano do |Adresy e-mail osób zatwierdzających. |
   |  Szczegóły |Wszelkie dodatkowe informacje, które chcesz wysłać do osób zatwierdzających wymienionych na liście w polu **Przypisano do**. |
   |  Link do elementu |Adres URL do elementu zatwierdzenia. W tym przykładzie jest to link do elementu w programie SharePoint. |
   |  Opis linku do elementu |Tekstowy opis **linku do elementu**. |
   
   > [!TIP]
   > Akcja **Rozpocznij zatwierdzenie** dostarcza kilka tokenów, łącznie z tokenem **Odpowiedź** i **Podsumowanie odpowiedzi**. Użyj tych tokenów w swoim przepływie, aby zapewnić zaawansowane raportowanie wyników z przebiegu przepływu żądania zatwierdzenia.
   > 
   > 
   
    Karta **Rozpoczynanie zatwierdzenia** jest szablonem żądania zatwierdzenia wysyłanego do osób zatwierdzających. Skonfiguruj ją w taki sposób, aby przydała się w Twojej organizacji. Oto przykład.
   
    ![rozpoczynanie zatwierdzenia](media/all-assigned-must-approve/start-an-approval-card.png)
8. Dodaj akcję **Office 365 Outlook — Wyślij wiadomość e-mail**, a następnie skonfiguruj ją w celu wysłania wiadomości e-mail z wynikami żądania.
   
    Oto przykład, jak może wyglądać karta **Wysyłanie wiadomości e-mail**.
   
    ![wysyłanie wiadomości e-mail](media/all-assigned-must-approve/send-an-email-card.png)

> [!NOTE]
> Dowolna akcja, która następuje po akcji **Rozpocznij zatwierdzenie**, jest uruchamiana na podstawie Twojego wyboru z listy **Typ zatwierdzenia** na karcie **Rozpoczynanie zatwierdzenia**. W poniższej tabeli wymieniono zachowanie w zależności od dokonanego wyboru.
> 
> 

| Typ zatwierdzenia | Zachowanie |
| --- | --- |
| Każdy z listy przypisanych |Akcje następujące po akcji **Rozpocznij zatwierdzenie** są uruchamiane, gdy którakolwiek z osób zatwierdzających zatwierdzi żądanie. |
| Wszyscy z listy przypisanych |Akcje następujące po akcji **Rozpocznij zatwierdzenie** są uruchamiane, gdy jedna z osób zatwierdzających odrzuci żądanie lub gdy wszystkie osoby zatwierdzające je zatwierdzą. |

W górnej części ekranu, w polu **Nazwa przepływu** wprowadź nazwę przepływu, a następnie wybierz polecenie **Utwórz przepływ**, aby go zapisać.

Gratulacje, Twój przepływ jest już gotowy! Jeśli wykonano wszystkie opisane do tego miejsca czynności, przepływ powinien wyglądać jak na poniższym obrazie.

![ogólny obraz przepływu](media/all-assigned-must-approve/overall-flow.png)

Od teraz zawsze, gdy element na liście programu SharePoint ulegnie zmianie, przepływ zostanie wyzwolony i wyśle żądania zatwierdzenia do wszystkich osób zatwierdzających wymienionych w polu **Przypisano do** na karcie **Rozpoczynanie zatwierdzenia**. Przepływ wysyła żądania zatwierdzenia za pomocą aplikacji mobilnej Microsoft Flow i za pośrednictwem poczty e-mail. Osoba, która tworzy element w programie SharePoint, otrzymuje wiadomość e-mail, który podsumowuje wyniki i jasno określa, czy żądanie zostało zatwierdzone, czy odrzucone.

Oto przykład żądania zatwierdzenia wysyłanego do każdej osoby zatwierdzającej.

![żądanie zatwierdzenia](media/all-assigned-must-approve/approval-request.png)

Oto przykład, jak może wyglądać odpowiedź i podsumowanie odpowiedzi po uruchomieniu przepływu.

![tokeny odpowiedzi](media/all-assigned-must-approve/response-output.png)

## <a name="learn-more-about-approvals"></a>Dowiedz się więcej o zatwierdzeniach
* [Nowoczesne zatwierdzenia z jedną osobą zatwierdzającą](modern-approvals.md)
* [Nowoczesne zatwierdzenia sekwencyjne](sequential-modern-approvals.md)
* [Nowoczesne zatwierdzenia równoległe](sequential-modern-approvals.md)

