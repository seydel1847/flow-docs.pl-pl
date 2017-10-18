---
title: "Bloki konstrukcyjne w usłudze Microsoft Flow | Microsoft Docs"
description: "Zapoznaj się z różnymi sekcjami usługi Microsoft Flow i ich wzajemnymi powiązaniami. Tworzenie nowych przepływów na podstawie szablonów i od początku."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: 9U8jMRO-Jv0
courseduration: 9m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 6a7fe2d56c7bc3b2253b675ce26f3f29042a7a71
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="building-blocks-of-microsoft-flow"></a>Bloki konstrukcyjne w usłudze Microsoft Flow
Poznawszy podstawy usługi Microsoft Flow, można przejść do **przewodnika po usłudze Microsoft Flow**. Krótko omówimy proces tworzenia przepływów na podstawie szablonów oraz proces tworzenia przepływów od podstaw.

## <a name="check-out-the-templates"></a>Zobacz szablony
W witrynie flow.microsoft.com po kliknięciu łącza **Szablony** na górze strony zostanie wyświetlonych kilka szablonów, których można natychmiast użyć z usługami sieci Web. Przejrzyj je, aby **poznać ogólne możliwości** usługi Microsoft Flow i dowiedzieć się, w jaki sposób może ona usprawnić Twoją działalność.

![Szablony przepływu](./media/learning-flow-parts/template-list.png)

Każdy szablon przepływu jest przeznaczony do określonego celu, na przykład do otrzymywania powiadomień o zdarzeniach, kopiowania nowego pliku z jednej usługi do drugiej lub śledzenia zatwierdzeń programu SharePoint. Te szablony są **gotowe do użycia**.  Wystarczy **skonfigurować szablony**, aby dodać przepływy do swojego konta. Można to zrobić, klikając opcję **Użyj tego szablonu**, logując się do wymaganych usług i wypełniając wyświetlone formularze.  Przedstawiony przykładowy przepływ został utworzony w oparciu o szablon do wysyłania powiadomień e-mail informujących o modyfikacji listy programu SharePoint. 

![Przykładowy szablon przepływu](./media/learning-flow-parts/example-template.png)

Istnieją setki szablonów. Można je znaleźć w sekcji **Microsoft Flow for web** (Usługa Microsoft Flow dla Internetu) lub **Microsoft Flow for mobile** (Usługa Microsoft Flow dla urządzeń przenośnych).

![Usługa Flow dla sieci Web i urządzeń przenośnych](./media/learning-flow-parts/flow-web-mobile.png)

## <a name="create-a-flow-from-scratch"></a>Tworzenie przepływu od podstaw
Pokazaliśmy już, jak utworzyć przepływ przy użyciu szablonu, co należy jednak zrobić, jeśli trzeba zautomatyzować zadanie, ale nie można znaleźć odpowiedniego szablonu? W takiej sytuacji można **utworzyć przepływ od podstaw**.  Tworzenie przepływu od podstaw należy rozpocząć od pustej kanwy, do której trzeba dodać **usługi, wyzwalacze i działania** w celu utworzenia własnego przepływu.  

![Pusty przepływ](./media/learning-flow-parts/flow-from-blank.png)

## <a name="building-blocks-of-a-flow"></a>Bloki konstrukcyjne przepływu
Bez względu na to, czy tworzysz przepływy na podstawie szablonu, czy od początku, będą one zawierać **bloki konstrukcyjne** współpracujące ze sobą w określony sposób, podobnie jak ma to miejsce na schemacie blokowym.

* **Usługi** stanowią źródła i miejsca docelowe danych w przepływie.
* **Wyzwalacze** to zdarzenia uruchamiające przepływ.
* **Akcje** to zadania wykonywane w ramach przepływu.
* **Warunki** umożliwiają tworzenie w ramach przepływu rozgałęzień wykorzystujących wyrażenia logiczne if/then.
* **Pętle** umożliwiają co najmniej jednokrotną iterację akcji.

