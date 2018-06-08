---
title: Informacje o operacjach na danych | Microsoft Docs
description: Naucz się wykonywać operacje takie jak tworzenie tabeli HTML, tworzenie tabeli CSV oraz tworzenie, łączenie, wybieranie i filtrowanie tablicy przy użyciu usługi Microsoft Flow.
services: ''
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/02/2017
ms.author: deonhe
ms.openlocfilehash: aa3f61d09cb5e9b8d07124838883da9b5b9794ab
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "23440914"
---
# <a name="use-data-operations-with-microsoft-flow"></a>Używanie operacji na danych w usłudze Microsoft Flow
W tym przewodniku poznasz niektóre popularne operacje na danych w usłudze Microsoft Flow — takie jak tworzenie, łączenie, wybieranie i filtrowanie tablicy, tworzenie tabeli oraz analizowanie kodu JSON — przy użyciu których można manipulować danymi podczas tworzenia przepływu.

## <a name="prerequisites"></a>Wymagania wstępne
* Dostęp do usługi Microsoft Flow.
* Narzędzie takie jak [PostMan](https://www.getpostman.com/postman) umożliwiające wysyłanie do przepływu żądań HTTP POST z tablicą JSON.

## <a name="use-the-compose-action"></a>Używanie akcji tworzenia
Używając akcji **Operacje na danych — Utwórz** (utwórz), możesz uniknąć wielokrotnego wprowadzania tych samych danych podczas tworzenia przepływu. Jeśli na przykład podczas tworzenia przepływu chcesz kilkukrotnie wprowadzić tablicę cyfr: ````[0,1,2,3,4,5,6,7,8,9]````, możesz za pomocą akcji tworzenia zapisać tablicę w następujący sposób:

1. Wyszukaj pozycję **Utwórz**, a następnie wybierz akcję **Operacje na danych — Utwórz** (utwórz).
   
    ![wyszukiwanie i wybieranie akcji tworzenia](./media/data-operations/search-select-compose.png)
2. Wprowadź tablicę do pola **Dane wejściowe**, do którego chcesz się później odwołać:
   
    ![konfigurowanie akcji tworzenia](./media/data-operations/add-array-compose.png)

> [!TIP]
> Aby ułatwić późniejsze odwołanie, zmień nazwę karty **Utwórz**, klikając tekst „Utwórz” na pasku tytułu karty **Utwórz**.
> 
> 

Gdy konieczne będzie uzyskanie dostępu do zawartości akcji tworzenia, można to zrobić za pośrednictwem tokenu **Dane wyjściowe** na liście **Dodaj zawartość dynamiczną z aplikacji i łączników używanych w tym przepływie**, wykonując następujące czynności:

1. Dodaj akcję taką jak **Operacje na danych — Połącz**.
2. Wybierz kontrolkę, do której chcesz dodać zawartość zapisaną w akcji tworzenia.
   
    Zostanie otwarta lista **Dodaj zawartość dynamiczną z aplikacji i łączników używanych w tym przepływie**.
3. Z listy **Dodaj zawartość dynamiczną z aplikacji i łączników używanych w tym przepływie** wybierz token **Dane wyjściowe** znajdujący się w kategorii **Utwórz** karty **Zawartość dynamiczna**.
   
    ![używanie danych wyjściowych z akcji tworzenia](./media/data-operations/use-compose-output.png)

## <a name="use-the-join-action"></a>Używanie akcji połączenia
Przy użyciu akcji **Operacje na danych — Połącz** (połącz) możesz rozdzielić tablicę dowolnym separatorem. Załóżmy na przykład, że przepływ otrzymuje żądanie sieciowe zawierające następującą tablicę adresów e-mail: ````["d@example.com", "k@example.com", "dal@example.com"]````. Jednak Twój program poczty e-mail wymaga, aby adresy znajdowały się w jednym ciągu rozdzielonym średnikami. Aby to zrobić, przy użyciu akcji **Operacje na danych — Połącz** (połącz) zmień przecinek oddzielający na średnik „;”, wykonując następujące czynności:

1. Dodaj nową akcję, wyszukaj pozycję **Połącz**, a następnie wybierz akcję **Operacje na danych — Połącz** (połącz).
   
    ![wyszukiwanie i wybieranie akcji połączenia](./media/data-operations/search-select-join.png)
2. Wprowadź tablicę w polu **Od**, a następnie w polu **Połącz przy użyciu** wprowadź nowy ogranicznik, którego chcesz używać.
   
    Oto średnik (;) użyty jako nowy organicznik.
   
    ![konfigurowanie akcji połączenia](./media/data-operations/add-array-join.png)
3. Zapisz przepływ i uruchom go.
4. Po zakończeniu przebiegu przepływu dane wyjściowe akcji **Operacje na danych — Połącz** będą wyglądać następująco:
   
    ![dane wyjściowe akcji połączenia](./media/data-operations/join-output.png)

## <a name="use-the-select-action"></a>Używanie akcji wybierania
Przy użyciu akcji **Operacje na danych — Wybierz** (wybierz) możesz zmienić kształt obiektów w tablicy. Na przykład możesz dodać lub usunąć elementy w każdym obiekcie w tablicy bądź zmienić nazwę tych elementów.

> [!NOTE]
> Przy użyciu akcji wybierania możesz dodawać lub usuwać elementy, jednak nie możesz zmienić liczby obiektów w tablicy.
> 
> 

Na przykład możesz użyć akcji wybierania, jeśli dane są wprowadzane do przepływu za pośrednictwem żądania sieciowego w następującym formacie:

````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]````

