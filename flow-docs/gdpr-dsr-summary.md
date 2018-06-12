---
title: 'RODO: podsumowanie żądań podmiotów danych | Microsoft Docs'
description: Dowiedz się, jak reagować na żądania podmiotów danych w usłudze Microsoft Flow.
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/24/2018
ms.author: keweare
ms.openlocfilehash: c57296bed460dbf94aa597542413783292e1a8f7
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34552173"
---
# <a name="responding-to-gdpr-data-subject-requests-for-microsoft-flow"></a>Reagowanie na żądania podmiotów danych RODO w usłudze Microsoft Flow

Ten artykuł przygotowuje Ciebie i Twoją organizację na wprowadzenie w Unii Europejskiej Ogólnego rozporządzenia o ochronie danych (RODO). W tym artykule nie tylko opisano czynności wykonywane przez firmę Microsoft w celu przygotowania do wprowadzenia RODO, ale także udostępniono przykłady kroków, które można wykonać dzisiaj w celu uzyskania zgodności z rozporządzeniem RODO w przypadku korzystania z usług PowerApps, Microsoft Flow i Common Data Service for Apps.

## <a name="prerequisites"></a>Wymagania wstępne

Akcje opisane w tym artykule mogą wykonywać użytkownicy i administratorzy.

### <a name="users"></a>Użytkownicy

