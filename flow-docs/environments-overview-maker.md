---
title: "Przełączanie środowisk podczas tworzenia przepływu | Microsoft Docs"
description: "Sposoby korzystania z różnych środowisk podczas tworzenia przepływu usługi Microsoft Flow"
services: 
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/27/2016
ms.author: sunayv
ms.openlocfilehash: bcbb566c20291da14881d771c538dd89689b6b1d
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="choosing-an-environment"></a>Wybieranie środowiska
Usługa Microsoft Flow umożliwia pracę w różnych środowiskach i proste przełączanie się między nimi. Zakres tego artykułu obejmuje następujące tematy dotyczące środowiska:

* Podstawy funkcji oferowanych przez środowiska
* Przełączanie środowisk
* Jak utworzyć przepływ w odpowiednim środowisku

## <a name="environments-overview"></a>Środowiska — omówienie
Środowiska umożliwiają wyznaczanie granic izolacji przepływów, połączeń, bram i innych zasobów. Podczas tworzenia przepływu możesz wybrać środowisko, które ma hostować przepływ, oraz zasoby używane w obrębie tego przepływu. Możesz używać różnych środowisk dla różnych scenariuszy.

Przykłady:

* Tworzysz przepływ korzystający z połączenia z usługą Microsoft Common Data Service. W tym scenariuszu przepływ i usługa Common Data Service znajdują się w tym samym środowisku. Dzięki temu wszystkie dane są izolowane w tym środowisku (w obrębie granic izolacji).
* Tworzysz przepływ dla działu kadr. Chcesz mieć pewność, że tylko użytkownicy z działu kadr mają dostęp do tego przepływu. Na przykład nie chcesz, aby grupa Sprzedaż korzystała z przepływu. W tym scenariuszu możesz użyć oddzielnego środowiska, w którym tylko użytkownicy z działu kadr mają uprawnienia do obsługi przepływu i wszystkich używanych przez niego zasobów, takich jak bramy lub połączenia.
* W Europie znajdują się użytkownicy, którzy za pomocą przepływu wyświetlają dane programu SharePoint. W tym scenariuszu należy utworzyć środowisko w Europie, które obsługuje przepływ, i połączenie programu SharePoint. Dzięki środowisku znajdującym się w Europie europejscy użytkownicy mogą uzyskiwać najlepszą wydajność, ponieważ wszystkie zasoby są lokalne w Europie (lokalizacja danych).

Środowiska są tworzone przez administratorów usługi Microsoft Flow. Administratorzy ci kontrolują także, kto ma dostęp do różnych środowisk.

W tym temacie opisano sposób przechodzenia między różnymi środowiskami. Aby uzyskać szczegółowe informacje dotyczące tworzenia środowisk i zarządzania nimi, zobacz część dotyczącą [administrowania środowiskami](environments-overview-admin.md).

## <a name="switching-environments"></a>Przełączanie środowisk
Usługa Microsoft Flow ułatwia w znacznym stopniu przełączanie między środowiskami. Po przełączeniu widzisz wszystkie elementy w określonym środowisku i nie widzisz elementów w żadnym innym środowisku.

Oto przykład.

Utwórz przepływ o nazwie *Nowy_pracownik* w środowisku *Kadry*. W witrynie [flow.microsoft.com](http://flow.microsoft.com) otwórz środowisko *Sprzedaż*. Przepływu *Nowy_pracownik* nie będzie na liście. Aby wyświetlić przepływ *Nowy_pracownik* otwórz środowisko *Kadry*. Pamiętaj, że dotyczy to wszelkich elementów utworzonych w środowisku, w tym połączeń, bram, aplikacji PowerApps i innych.

1. Otwórz witrynę [flow.microsoft.com](http://flow.microsoft.com).
2. W prawym górnym rogu jest wyświetlana Twoja nazwa i bieżące środowisko:  
   ![](./media/environments-overview-maker/default-environment.png)
   
    Na ilustracji zwróć uwagę na powiadomienia. Te powiadomienia są specyficzne dla przepływu w tym środowisku domyślnym.
3. Wybierz nazwę. Na liście rozwijanej są wyświetlane wszystkie dostępne środowiska. Twoje bieżące środowisko jest zaznaczone:  
   ![](./media/environments-overview-maker/all-environments.png)
4. Aby przełączyć się do innego środowiska, wybierz środowisko na liście:  
   ![](./media/environments-overview-maker/select-europe.png)
5. Usługa Microsoft Flow automatycznie wykona przełączenie do nowego środowiska:  
   ![](./media/environments-overview-maker/europe-environment.png)
   
    Na ilustracji zwróć uwagę na brak powiadomień. Nowe środowisko Europa nie ma żadnych powiadomień.

## <a name="create-flows-in-the-right-environment"></a>Tworzenie przepływów w odpowiednim środowisku
Przed utworzeniem przepływu zawsze upewnij się, że wybierasz odpowiednie środowisko do umieszczenia w nim przepływu. W przeciwnym razie będzie trzeba usunąć przepływ i ponownie uruchomić go w prawidłowym środowisku.

Wybierając środowisko do utworzenia przepływów, weź pod uwagę następujące czynniki:

* Bramy są tworzone w środowisku domyślnym. Bram nie można tworzyć w innych środowiskach, dlatego aby połączyć się z danymi lokalnymi, należy użyć środowiska domyślnego.
* W obrębie przepływów można używać tylko połączeń i innych zasobów tego samego środowiska. Nie można korzystać z zasobów w innym środowisku. Na przykład tworzysz przepływ, który używa łącznika niestandardowego. Ten łącznik niestandardowy musi działać w tym samym środowisku co przepływ.
* Baza danych usługi Microsoft Common Data Service jest zawsze powiązana z tylko jednym środowiskiem. Oznacza to, jeśli kiedykolwiek chcesz pracować z danymi usługi Common Data Service, musisz wybrać środowisko, w którym znajduje się baza danych.
* Będziesz widzieć wszystkie środowiska, w których możesz edytować zasoby. Nie oznacza to jednak, że możesz tworzyć nowe zasoby we wszystkich środowiskach. W związku z tym w niektórych środowiskach nie możesz tworzyć nowych przepływów. Musisz poprosić administratora, aby dodał Cię jako **twórcę** do tego środowiska, lub wybrać inne środowisko, w którym utworzysz przepływ (zawsze możesz tworzyć przepływy w środowisku domyślnym).

## <a name="what-you-did"></a>Co zostało zrobione
Wykonując poniższe czynności, przełączasz się między środowiskami, których zgodnie z uprawnieniami możesz używać. Teraz możesz rozpocząć tworzenie przepływów.

## <a name="next-steps"></a>Następne kroki
[Tworzenie przepływu na podstawie szablonu](get-started-logic-template.md)  
[Tworzenie przepływu](get-started-logic-flow.md)  
[Omówienie środowiska dla administratorów](environments-overview-admin.md)

