---
title: "Nauka z przewodnikiem — usługa Microsoft Flow | Microsoft Docs"
description: "Omówienie usługi Microsoft Flow i możliwości jej zastosowania."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: CYR-fZc5Maw
courseduration: 14m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/15/2017
ms.author: deonhe
ms.openlocfilehash: 4cf872ec10b7241cc998f020412e8e227f7c98cf
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="guided-learning-for-microsoft-flow"></a>Nauka z przewodnikiem — usługa Microsoft Flow
Witamy na kursie Nauka z przewodnikiem poświęconym usłudze Microsoft Flow. Użytkownicy mogą zapoznawać się z zagadnieniami tego **kursu online dotyczącego usługi Microsoft Flow we własnym tempie**. Zagadnienia są omawiane kolejno, można więc zdobywać wiedzę od podstaw. Kurs zaprojektowano tak, aby zapewniał **wskazówki dostarczane w zrozumiałych porcjach** z użyciem dużej liczby **wizualizacji i przykładów** przy zachowaniu logicznej progresji, dzięki czemu możesz łatwiej poznawać podstawowe i szczegółowe zagadnienia.

W ramach tego kursu zapoznasz się z usługą Microsoft Flow i jej pojęciami, zobaczysz, jak **tworzyć przepływy**, **zarządzać nimi** oraz **administrować nimi** w swoim środowisku. Przedstawimy Ci informacje i scenariusze dotyczące fikcyjnej firmy o nazwie Contoso Flooring, ale dowiesz się, w jaki sposób zastosować te same scenariusze w swojej firmie lub w firmach Twoich klientów.

Jeśli jesteś początkującym użytkownikiem usługi Microsoft Flow, ten kurs pomoże Ci rozpocząć pracę. Jeśli masz już pewne doświadczenie z usługą, ten kurs pomoże powiązać razem poznane pojęcia i uzupełnić luki. Ten kurs jest nadal dopracowywany, więc **podziel się z nami swoją opinią na jego temat** oraz na temat innych zagadnień, które powinny zostać w nim poruszone.

## <a name="what-is-microsoft-flow"></a>Co to jest usługa Microsoft Flow?
Microsoft Flow jest **usługą przepływu pracy** w trybie online, która pozwala usprawnić pracę i zwiększyć jej wydajność dzięki **automatyzacji przepływów pracy** w ramach najczęściej używanych aplikacji i usług. Możesz na przykład utworzyć przepływ, który dodaje potencjalnego klienta do usługi **Dynamics 365** oraz rekord w usłudze **MailChimp** za każdym razem, gdy ktoś posiadający ponad 100 obserwatorów opublikuje tweet dotyczący Twojej firmy.

![Szkic koncepcyjny usługi Flow](./media/learning-introduce-flow/conceptual.png)

Po rejestracji możesz **połączyć się z ponad 100 usługami** i **zarządzać danymi ze źródeł lokalnych lub w chmurze**, takich jak SQL Server i SharePoint. Lista aplikacji i usług, z których można korzystać w usłudze Microsoft Flow, wciąż się wydłuża.

![Lista usług](./media/learning-introduce-flow/services.png)

## <a name="what-can-you-do-with-microsoft-flow"></a>Co można zrobić, korzystając z usługi Microsoft Flow?
Z użyciem usługi Microsoft Flow możesz **automatyzować przepływy pracy** między ulubionymi **aplikacjami i usługami**, synchronizować pliki, uzyskiwać powiadomienia, gromadzić dane i wykonywać wiele innych operacji. 

Możesz na przykład **zautomatyzować** następujące zadania:

* Natychmiastowe odpowiadanie na wiadomości e-mail lub powiadomienia o wysokim priorytecie.
* Przechwytywanie, śledzenie i monitowanie nowych potencjalnych klientów.
* Kopiowanie plików z jednej usługi do innej.
* Zbieranie danych dotyczących firmy, a następnie udostępnianie tych informacji zespołowi.
* Automatyzacja przepływów pracy zatwierdzania.

Jedno z typowych zastosowań usługi Microsoft Flow to **odbieranie powiadomień**. Możesz na przykład natychmiast otrzymywać wiadomość e-mail lub powiadomienie wypychane na telefon za każdym razem, gdy potencjalny klient zostanie dodany do usługi Dynamics 365 lub Salesforce.

![Przykład powiadomienia e-mail i powiadomienia wypychanego](./media/learning-introduce-flow/sales-lead.png)

**Za pomocą usługi Microsoft Flow możesz również kopiować pliki**. Przykładowo możesz zadbać, aby każdy plik dodawany do usługi Dropbox był **automatycznie kopiowany** do programu SharePoint, gdzie będzie dostępny dla Twojego zespołu.

![Lista plików w usłudze Dropbox](./media/learning-introduce-flow/dropbox-files.png) 

![Lista tych samych plików w programie SharePoint](./media/learning-introduce-flow/sharepoint-files.png) 

