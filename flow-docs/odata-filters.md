---
title: Filtrowanie i kopiowanie danych | Microsoft Docs
description: Informacje na temat filtrowania i kopiowania danych ze źródła do miejsca docelowego przy użyciu usługi Microsoft Flow
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
ms.date: 09/21/2017
ms.author: deonhe
ms.openlocfilehash: 7c182328c341043ffc155a679f39bcbc2130a0bc
ms.sourcegitcommit: d00c10759d4afb54517a0b1032f8d0a509006d5b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="filter-and-copy-data-with-microsoft-flow"></a>Filtrowanie i kopiowanie danych przy użyciu usługi Microsoft Flow
W tym przewodniku przedstawiono sposób tworzenia przepływu, który monitoruje źródło pod kątem nowych lub zmienionych elementów, a następnie kopiuje te zmiany do miejsca docelowego. Taki przepływ możesz utworzyć, jeśli Twoi użytkownicy wprowadzają dane w jednej lokalizacji, a zespół potrzebuje ich w innej lokalizacji lub w innym formacie.

W tym przewodniku dane są kopiowane z [listy](https://support.office.com/article/SharePoint-lists-I-An-introduction-f11cd5fe-bc87-4f9e-9bfe-bbd87a22a194) programu Microsoft SharePoint (źródło) do tabeli w usłudze [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) (miejsce docelowe), ale dane można kopiować między dowolnymi z ponad [150 usług](https://flow.microsoft.com/connectors/) obsługiwanych przez usługę Microsoft Flow.

> [!IMPORTANT]
> Zmiany wprowadzane w miejscu docelowym nie są kopiowane do źródła, ponieważ synchronizacje dwukierunkowe nie są obsługiwane. Jeśli spróbujesz skonfigurować synchronizację dwukierunkową, utworzysz pętlę nieskończoną, w której zmiany będą bez końca przesyłane między źródłem i miejscem docelowym.
> 
> 

## <a name="prerequisites"></a>Wymagania wstępne
* Dostęp do źródła danych i miejsca docelowego. W tym przewodniku nie przedstawiono procedury tworzenia źródła i miejsca docelowego.
* Należy mieć dostęp do usługi [Microsoft Flow](https://flow.microsoft.com).
* Podstawowa wiedza na temat sposobu przechowywania danych.
* Znajomość podstaw tworzenia przepływów. Możesz przejrzeć informacje na temat dodawania [akcji, wyzwalaczy](multi-step-logic-flow.md#add-another-action) i [warunków](add-condition.md). W następujących krokach założono, że wiesz, jak wykonywać te akcje.

> [!TIP]
> Nie wszystkie nazwy kolumn w źródle i miejscu docelowym muszą być zgodne, ale musisz podać dane we wszystkich *wymaganych* kolumnach, gdy wstawiasz lub aktualizujesz element. Usługa Microsoft Flow identyfikuje wymagane pola za Ciebie.
> 
> 

## <a name="quick-overview-of-the-steps"></a>Szybki przegląd procedury
Jeśli wiesz, jak używać usługi Microsoft Flow, wykonaj następującą szybką procedurę, aby skopiować dane z jednego źródła danych do drugiego:

1. Określ źródło, które będziesz monitorować, i miejsce docelowe, do którego będą kopiowane zmienione dane. Upewnij się, że masz dostęp do obu miejsc.
2. Określ co najmniej jedną kolumnę, która unikatowo identyfikuje elementy w źródle i miejscu docelowym. W następującym przykładzie używana jest kolumna **Tytuł**, ale można użyć dowolnej kolumny.
3. Skonfiguruj wyzwalacz, który monitoruje źródło pod kątem zmian.
4. Przeszukaj miejsce docelowe, aby ustalić, czy zmieniony element istnieje.
5. Użyj **warunku** jak poniżej:
   * Jeśli nowy lub zmieniony element nie istnieje w miejscu docelowym, utwórz go.
   * Jeśli nowy lub zmieniony element istnieje w miejscu docelowym, zaktualizuj go.
6. Wyzwól przepływ i upewnij się, że nowe lub zmienione elementy są kopiowane ze źródła do miejsca docelowego.

> [!NOTE]
> Jeśli wcześniej nie utworzono połączenia z programem SharePoint lub usługą Azure SQL Database, po wyświetleniu monitu o zalogowanie postępuj zgodnie z instrukcjami.
> 
> 

Poniżej szczegółowo przedstawiono procedurę tworzenia przepływu.

## <a name="monitor-the-source-for-changes"></a>Monitorowanie źródła pod kątem zmian
1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com) i wybierz pozycję **Moje przepływy** > **Utwórz z pustego**.
2. Wyszukaj ciąg **SharePoint**, a następnie z listy wyzwalaczy wybierz wyzwalacz **SharePoint — Po utworzeniu lub zmodyfikowaniu elementu**.
3. Wprowadź **Adres witryny**, a następnie wybierz pozycję **Nazwa listy** na karcie **Po utworzeniu lub zmodyfikowaniu elementu**.
   
    Podaj wartości **Adres witryny** i **Nazwa listy** dla listy programu SharePoint, która jest monitorowana przez przepływ pod kątem nowych lub zaktualizowanych elementów.
   
    ![Konfigurowanie wyzwalacza SharePoint](media/odata-filters/configure-sharepoint-trigger.png)

## <a name="search-the-destination-for-the-new-or-changed-item"></a>Przeszukiwanie miejsca docelowego pod kątem nowego lub zmienionego elementu
Aby przeszukać miejsce docelowe pod kątem nowego lub zmienionego elementu, używana jest akcja **SQL Server — Pobierz wiersze**.

1. Wybierz kolejno pozycje **Nowy krok** > **Dodaj akcję**.
2. Wyszukaj ciąg **Pobierz wiersze**, wybierz pozycję **SQL Server — Pobierz wiersze**, a następnie z listy **Nazwa tabeli** wybierz tabelę, którą chcesz monitorować.
3. Wybierz pozycję **Pokaż opcje zaawansowane**.
4. W polu **Zapytanie filtru** wprowadź wartość **Title eq '**, z listy zawartości dynamicznej wybierz token **Tytuł**, a następnie wprowadź znak **'**.
   
    W poprzednim kroku założono, że sprawdzana jest zgodność tytułów wierszy w źródle i miejscu docelowym.
   
    Karta **Pobierz wiersze** powinna teraz wyglądać jak na poniższym obrazie:
   
    ![Próba pobrania elementu z docelowej bazy danych](media/odata-filters/configure-sql-get-rows-action.png)

## <a name="check-if-the-new-or-changed-item-was-found"></a>Sprawdzanie, czy znaleziono nowy lub zmieniony element
Wybierz pozycję **Nowy krok** > **Dodaj warunek**, aby otworzyć kartę **Warunek**.

Na karcie Warunek:

1. Zaznacz pole po lewej stronie.
   
    Zostanie otwarta lista **Dodaj zawartość dynamiczną z aplikacji i łączników używanych w tym przepływie**.
2. Wybierz pozycję **wartość** z kategorii **Pobierz wiersze**.
   
   > [!TIP]
   > Upewnij się, że została wybrana pozycja **wartość** z kategorii **Pobierz wiersze**. Nie wybieraj pozycji **wartość** z kategorii **Po utworzeniu lub zmodyfikowaniu elementu**.
   > 
   > 
3. Z listy w środkowym polu wybierz pozycję **jest równe**.
4. W polu po prawej stronie wprowadź wartość **0** (zero).
   
    Teraz karta **Warunek** wygląda następująco:
   
    ![Konfigurowanie warunku](media/odata-filters/configure-condition.png)
5. Wybierz pozycję **Edytuj w trybie zaawansowanym**.
   
    Po otwarciu trybu zaawansowanego w polu zostanie wyświetlone wyrażenie **\@equals(body('Get_rows')?['value'], 0)**. Zmodyfikuj to wyrażenie przez dodanie funkcji **length()** wokół funkcji **body('Get_items')?['value']**. Całe wyrażenie wygląda teraz następująco: **@equals(length(body('Get_rows')?['value']), 0)**
   
    Teraz karta **Warunek** wygląda następująco:
   
    ![Konfigurowanie warunku](media/odata-filters/configure-condition-add-length.png)
   
   > [!TIP]
   > Dzięki dodaniu funkcji **length()** przepływ może sprawdzić listę **wartość** i określić, czy zawiera jakieś elementy.
   > 
   > 

Gdy przepływ pobiera elementy z miejsca docelowego, istnieją dwa możliwe wyniki.

| Wynik | Następny krok |
| --- | --- |
| Element istnieje |[Zaktualizuj element](odata-filters.md#update-the-item-in-the-destination) |
| Element nie istnieje |[Utwórz nowy element](odata-filters.md#create-the-item-in-the-destination) |

> [!NOTE]
> Obrazy kart **Wstaw wiersz** i **Aktualizuj wiersz** pokazane poniżej mogą różnić się od Twoich, ponieważ na tych kartach są wyświetlane nazwy kolumn w tabeli usługi Azure SQL Database, które są używane w przepływie.
> 
> 

## <a name="create-the-item-in-the-destination"></a>Tworzenie elementu w miejscu docelowym
Jeśli element nie istnieje w miejscu docelowym, utwórz go za pomocą akcji **SQL Server — Wstaw wiersz**.

W gałęzi **Jeśli tak** elementu **Warunek**:

1. Wybierz pozycję **Dodaj akcję**, wyszukaj ciąg **wstaw wiersz**, a następnie wybierz akcję **SQL Server — Wstaw wiersz**.
   
    Zostanie otwarta karta **Wstaw wiersz**.
2. Z listy **Nazwa tabeli** wybierz tabelę, do której nowy element zostanie wstawiony.
   
    Karta **Wstaw wiersz** rozszerzy się i wyświetli wszystkie pola w wybranej tabeli. Pola oznaczone gwiazdką (*) są wymagane i muszą być wypełnione, aby wiersz był prawidłowy.
3. Zaznacz każde pole, które chcesz wypełnić, a następnie wprowadź dane.
   
    Dane możesz wprowadzić ręcznie, wybrać jeden lub kilka tokenów z listy **Zawartość dynamiczna** albo wprowadzić w polach dowolną kombinację tekstu i tokenów.
   
    Teraz karta **Wstaw wiersz** wygląda następująco:
   
    ![Konfigurowanie warunku](media/odata-filters/insert-row.png)

## <a name="update-the-item-in-the-destination"></a>Aktualizowanie elementu w miejscu docelowym
Jeśli element istnieje w miejscu docelowym, zaktualizuj go za pomocą zmian.

1. Dodaj akcję **SQL Server — Aktualizuj wiersz** do gałęzi **Jeśli nie** na karcie **Warunek**.
2. Postępuj zgodnie z instrukcjami w sekcji tego dokumentu dotyczącej [tworzenia elementu](odata-filters.md#create-the-item-in-the-destination), aby wypełnić pola tabeli.
   
    ![Wyświetlanie środowisk](media/odata-filters/update-row.png)
3. W górnej części strony, w polu **Nazwa przepływu** wprowadź nazwę przepływu, a następnie wybierz pozycję **Utwórz przepływ**, aby go zapisać.
   
    ![Nadawanie nazwy przepływowi](media/odata-filters/give-the-flow-a-name.png)

Teraz zawsze, gdy element na liście programu SharePoint (źródło) zostanie zmieniony, przepływ zostanie wyzwolony i wstawi nowy element lub zaktualizuje już istniejący element w usłudze Azure SQL Database (miejsce docelowe).

> [!NOTE]
> Przepływ nie zostanie wyzwolony, gdy element zostanie usunięty ze źródła. Jeśli jest to ważne, rozważ dodanie oddzielnej kolumny wskazującej, kiedy dany element nie jest już potrzebny.
> 
> 

## <a name="learn-more"></a>Dowiedz się więcej
Używaj [operacji na danych](data-operations.md) w swoich przepływach.

