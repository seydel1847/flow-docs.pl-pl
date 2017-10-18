---
title: "Dowiedz się, jak zarządzać lokalnymi bramami danych | Microsoft Docs"
description: "Wyświetlanie i instalowanie lokalnej bramy danych w usłudze Microsoft Flow"
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
ms.date: 02/15/2017
ms.author: deonhe
ms.openlocfilehash: 41f5d40ca2ad5fcce3a7967beef7104dd532b1d8
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="manage-an-on-premises-data-gateway-in-microsoft-flow"></a>Zarządzanie lokalnymi bramami danych w usłudze Microsoft Flow
Zainstaluj lokalną bramę danych i zarządzaj nią, aby bezpiecznie zintegrować różne aplikacje oparte na chmurze z danymi i aplikacjami lokalnymi w usłudze Microsoft Flow.

Bramy pozwalają łączyć się z danymi lokalnymi przez te połączenia:

* SharePoint
* SQL Server
* Oracle
* Informix
* System plików
* DB2

> [!IMPORTANT]
> Bramy danych programu Microsoft SharePoint obsługują ruch HTTP, ale nie obsługują ruchu HTTPS.
> 
> 

## <a name="prerequisites"></a>Wymagania wstępne
* Nazwa użytkownika i hasło, których użyto w celu [zarejestrowania się](sign-up-sign-in.md) w usłudze Microsoft Flow.
* Uprawnienia administracyjne dotyczące bramy.
  
  Posiadasz te uprawnienia domyślnie dla każdej instalowanej bramy, a administrator innej bramy można przyznać Ci uprawnienia do bramy, która mu podlega.
* Licencja obsługująca bramy. Aby uzyskać więcej informacji, zobacz sekcję „Łączność” na [stronie z cennikiem](https://flow.microsoft.com/pricing/).
* Możesz utworzyć bramę oraz połączenie lokalne tylko w [środowisku domyślnym](environments-overview-maker.md).

## <a name="view-your-gateways"></a>Wyświetlanie bram
W prawym górnym rogu [witryny sieci Web usługi Microsoft Flow](https://flow.microsoft.com) kliknij lub naciśnij ikonę koła zębatego, a następnie kliknij lub naciśnij opcję **Bramy**.

![Brama objęta zarządzaniem][1]

**Uwaga**: jeśli utworzono lub uzyskano dostęp do bramy w usłudze PowerApps, brama ta pojawi się na liście **Moje bramy** w usłudze Microsoft Flow.

## <a name="install-a-gateway"></a>Instalowanie bramy
1. Pobierz [Kreatora instalacji bramy](http://go.microsoft.com/fwlink/?LinkID=820580&clcid=0x409).
   
    Możesz również pobrać tego kreatora, klikając lub naciskając ikonę koła zębatego w prawym górnym rogu [witryny internetowej usługi Microsoft Flow](https://flow.microsoft.com), klikając lub naciskając pozycję **Bramy**, a następnie klikając lub naciskając pozycję **Utwórz bramę**.
   
    ![Instalacja bramy][2]
2. Uruchom tego kreatora, podając te same poświadczenia, których używasz do logowania się w usłudze Microsoft Flow.
   
    Po pomyślnym zarejestrowaniu i skonfigurowaniu bramy zostanie ona wyświetlona na liście **Moje bramy** w usłudze Microsoft Flow.

Aby uzyskać więcej informacji, zobacz [Opis bram](gateway-reference.md).

<!-- Image references -->
[1]: ./media/manage-gateway/view-gateways.png
[2]: ./media/manage-gateway/list-gateways.png
