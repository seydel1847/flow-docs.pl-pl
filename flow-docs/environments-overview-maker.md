---
title: Informacje na temat środowisk usługi Microsoft Flow | Microsoft Docs
description: Dowiedz się, jak izolować przepływy przy użyciu środowisk
services: ''
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/27/2017
ms.author: sunayv
ms.openlocfilehash: e6667c1c1999c36177d40d52fa657edadd063516
ms.sourcegitcommit: d00c10759d4afb54517a0b1032f8d0a509006d5b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-an-environment"></a>Wybieranie środowiska

W tym artykule zostały opisane **środowiska** usługi Microsoft Flow, w których można tworzyć i bezpiecznie izolować przepływy, bramy, połączenia i inne zasoby.

Dowiesz się:

* jakie funkcje zapewniają środowiska,
* jak przełączać się między środowiskami,
* jak utworzyć przepływ w odpowiednim środowisku.

## <a name="environments-overview"></a>Środowiska — omówienie

Podczas tworzenia przepływu możesz wybrać środowisko, które ma hostować przepływ, oraz zasoby używane w tym przepływie. Możesz używać osobnych środowisk dla różnych scenariuszy.

## <a name="here-are-a-few-scenarios-for-using-environments"></a>Kilka scenariuszy używania środowisk

Scenariusz|Zalecenie
-----|-----
Chcesz utworzyć przepływ korzystający z połączenia z usługą Microsoft Common Data Service.|Umieść przepływ i usługę Common Data Service w tym samym środowisku. Dzięki temu wszystkie dane są izolowane w tym środowisku (w obrębie granic izolacji).
Tworzysz przepływ dla działu kadr. Chcesz mieć pewność, że tylko użytkownicy z działu kadr mają dostęp do tego przepływu.|Utwórz środowisko i dodaj do niego tylko użytkowników z działu kadr. Umieść przepływ i wszelkie inne zasoby używane przez przepływ w tym środowisku.
W Europie znajdują się użytkownicy, którzy za pomocą przepływu wyświetlają dane programu SharePoint.|Utwórz środowisko w Europie, a następnie utwórz w nim przepływ i połączenie programu SharePoint. Dzięki środowisku znajdującym się w Europie europejscy użytkownicy mogą uzyskiwać najlepszą wydajność, ponieważ wszystkie zasoby są lokalne w Europie (lokalizacja danych).

Aby tworzyć środowiska, musisz być administratorem usługi Microsoft Flow. Administratorzy określają, kto ma dostęp do środowisk. Aby uzyskać szczegółowe informacje dotyczące tworzenia środowisk i zarządzania nimi, zobacz temat dotyczący [administrowania środowiskami](environments-overview-admin.md).

## <a name="switching-environments"></a>Przełączanie środowisk

Usługa Microsoft Flow ułatwia przełączanie między środowiskami. Po przełączeniu środowisk są widoczne tylko elementy tworzone w tym konkretnym środowisku. Nie będą widoczne elementy z żadnego innego środowiska, ani nie będziesz mieć do nich dostępu.

Oto przykład.

Utworzono przepływ o nazwie *Nowy_pracownik* w środowisku *Kadry*. W usłudze [Microsoft Flow](https://flow.microsoft.com) otwarto środowisko *Sprzedaż*. Przepływu *Nowy_pracownik* nie ma na liście. Aby wyświetlić przepływ *Nowy_pracownik* otwórz środowisko *Kadry*. Pamiętaj, że te same reguły mają zastosowanie do wszelkich innych elementów utworzonych w środowisku, w tym połączeń, bram, przepływów i innych.

Wykonaj następujące kroki, aby przełączyć środowiska:

1. Zaloguj się w usłudze [Microsoft Flow](https://flow.microsoft.com).
1. W prawym górnym rogu widać obraz odzwierciedlający Twój profil.

   ![Obraz profilu](./media/environments-overview-maker/default-environment.png)

1. Wybierz ten obraz. Na liście rozwijanej zostaną wyświetlone wszystkie dostępne środowiska. Środowisko, do którego się obecnie zalogowano, jest oznaczone znacznikiem wyboru:

   ![Obraz listy środowisk](./media/environments-overview-maker/all-environments.png)
1. Aby przełączyć się do innego środowiska, wybierz środowisko na liście:

   ![Wybierz środowisko, do którego chcesz się przełączyć](./media/environments-overview-maker/select-europe.png)
1. Usługa Microsoft Flow wykona przełączenie do nowego środowiska.

## <a name="create-flows-in-the-right-environment"></a>Tworzenie przepływów w odpowiednim środowisku

Przed utworzeniem przepływu wybierz środowisko, do którego dodasz przepływ i jego zasoby.

> [!NOTE]
> Jeśli utworzysz przepływ w niewłaściwym środowisku, będzie trzeba go usunąć, a następnie utworzyć we właściwym środowisku.

Wybierając środowisko do hostowania przepływów, weź pod uwagę następujące czynniki:

* Bramy można tworzyć tylko w domyślnym środowisku. Dlatego jeśli chcesz używać bramy do łączenia przepływu z danymi lokalnymi, należy użyć środowiska domyślnego.
* Bazy danych usługi Microsoft Common Data Service są powiązane z konkretnym środowiskiem. Dlatego jeśli chcesz utworzyć przepływ, który używa usługi Common Data Service, należy utworzyć przepływ w środowisku hostującym bazę danych.
* Będziesz widzieć wszystkie środowiska, w których możesz edytować zasoby. Jednak należy poprosić administratora o dodanie Cię jako twórcy do wszystkich środowisk, w których chcesz tworzyć przepływy.

> [!NOTE]
> Zawsze będzie można tworzyć przepływy w środowisku domyślnym.

## <a name="next-steps"></a>Następne kroki

* [Tworzenie przepływu na podstawie szablonu](get-started-logic-template.md)
* [Tworzenie przepływu](get-started-logic-flow.md)
* [Omówienie środowiska dla administratorów](environments-overview-admin.md)