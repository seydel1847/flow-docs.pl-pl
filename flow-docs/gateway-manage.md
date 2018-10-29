---
title: Dowiedz się, jak zarządzać lokalnymi bramami danych | Microsoft Docs
description: Wyświetlanie i instalowanie lokalnej bramy danych w usłudze Microsoft Flow
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
ms.date: 02/05/2018
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: b25f63a3980d21e60b26a0783ac4bf5eb6030cd3
ms.sourcegitcommit: 282059c82bfcf5896d06043476c34641906e20e3
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087913"
---
# <a name="manage-an-on-premises-data-gateway-in-microsoft-flow"></a>Zarządzanie lokalnymi bramami danych w usłudze Microsoft Flow

Zainstaluj lokalną bramę danych i zarządzaj nią, aby bezpiecznie zintegrować różne aplikacje oparte na chmurze z danymi i aplikacjami lokalnymi w usłudze Microsoft Flow.

Bramy pozwalają łączyć się z danymi lokalnymi przez te połączenia:

* Apache Impala
* Utworzone przez użytkownika łączniki niestandardowe
* DB2
* System plików
* HTTP z usługą Azure AD
* Informix
* MySQL
* Oracle Database
* PostgreSQL
* SharePoint
* SQL Server
* Teradata (wersja zapoznawcza)

> [!IMPORTANT]
> Bramy danych programu Microsoft SharePoint obsługują teraz zarówno ruch HTTP, jak i HTTPS.

## <a name="prerequisites"></a>Wymagania wstępne

* Nazwa użytkownika i hasło, których użyto w celu [zarejestrowania się](sign-up-sign-in.md) w usłudze Microsoft Flow.
* Uprawnienia administracyjne dotyczące bramy.

  Te uprawnienia są przyznawane domyślnie dla każdej instalowanej bramy. Ponadto administrator innej bramy może nadać użytkownikowi te uprawnienia w odniesieniu do danej bramy.
* Licencja obsługująca bramy. Aby uzyskać więcej informacji, zobacz sekcję „Łączność” na [stronie z cennikiem](https://flow.microsoft.com/pricing/).

> [!NOTE]
> Możesz utworzyć bramę oraz połączenie lokalne tylko w [środowisku domyślnym](environments-overview-maker.md).



## <a name="view-your-gateways"></a>Wyświetlanie bram

W prawym górnym rogu [witryny Microsoft Flow](https://flow.microsoft.com) wybierz ikonę koła zębatego, a następnie opcję **Bramy**.

![Brama objęta zarządzaniem][1]

> [!NOTE]
> Jeśli utworzono lub uzyskano dostęp do bramy w usłudze PowerApps, brama ta pojawi się na liście **Moje bramy** w usłudze Microsoft Flow.



## <a name="install-a-gateway"></a>Instalowanie bramy

1. Pobierz [Kreatora instalacji bramy](https://go.microsoft.com/fwlink/?LinkID=820580&clcid=0x409).

1. Uruchom tego kreatora, podając te same poświadczenia, których użyto do zalogowania się w usłudze Microsoft Flow.

    Po pomyślnym zarejestrowaniu i skonfigurowaniu bramy będzie ona widoczna na liście **Bramy** w usłudze Microsoft Flow.

Aby uzyskać więcej informacji, zobacz [Opis bram](gateway-reference.md).

<!-- Image references -->
[1]: ./media/manage-gateway/view-gateways.png