### <a name="services"></a>Usługi
Usługa Microsoft Flow może łączyć się z wieloma różnymi **aplikacjami i usługami**.  Przykłady takich usług to **Twitter**, **Github**, **Wunderlist**, **Office 365** i **Dokumenty Google**.  Stanowią one **źródła** dostarczające dane do usługi Microsoft Flow i pełnią rolę **miejsc docelowych** dla pracy wykonanej w ramach usługi.  Pełną listę usług można wyświetlić, klikając łącze **Usługi** u góry witryny **flow.microsoft.com**.

![Łączniki przepływu](./media/learning-flow-parts/flow-connectors.png)

### <a name="triggers"></a>Wyzwalacze
Każdy przepływ rozpoczyna się od uruchomienia **wyzwalacza**.  Istnieje wiele różnych rodzajów wyzwalaczy.  Niektóre z nich to zdarzenia w połączonych usługach sieci Web, takie jak **wysłanie tweeta przez określonego użytkownika** lub **zapis pliku na koncie Dropbox**.  Inne wyzwalacze są wbudowane, np. **uruchomienie przepływu w ramach harmonogramu cyklicznego** lub **uruchomienie przepływu w odpowiedzi na żądanie sieci Web**.  Istnieją także wyzwalacze ręczne, np. uruchomianie przepływu poprzez kliknięcie **przycisku w usłudze Microsoft Flow lub Microsoft PowerApps**.  Wyzwalacze często **przekazują informacje o zdarzeniu, które miało miejsce**, do akcji w przepływie.

![Wyzwalacze przepływu](./media/learning-flow-parts/flow-triggers.png)  

### <a name="actions"></a>Akcje
**Akcja** reprezentuje to, co właściwie ma **się zdarzyć** po wyzwoleniu przepływu.  Może to być **powiadomienie**, **skopiowanie danych lub plików** ze źródła do miejsca docelowego lub inna akcja, taka jak **wysłanie postu do serwisu społecznościowego** lub **opóźnienie o wskazany czas**.  Można także użyć akcji do **pobierania danych z usługi** w celu ich użycia z innymi akcjami.

![Akcje przepływu](./media/learning-flow-parts/flow-actions.png) 

### <a name="conditions"></a>Warunki
**Warunki** umożliwiają dodawanie decyzji do przepływu.  Po oszacowaniu warunku przepływ przechodzi do ścieżki **tak** lub ścieżki **nie**.   Na przykład jeśli chcesz skopiować zdjęcia z urlopu z usługi **Dropbox** do usługi **OneDrive**, możesz utworzyć po wyzwalaczu **Nowy plik z usługi Dropbox** warunek, który sprawdza, czy nazwa pliku zawiera słowo *urlop* — jeśli tak, plik zostanie skopiowany do usługi **OneDrive**; jeśli nie, nic się nie wydarzy.

![Warunek przepływu](./media/learning-flow-parts/flow-condition.png) 

### <a name="loops"></a>Pętle
**Pętle** umożliwiają uruchamianie akcji więcej niż jeden raz, np. gdy należy ją wykonać wielokrotnie lub jednorazowo dla każdego elementu w kolekcji.

## <a name="next-lesson"></a>Następna lekcja
W tym temacie przyjrzeliśmy się ogólnym możliwościom usługi Microsoft Flow.  Przejrzeliśmy **szablony** i omówiliśmy proces **tworzenia przepływu od podstaw**.  Przepływy tworzy się, łącząc się z aplikacjami i usługami oraz korzystając z **wyzwalaczy** uruchamiających przepływy, **akcji** powodujących wykonanie konkretnych zadań, **warunków** uwzględniających decyzje oraz **pętli** do iteracji w przepływie.  **Najprostszym sposobem na poszerzenie wiedzy o usłudze Microsoft Flow jest uruchomienie szablonu** i połączenie go z już używanymi aplikacjami i usługami. 

Teraz dokonamy przeglądu informacji omówionych na wcześniejszych etapach tego kursu z przewodnikiem.