i chcesz zmienić kształt przychodzących danych, zmieniając wartości „first” na „FirstName” i „last” na „LastName” oraz dodając nowy element członkowski o nazwie „FamilyName” łączący wartości „first” i „last” (oddzielone spacją):

````[ { "FirstName": "Deon", "FamilyName": "Herb", "FullName": "Deon Herb" }, { "FirstName": "K", "FamilyName": "Herb", "FullName": "K Herb" } ]````.

Aby to zrobić, wykonaj następujące czynności:

1. Dodaj do przepływu akcję **Żądanie / Odpowiedź — Odpowiedź** (żądanie)
2. Wybierz pozycję **Użyj przykładowego ładunku do wygenerowania schematu** z karty **Żądanie**.
3. W wyświetlonym polu wklej próbkę tablicy danych źródłowych, a następnie wybierz przycisk **Gotowe**.
4. Dodaj akcję **Operacje na danych — Wybierz** (wybierz), a następnie skonfiguruj ją zgodnie z poniższym obrazem.
   
    ![konfigurowanie akcji wybierania](./media/data-operations/select-card.png)
   
   > [!TIP]
   > Dane wyjściowe z akcji wybierania to tablica zawierająca nowo uformowane obiekty. Następnie możesz użyć tej tablicy w dowolnej innej akcji, na przykład omawianej wcześniej akcji **Utwórz**.
   > 
   > 

## <a name="use-the-filter-array-action"></a>Używanie akcji filtrowania tablicy
Przy użyciu akcji **Operacje na danych — Filtruj tablicę** (filtruj tablicę) możesz zmniejszyć liczbę obiektów w tablicy do podzestawu spełniającego określone kryteria.

> [!NOTE]
> Przy użyciu akcji filtrowania tablicy nie można zmienić kształtu obiektów w tablicy. Ponadto w tekście filtrującym jest uwzględniana wielkość liter.
> 
> 

Na przykład możesz użyć akcji filtrowania tablicy na tej tablicy:

````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]````

aby utworzyć nową tablicę zawierającą tylko obiekty, w których element *first* ma wartość „Deon”.

Zróbmy to.

1. Wyszukaj, a następnie dodaj akcję **Operacje na danych — Filtrowanie tablicy** (filtrowanie tablicy) do przepływu.
2. Skonfiguruj akcję filtrowania tablicy zgodnie z poniższym obrazem.
   
    ![konfigurowanie akcji filtrowania tablicy](./media/data-operations/add-configure-filter-array.png)
3. Zapisz przepływ i uruchom go.
   
    Przy użyciu narzędzia [PostMan](https://www.getpostman.com/postman) możesz wygenerować żądanie sieciowe, które wyśle tablicę JSON do przepływu.
4. Po uruchomieniu przebiegu przepływu — zakładając, że dane wejściowe JSON wyglądają jak ta tablica:
   
    ````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]```` —
   
    dane wyjściowe będą wyglądać jak ta tablica (zauważ, że w danych wyjściowych akcji uwzględnione są tylko obiekty, w których element *first* ma wartość „Deon”):
   
    ````[ { "first": "Deon", "last": "Herb" } ]````

## <a name="use-the-create-csv-table-action"></a>Używanie akcji tworzenia tabeli CSV
Przy użyciu akcji **Operacje na danych — Utwórz tabelę CSV** (utwórz tabelę CSV) możesz zmienić dane wejściowe tablicy JSON na tabelę z wartościami rozdzielanymi przecinkami (CSV). Opcjonalnie możesz zachować widoczność nagłówków w danych wyjściowych CSV. Przy użyciu akcji **Utwórz tabelę CSV** możesz na przykład przekonwertować następującą tablicę na tabelę CSV:

````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]````

1. Wyszukaj, dodaj, a następnie skonfiguruj akcję **Operacje na danych — Utwórz tabelę CSV** zgodnie z poniższym obrazem.
   
    ![konfigurowanie akcji tworzenia tabeli CSV](./media/data-operations/create-csv-table.png)
   
    Uwaga: token **Treść** na tym obrazie pochodzi z akcji **Żądanie / Odpowiedź — Żądanie**, jednak można uzyskać dane wejściowe dla akcji **Utwórz tabelę CSV** z danych wyjściowych poprzedniej akcji w przepływie lub możesz wprowadzić te dane bezpośrednio w polu **Od**.
2. Zapisz przepływ i uruchom go.
   
    Po uruchomieniu przebiegu przepływu dane wyjściowe akcji **Utwórz tabelę CSV** będą wyglądać jak na poniższym obrazie:
   
    ![dane wyjściowe akcji tworzenia tabeli CSV](./media/data-operations/create-csv-table-output.png)

## <a name="use-the-create-html-table-action"></a>Używanie akcji tworzenia tabeli HTML
Przy użyciu akcji **Operacje na danych — Utwórz tabelę HTML** możesz zmienić dane wejściowe tablicy JSON na tabelę HTML. Opcjonalnie możesz zachować widoczność nagłówków w danych wyjściowych HTML.

Aby to zrobić, zapoznaj się ze szczegółowym przykładem, wykonując czynności opisane w [sekcji dotyczącej tworzenia tabeli CSV](#use-the-create-csv-table-action). Pamiętaj, aby użyć akcji **Operacje na danych — Utwórz tabelę HTML**, a nie akcji **Operacje na danych — Utwórz tabelę CSV**.

> [!TIP]
> Jeśli zamierzasz wysłać tabelę HTML za pośrednictwem poczty e-mail, pamiętaj, aby w akcji poczty e-mail zaznaczyć opcję „IsHtml”.
> 
> 