Tworząc przepływ uruchamiany za każdym razem, kiedy **ktoś wyśle tweet** zawierający określony hasztag, możesz **monitorować, co ludzie mówią** na temat Twojej firmy. Przepływ może umieszczać informacje o takim tweecie w bazie danych programu SQL Server, na liście programu SharePoint, a nawet w pliku programu Excel hostowanym w usłudze OneDrive — w zależności od Twoich preferencji. Gromadzone dane mogą posłużyć do utworzenia akcji w celu połączenia ich z usługą Power BI, wykrywania trendów i zadawania pytań dotyczących danych.

![Lista tweetów w programie Excel](./media/learning-introduce-flow/tweets-to-excel.png)

![Lista tweetów w programie Excel](./media/learning-introduce-flow/excel-tweets.png)

Oprócz tego możesz również **zautomatyzować pętle zatwierdzania**, na przykład dla wniosków urlopowych na liście programu SharePoint.

![Lista wniosków urlopowych w programie SharePoint](./media/learning-introduce-flow/vacation-requests.png)

Więcej pomysłów odnośnie zastosowań możesz znaleźć, **przeglądając naszą listę szablonów**, które pomagają tworzyć przepływy przy użyciu zaledwie kilku kroków. Na przykład możesz w łatwy sposób tworzyć przepływy, aby **wysyłać sobie prognozy pogody**, przypomnienia w regularnych odstępach czasu lub powiadomienia na telefon za każdym razem, gdy Twój przełożony wyśle do Ciebie wiadomość e-mail.

![Lista szablonów](./media/learning-introduce-flow/templates-you-might-use.png)

Masz pomysł na przepływ, którego nie ma na tej liście? Utwórz własny przepływ od podstaw i, jeśli chcesz, podzieli się nim ze społecznością!

## <a name="where-can-i-create-and-administer-a-flow"></a>Gdzie mogę utworzyć przepływ i zarządzać nim?
Tworzenie przepływów i wykonywanie zadań administracyjnych jest możliwe **w przeglądarce** lub **na telefonie** — jeśli pobierzesz aplikację mobilną usługi Microsoft Flow.

![Zrzut ekranu przedstawiający aplikację mobilną](./media/learning-introduce-flow/screen-mobile-app.png)  

Wykonywać możesz między innymi następujące zadania:

* Włączać i wyłączać przepływy bez względu na swoją lokalizację.
* Sprawdzać, które przepływy nie zadziałały.
* Przeglądać szczegółowe raporty historii uruchamiania.
* Wyświetlać i filtrować uruchomienia według typu powiadomienia.

## <a name="a-brief-tour-of-microsoft-flow"></a>Krótki przewodnik po usłudze Microsoft Flow
Przejdźmy do narzędzia, aby je nieco przybliżyć. Mamy do przekazania wiele informacji na temat tego, w jaki sposób używać usługi Microsoft Flow.

![Początek przewodnika](./media/learning-introduce-flow/start-of-tour.png)

Na stronie głównej znajdują się menu:

* **Moje przepływy**, gdzie znajdziesz swoje przepływy.
* **Szablony** stanowiące doskonałe miejsce, aby rozpocząć.
* **Zatwierdzenia**, gdzie możesz zautomatyzować i uprościć proces zatwierdzania.
* **Łączniki** (dawniej **Usługi**), gdzie możesz połączyć usługi ze sobą.
* **Nauka**, gdzie możesz zdobyć informacje, które pomogą Ci szybciej poznać usługę Microsoft Flow.

![Co możesz zrobić](./media/learning-introduce-flow/what-you-can-do.png)

Skupmy się na razie na menu **Nauka**, gdzie znajdują się następujące pozycje:

* **Nauka z przewodnikiem** pokaże Ci, jak korzystać z usługi Microsoft Flow, począwszy od technik dla początkujących po zaawansowane scenariusze.
* **Dokumentacja** to miejsce, gdzie można znaleźć zaawansowane tematy. Jeśli chcesz dokładnie zrozumieć funkcję lub opcję, możesz zagłębić się w szczegółowe informacje w tym miejscu.
* **Pomoc techniczna** to idealne miejsce, aby znaleźć pomoc.
* **Społeczność** jest miejscem, w którym możesz dowiedzieć się, jak inni użytkownicy korzystają z usługi Microsoft Flow.
* **Prześlij opinię** stanowi łącznik ze społecznością zaawansowanych użytkowników, gdzie możesz **wysyłać komentarze i pytania** do deweloperów i innych użytkowników.
* **Blog** zapewnia informacje o nowościach i nowych wydaniach w ramach ekosystemu usługi Microsoft Flow.
* **Cennik** pomaga w wyborze właściwego planu dla Ciebie lub Twojej firmy.

Na stronie **Szablony** możesz zapoznać się z najpopularniejszymi szablonami, które powinny ułatwić wybór przepływów do wypróbowania.

![Strona docelowa szablonu](./media/learning-introduce-flow/template-page.png)

## <a name="next-lesson"></a>Następna lekcja
Skoro wiesz już co nieco o usłudze Microsoft Flow (czym jest i co można zrobić za jej pomocą), czas na omówienie elementów przepływu.

