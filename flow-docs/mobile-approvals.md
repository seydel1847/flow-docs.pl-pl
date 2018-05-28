---
title: Zatwierdzanie żądań na urządzeniu przenośnym | Microsoft Docs
description: Żądania utworzone w usłudze Microsoft Flow można zatwierdzać na urządzeniu przenośnym.
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
ms.openlocfilehash: 2b856dfa75e0acb7eb83525c4d64d070315b5735
ms.sourcegitcommit: f0202f74ba9a2282a670a1751462f598a5ea0ce5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="approve-requests-on-your-mobile-device-by-using-microsoft-flow"></a>Zatwierdzanie żądań na urządzeniu przenośnym za pomocą usługi Microsoft Flow
Jeśli jesteś w przepływie wskazany jako osoba zatwierdzająca i masz zainstalowaną aplikację mobilną usługi Microsoft Flow, otrzymasz powiadomienie wypychane za każdym razem, gdy będzie potrzebne Twoje zatwierdzenie.

W tym artykule omówiono klika typowych scenariuszy, z którymi pewnie się spotkasz, zarządzając żądaniami zatwierdzenia w aplikacji mobilnej usługi Microsoft Flow.

> [!NOTE]
> Ilustracje w tym artykule pochodzą z urządzenia z systemem Android, ale w systemie iOS wszystko wygląda podobnie.
> 
> 

## <a name="prerequisites"></a>Wymagania wstępne
Aby ukończyć ten przewodnik, potrzebne są:

* Urządzenie z systemem [Android](https://aka.ms/flowmobiledocsandroid) lub [iOS](https://aka.ms/flowmobiledocsios) i aplikacją mobilną usługi Microsoft Flow.
* Wyznaczenie jako osoba zatwierdzająca w przepływie zatwierdzenia.
* Oczekujące żądania zatwierdzenia.

## <a name="view-pending-requests"></a>Wyświetlanie oczekujących żądań
1. Otwórz aplikację mobilną usługi Microsoft Flow.
   
    ![Uruchamianie aplikacji mobilnej](./media/mobile-approvals/open-app.png)
2. Wybierz pozycję **ZATWIERDZENIA** w prawym górnym rogu.
   
    ![Wybieranie zatwierdzeń](./media/mobile-approvals/select-approvals.png)
3. Wyświetl wszystkie oczekujące zatwierdzenia:
   
    ![Wyświetlanie oczekujących żądań zatwierdzenia](./media/mobile-approvals/show-pending-approval-requests.png)

Jeśli nie masz żadnych oczekujących żądań zatwierdzenia, utwórz [przepływ zatwierdzania](modern-approvals.md), ustaw siebie jako osobę zatwierdzającą, a następnie wyzwól przepływ. Żądania zatwierdzenia pojawiają się w centrum zatwierdzania kilka sekund po wyzwoleniu przepływu i wysłaniu żądania do zatwierdzenia.

## <a name="approve-requests-and-leave-an-optional-comment"></a>Zatwierdzanie żądań i pozostawianie opcjonalnego komentarza
1. Jeśli nie zostało to jeszcze zrobione, wykonaj wcześniejsze kroki, aby [wyświetlić oczekujące żądania](mobile-approvals.md#view-pending-requests).
2. Wybierz pozycję **ZATWIERDŹ** dla żądania, które chcesz zatwierdzić.
   
    ![Wybieranie pozycji Zatwierdź](./media/mobile-approvals/select-approve.png)
3. (Opcjonalnie) Wybierz pozycję **Dodaj komentarz (opcjonalnie)**.
   
    ![Wybieranie pozycji Dodaj komentarz](./media/mobile-approvals/select-add-comment.png)
   
    Wprowadź komentarz na ekranie **Dodaj komentarz**.
   
    ![Wprowadzanie komentarza](./media/mobile-approvals/enter-comment-for-approval.png)
4. W prawym górnym rogu ekranu wybierz pozycję **POTWIERDŹ**.
   
    ![Potwierdzenie zakończenia](./media/mobile-approvals/tap-confirm-button.png)
   
    Gdy decyzja zostanie zarejestrowana w przepływie, zostanie wyświetlony ekran informujący o powodzeniu.
   
    ![Ekran powodzenia](./media/mobile-approvals/approved.png)

## <a name="reject-requests-and-leave-an-optional-comment"></a>Odrzucanie żądań i pozostawianie opcjonalnego komentarza
Postępuj zgodnie z [krokami zatwierdzania żądania](mobile-approvals.md#approve-requests-and-leave-an-optional-comment), ale w drugim kroku wybierz pozycję **ODRZUĆ**.

## <a name="learn-more"></a>Dowiedz się więcej
[Tworzenie nowoczesnych przepływów zatwierdzania](modern-approvals.md).

