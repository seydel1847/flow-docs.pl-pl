---
title: Uruchamianie przepływów na podstawie właściwości wiadomości e-mail | Microsoft Docs
description: Uruchamianie przepływu na podstawie właściwości wiadomości e-mail, takich jak temat, adres nadawcy lub adres odbiorcy wiadomości.
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
ms.date: 06/08/2017
ms.author: deonhe
ms.openlocfilehash: c021f4fee692863bdeaa71d2d49901fbb603aa31
ms.sourcegitcommit: cd3cdcff3accb9a54f002fdc33d33935b4276249
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39519967"
---
# <a name="trigger-a-flow-based-on-email-properties"></a>Wyzwalanie przepływu na podstawie właściwości wiadomości e-mail
Użyj wyzwalacza **Po nadejściu nowej wiadomości e-mail**, aby utworzyć przepływ, który jest uruchamiany, gdy jedna lub więcej z poniższych właściwości wiadomości e-mail spełnia podane kryteria:

| Właściwość | Kiedy stosować |
| --- | --- |
| Folder |Wyzwalanie przepływu za każdym razem, gdy wiadomości e-mail zostaną odebrane w określonym folderze. Ta właściwość może być przydatna w przypadku używania reguł, które kierują wiadomości e-mail do różnych folderów. |
| Do |Wyzwalanie przepływu na podstawie adresu, na który została wysłana wiadomość e-mail. Ta właściwość może być przydatna, jeśli wiadomości e-mail wysłane na różne adresy e-mail są odbierane w tej samej skrzynce odbiorczej. |
| Od |Wyzwalanie przepływu na podstawie adresu e-mail nadawcy. |
| Ważność |Wyzwalanie przepływu na podstawie ważności, z którą zostały wysłane wiadomości e-mail. Wiadomości e-mail mogą być wysyłane z wysoką, normalną lub niską ważnością. |
| Zawiera załącznik |Wyzwalanie przepływu na podstawie obecności załączników w przychodzących wiadomościach e-mail. |
| Filtr tematu |Wyszukiwanie obecności konkretnych słów w temacie wiadomości e-mail. Następnie przepływ uruchamia *akcje* na podstawie wyników wyszukiwania. |

> [!IMPORTANT]
> Każdy [plan usługi Microsoft Flow](https://flow.microsoft.com/pricing/) obejmuje limit przydziału przebiegów. Jeśli to możliwe, należy zawsze sprawdzać właściwości w wyzwalaczu przepływu. Pozwala to uniknąć niepotrzebnego korzystania z limitu przydziału przebiegów. Jeśli właściwość jest sprawdzana w warunku, każdy przebieg jest wliczany do limitu przydziału przebiegów dla planu, nawet jeśli zdefiniowany warunek filtru nie jest spełniony. 

Jeśli na przykład adres nadawcy (w polu *Od*) wiadomości e-mail jest sprawdzany w warunku, każdy przebieg wlicza się do limitu przydziału przebiegów dla planu, nawet jeśli wiadomość e-mail nie została wysłana *z* adresu określonego w warunku.
> 
> 

W poniższych przewodnikach wszystkie właściwości będą sprawdzane w wyzwalaczu **Po nadejściu nowej wiadomości e-mail**. Więcej informacji możesz uzyskać, odwiedzając strony [często zadawanych pytań dotyczących rozliczeń](billing-questions.md#what-counts-as-a-run) i [cennika](https://ms.flow.microsoft.com/pricing/).

## <a name="prerequisites"></a>Wymagania wstępne
* Konto z dostępem do usługi [Microsoft Flow](https://flow.microsoft.com)
* Konto usługi Office 365 Outlook
* Aplikacja mobilna usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows)
* Połączenia z pakietem Office, programem Outlook i usługą powiadomień wypychanych

## <a name="trigger-a-flow-based-on-an-emails-subject"></a>Wyzwalanie przepływu na podstawie tematu wiadomości e-mail
W tym przewodniku zostanie utworzony przepływ, który wysyła powiadomienie wypychane na urządzenie przenośne, jeśli temat dowolnej nowej wiadomości e-mail zawiera słowo „lottery”. Następnie przepływ oznacza każdą taką wiadomość e-mail jako *przeczytane*.

>[!NOTE]
>W tym przewodniku przepływ wysyła powiadomienie wypychane, ale można użyć dowolnej innej akcji, która odpowiada potrzebom przepływu pracy. Można na przykład zapisywać zawartość wiadomości e-mail w innym repozytorium, takim jak usługa Arkusze Google lub plik programu Microsoft Excel przechowywany w usłudze Dropbox.

Zaczynajmy:

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-inbox-folder](includes/sign-in-use-blank-select-email-trigger-and-inbox-folder.md)]

