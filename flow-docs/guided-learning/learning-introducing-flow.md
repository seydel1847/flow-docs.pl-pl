---
title: "Wprowadzenie do usługi Microsoft Flow | Microsoft Docs"
description: "Omówienie usługi Microsoft Flow i możliwości jej zastosowania."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: kZs7lqgp4LU
courseduration: 5m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 63ecfabc6b91f3a12fffd6986187b6bbd254b6da
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="guided-learning-for-microsoft-flow"></a>Nauka z przewodnikiem — usługa Microsoft Flow
Witamy na kursie **Nauka z przewodnikiem** poświęconym usłudze Microsoft Flow. Użytkownicy mogą zapoznawać się z zagadnieniami tego kursu online we własnym tempie. Zagadnienia są omawiane kolejno, można więc zdobywać wiedzę od podstaw.

**Kurs z przewodnikiem** zawiera obecnie sekcję wprowadzającą; w ciągu najbliższych tygodni dodamy dalszą treść. Ten kurs ma na celu dostarczać wskazówki w zrozumiałej formie — logicznie połączone i zebrane w większe fragmenty. Przedstawione wskazówki pozwalają zrozumieć poszczególne koncepcje, uzyskać szczegółowe informacje i zapoznać się z przykładami. Kurs zawiera wiele elementów wizualnych, które także ułatwiają przyswajanie wiedzy.

Kurs pozwoli **początkującym użytkownikom** usługi Microsoft Flow rozpocząć korzystanie z niej. **Weterani** usługi mogą odświeżyć pojęcia i odkryć ich wzajemne powiązania, a także uzupełnić wiedzę. Mamy nadzieję, że kurs przypadnie użytkownikom do gustu. W przyszłości poszerzymy go o kolejne treści.

**Cały czas pracujemy** nad tym kursem przewodnika szkoleniowego.  **Podziel się z nami** swoją opinią na jego temat oraz na temat **innych zagadnień do poruszenia** w ramach tego kursu.

## <a name="what-is-microsoft-flow"></a>Co to jest usługa Microsoft Flow?
Microsoft Flow jest **usługą przepływu pracy** w trybie online, która pozwala usprawnić pracę i zwiększyć jej wydajność dzięki automatyzacji przepływów pracy w ramach najczęściej używanych aplikacji i usług.  Usługa Microsoft Flow może łączyć się z ponad stu usługami, które są gotowe do użycia od razu po zarejestrowaniu się. Usługa Microsoft Flow oferuje aplikację mobilną, która pozwala śledzić przepływy pracy podczas podróży, i środowisko administracyjne do użytku w przedsiębiorstwie. Możliwe jest też osadzanie usługi Microsoft Flow we własnych aplikacjach.

W ramach tego kursu zapoznasz się z usługą Microsoft Flow i jej pojęciami oraz zobaczysz, jak tworzyć przepływy, zarządzać nimi i kontrolować je jako administrator w swoim środowisku. Zaprezentujemy informacje i scenariusze użycia na podstawie fikcyjnej firmy o nazwie Contoso Flooring Company.  W ten sposób chcemy pokazać, jak tworzone scenariusze mogą przydać się w Twojej firmie lub w firmach Twoich klientów.

![Szkic koncepcyjny usługi Flow](./media/learning-introducing-flow/flow-conceptual.png)

Usługa Microsoft Flow nie ogranicza się do **aplikacji w Internecie**.  Można w jej przepływach uwzględnić **dane lokalne** pochodzące np. z programów SQL Server i SharePoint.

## <a name="what-you-can-do-with-microsoft-flow"></a>Co można zrobić, korzystając z usługi Microsoft Flow
 Z użyciem usługi Microsoft Flow możesz tworzyć **zautomatyzowane przepływy pracy** między ulubionymi aplikacjami i usługami, aby synchronizować pliki, uzyskiwać powiadomienia, gromadzić dane i wykonywać wiele innych operacji.  [Lista aplikacji i usług, z których można korzystać w usłudze Microsoft Flow](https://flow.microsoft.com/services/), wciąż się wydłuża.  Przykłady zadań, które można zautomatyzować za pomocą usługi Microsoft Flow:

* Natychmiastowe otrzymywanie i odpowiadanie na wiadomości e-mail lub powiadomienia o krytycznym znaczeniu.
* Przechwytywanie, śledzenie i monitowanie nowych potencjalnych klientów.
* Kopiowanie plików z jednej usługi do innej.
* Zbieranie danych dotyczących firmy oraz informowanie zespołu.
* Automatyzowanie zatwierdzeń.

Jedno z typowych zastosowań usługi Microsoft Flow to **odbieranie powiadomień**. Na przykład za każdym razem, gdy potencjalny klient zostanie dodany do usługi Dynamics 365 lub Salesforce, możesz natychmiast otrzymać wiadomość e-mail lub powiadomienie wypychane do aplikacji mobilnej na telefonie. To wspaniały sposób na obserwowanie **nowych potencjalnych klientów**.

Za pomocą usługi Microsoft Flow możesz również kopiować pliki. Na przykład za każdym razem, gdy do folderu w usłudze DropBox jest dodawany plik, możesz automatycznie skopiować go do folderu w programie SharePoint, aby **poinformować zespół** o tym fakcie.

Jeśli chcesz wiedzieć, co ludzie mówią o Twojej firmie, możesz **utworzyć przepływ**, który będzie **wyzwalany** za każdym razem, gdy ktoś opublikuje tweet z określonym hasztagiem. Przepływ będzie kopiować szczegóły takich tweetów, umieszczać je w bazie danych SQL, na liście programu SharePoint lub nawet w pliku programu Excel przechowywanym w usłudze OneDrive. Wybór zależy od Twoich preferencji. Gromadzone dane mogą posłużyć do utworzenia **akcji** w celu połączenia ich z usługą Power BI, wykrywania trendów i zadawania pytań dotyczących danych.

I wreszcie jednym z najpopularniejszych sposobów wykorzystania przepływów jest **automatyzacja zatwierdzania**. Jeśli na przykład korzystasz z listy programu SharePoint do śledzenia zatwierdzeń w firmie, możesz uruchomić przepływ pracy zatwierdzania.

Więcej pomysłów dotyczących zastosowań możesz znaleźć, przeglądając naszą listę **szablonów** na **stronie docelowej szablonów** (bardziej szczegółowe omówienie znajduje się w następnej sekcji). Masz pomysł na przepływ, którego nie ma na tej liście?  To świetnie!  Możesz tworzyć własne przepływy od podstaw. Jeśli chcesz, możesz się nimi dzielić z naszą społecznością!

## <a name="creating-and-administering-flows"></a>Tworzenie przepływów i zarządzanie nimi
Przepływy można tworzyć i zarządzać nimi, korzystając z aplikacji internetowej lub z aplikacji mobilnej usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows). Niezależnie od platformy możesz łatwo diagnozować problemy, synchronizować dane i wykonywać inne czynności:

* Włączać i wyłączać przepływy bez względu na swoją lokalizację.
* Sprawdzać, które przepływy nie zadziałały.
* Przeglądać szczegółowe raporty historii wykonywania.
* Wyświetlać i filtrować uruchomienia według typu powiadomienia.

## <a name="next-lesson"></a>Następna lekcja
Skoro wiesz już co nieco o usłudze Microsoft Flow (czym jest i co można zrobić za jej pomocą), czas na omówienie elementów przepływu.