Użytkownik musi mieć aktywne konto usługi Azure Active Directory z [licencją usługi Microsoft Flow](https://preview.flow.microsoft.com/pricing/). Użytkownicy, którzy nie spełniają tego wymagania, muszą poprosić administratora o wykonanie tych akcji.

### <a name="administrators"></a>Administratorzy

Możesz wykonywać opisane w tym artykule operacje, które wymagają uprawnień administratora, jeśli zalogujesz się do [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com/) lub [programu PowerShell dla administratora usługi PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) z konta, które ma obydwa te uprawnienia:

- Licencja płatna lub w wersji próbnej dla planu 2 usługi PowerApps.

    [Licencja w wersji próbnej](http://web.powerapps.com/trial) wygasa w ciągu 30 dni.

- [Administrator globalny usługi Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) lub [administrator globalny usługi Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

### <a name="unmanaged-tenants"></a>Dzierżawy niezarządzane
Jeśli jesteś członkiem [dzierżawy niezarządzanej](https://docs.microsoft.com/azure/active-directory/domains-admin-takeover) (co oznacza, że dzierżawa usługi Azure AD nie ma administratora globalnego), nadal będziesz mieć możliwość wykonania kroków opisanych w tym artykule w celu wyeksportowania i usunięcia własnych danych osobowych. 

## <a name="responding-to-dsrs-for-microsoft-flow-customer-data"></a>Reagowanie na żądania podmiotów danych dotyczące danych klientów usługi Microsoft Flow

Rozporządzenie RODO nadaje osobom (określanym w RODO jako podmioty danych) prawa do zarządzania danymi osobowymi zebranymi przez pracodawcę lub agencję albo organizację innego typu (określanymi jako kontroler danych lub po prostu kontroler). Dane osobowe mają w rozporządzeniu RODO bardzo szeroką definicję: są to wszystkie dane powiązane ze zidentyfikowaną lub możliwą do zidentyfikowania osobą fizyczną. RODO udostępnia podmiotom danych określone prawa do ich danych osobowych; prawa te obejmują uzyskiwanie kopii danych osobowych, żądanie wprowadzenia ich korekty, ograniczenie ich przetwarzania, ich usuwanie lub odbieranie w formie elektronicznej w celu przeniesienia do innego kontrolera. Formalne żądanie podmiotu danych skierowane do kontrolera i dotyczące podjęcia akcji związanej z jego danymi nosi nazwę żądania praw podmiotu danych (DSR, Data Subject Rights).

W tym artykule omówiono sposób używania produktów, usług i narzędzi administracyjnych firmy Microsoft w celu ułatwienia kontrolerom wyszukiwania danych osobowych i wykonywania związanych z nimi akcji w przypadku reagowania na żądania podmiotów danych. W szczególności ten artykuł zawiera informacje dotyczące sposobu znajdowania danych osobowych, które znajdują się w chmurze firmy Microsoft, uzyskiwania do nich dostępu i wykonywania właściwych czynności związanych z tymi danymi. Oto krótkie omówienie procesów przedstawionych w tym przewodniku:

1. Odnajdowanie: używanie narzędzi do wyszukiwania i odnajdywania w celu łatwiejszego znajdowania danych klienta, które mogą być przedmiotem żądania podmiotu danych. Po zebraniu potencjalnie użytecznych dokumentów można wykonać co najmniej jedną z akcji żądania podmiotu danych opisanych w poniższych krokach, aby odpowiedzieć na żądanie. Alternatywnie można stwierdzić, że żądanie nie spełnia wytycznych organizacji dotyczących reagowania na żądania podmiotów danych. [Dokumentacja dotycząca odnajdywania dla żądań podmiotów danych w usłudze Microsoft Flow](gdpr-dsr-discovery.md)

1. Uzyskiwanie dostępu: pobieranie danych osobowych, które znajdują się w chmurze firmy Microsoft, i jeśli tego zażądano, wykonywanie kopii do udostępnienia osobie, której dane dotyczą.

1. Korygowanie: wprowadzanie zmian lub implementowanie innych żądanych akcji związanych z danymi osobowymi, jeśli mają zastosowanie.

    Jeśli osoba, której dotyczą dane, zażąda skorygowania danych osobowych przechowywanych przez organizację, Ty i Twoja organizacja musicie zdecydować, czy należy zastosować się do tego żądania.  Korygowanie danych może obejmować wykonanie akcji, takich jak edytowanie, redagowanie lub usuwanie danych osobowych.

    Do zarządzania tożsamościami użytkowników usługi Microsoft Flow można używać usługi Azure Active Directory. Klienci korporacyjni mogą zarządzać żądaniami podmiotów danych dotyczących korygowania, w tym ograniczonymi funkcjami edytowania, zgodnie z charakterem danej usługi firmy Microsoft.  Jako podmiot przetwarzający dane firma Microsoft nie oferuje możliwości poprawiania dzienników generowanych przez system, ponieważ odzwierciedlają one faktyczne działania i stanowią historyczny rekord zdarzeń zachodzących w usługach firmy Microsoft.  [Dowiedz się więcej na temat żądań podmiotów danych](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-azure).

1. Ograniczanie: ograniczanie przetwarzania danych osobowych przez usunięcie licencji różnych usług online albo wyłączenie żądanych usług, jeśli jest to możliwe. Można również usunąć dane z chmury firmy Microsoft i przechowywać je lokalnie lub w innej lokalizacji.

    Osoby, których dane dotyczą, mogą zażądać ograniczenia przetwarzania ich danych osobowych.  Firma Microsoft udostępnia przeznaczone do tego celu interfejsu programowania aplikacji (API) i interfejsy użytkownika.  Te interfejsy umożliwiają administratorowi dzierżawy klienta korporacyjnego zarządzanie takimi żądaniami podmiotów danych za pośrednictwem kombinacji eksportu danych i usuwania danych. Klient może (1) wyeksportować elektroniczną kopię danych osobowych użytkownika, w tym konta, dzienniki generowane przez system i skojarzone dzienniki, a następnie (2) usunąć konto i skojarzone dane znajdujące się w systemach firmy Microsoft.

1. Usuwanie: trwałe usuwanie danych osobowych, które znajdują się w chmurze firmy Microsoft. [Dowiedz się więcej na temat usuwania danych osobowych](gdpr-dsr-delete.md).

1. Eksportowanie: udostępnianie elektronicznej kopii danych osobowych (w formacie możliwym do odczytu maszynowego) osobie, której dane dotyczą. W poszczególnych sekcjach tego artykułu opisano procedury techniczne, które organizacja kontrolera danych może wykonać w odpowiedzi na żądanie podmiotu danych dotyczące danych osobowych w chmurze firmy Microsoft. [Dowiedz się więcej na temat eksportowania danych osobowych](gdpr-dsr-export.md).

## <a name="system-generated-logs"></a>Dzienniki generowane przez system

Zapoznaj się z tym [przewodnikiem](https://docs.microsoft.com/powerapps/administrator/powerapps-gdpr-dsr-guide-systemlogs), aby uzyskać więcej informacji na temat dzienników generowanych przez system na potrzeby usługi Microsoft Flow.