1. W polu **Filtr tematu** wprowadź tekst, którego przepływ będzie używał do filtrowania przychodzących wiadomości e-mail.
   
     W tym przykładzie interesuje nas każda wiadomość e-mail zawierająca słowo „lottery” w temacie.
   
    ![Opcje zaawansowane](./media/email-triggers/email-triggers-subject-text.png)

    [!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. Wprowadź szczegóły powiadomienia na urządzenie przenośne, które chcesz otrzymywać po nadejściu wiadomości e-mail zgodnej z określonym wcześniej **Filtrem tematu**.
   
    ![Szczegóły powiadomienia](./media/email-triggers/email-triggers-4.png)

    [!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. Nadaj przepływowi nazwę. Następnie zapisz go, wybierając pozycję **Utwórz przepływ** w górnej części strony.
   
    ![Zapisywanie przepływu](./media/email-triggers/email-triggers-subject-notification.png)

Gratulacje! Otrzymasz powiadomienie wypychane za każdym razem, gdy nadejdzie wiadomość e-mail zawierająca słowo „lottery” w temacie.

## <a name="trigger-a-flow-based-on-an-emails-sender"></a>Wyzwalanie przepływu na podstawie nadawcy wiadomości e-mail
W tym przewodniku zostanie utworzony przepływ, który wysyła powiadomienie wypychane na urządzenie przenośne, jeśli nadejdzie dowolna nowa wiadomość e-mail od określonego nadawcy (adresu e-mail). Przepływ oznaczy również każdą taką wiadomość e-mail jako *przeczytane*.

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-inbox-folder](includes/sign-in-use-blank-select-email-trigger-and-inbox-folder.md)]

1. W polu **Od** wprowadź adres e-mail nadawcy. 
   
     Przepływ wykonuje akcję na wszystkich wiadomościach e-mail wysłanych z tego adresu.
   
    ![Właściwości wiadomości e-mail](./media/email-triggers/email-triggers-from.png)

    [!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. Wprowadź szczegóły powiadomienia na urządzenie przenośne, które chcesz otrzymywać po nadejściu każdej wiadomości e-mail wysłanej z podanego wcześniej adresu e-mail.
   
    ![Szczegóły powiadomienia](./media/email-triggers/email-triggers-sender-notification.png)

    [!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. Określ nazwę przepływu, a następnie zapisz go, wybierając pozycję **Utwórz przepływ** w górnej części strony.
   
    ![Zapisywanie przepływu](./media/email-triggers/email-triggers-sender-5.png)

## <a name="trigger-a-flow-when-emails-arrive-in-a-specific-folder"></a>Wyzwalanie przepływu w momencie nadejścia wiadomości e-mail odbieranych w określonym folderze
Jeśli masz reguły, które kierują pocztę e-mail do różnych folderów na podstawie określonych właściwości, takich jak adres, możesz użyć tego typu przepływu.

Zaczynajmy:

> [!NOTE]
> Jeśli nie masz jeszcze reguły, która kieruje wiadomości e-mail do folderu innego niż skrzynka odbiorcza, utwórz taką regułę i upewnij się, że działa, wysyłając testową wiadomość e-mail.
> 
> 

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-specific-folder](includes/sign-in-use-blank-select-email-trigger-and-specific-folder.md)]

1. Wybierz folder, do którego mają być kierowane określone wiadomości e-mail. Aby wyświetlić wszystkie foldery poczty e-mail, najpierw wybierz ikonę **Pokaż narzędzie wyboru** znajdującą się po prawej stronie pola **Folder** na karcie **Po nadejściu nowej wiadomości e-mail**.
   
    ![Wybieranie folderu](./media/email-triggers/email-triggers-2.png)

    [!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. Wprowadź szczegóły powiadomienia na urządzenie przenośne, które chcesz otrzymywać po nadejściu wiadomości e-mail odbieranej w wybranym wcześniej folderze. Jeśli jeszcze tego nie zrobiono, wprowadź poświadczenia dla usługi powiadomień.
   
    ![Szczegóły powiadomienia](./media/email-triggers/email-triggers-folder-notification.png)

    [!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. Określ nazwę przepływu, a następnie zapisz go, wybierając pozycję **Utwórz przepływ** w górnej części strony.
   
    ![Zapisywanie przepływu](./media/email-triggers/email-triggers-7.png)

Przetestuj przepływ, wysyłając wiadomość e-mail, która jest kierowana do folderu wybranego wcześniej w tym przewodniku.

