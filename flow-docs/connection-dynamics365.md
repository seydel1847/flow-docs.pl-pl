---
title: Tworzenie przepływu przy użyciu usługi Dynamics 365 (online) | Microsoft Docs
description: Tworzenie przydatnych przepływów pracy przy użyciu połączenia Dynamics 365 i usługi Microsoft Flow
services: ''
suite: flow
documentationcenter: na
author: Mattp123
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/06/2017
ms.author: matp
ms.openlocfilehash: 923fd1fc573586871d506a66aaa2b09d5b5dc9da
ms.sourcegitcommit: f0202f74ba9a2282a670a1751462f598a5ea0ce5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="create-a-flow-by-using-dynamics-365-online"></a>Tworzenie przepływu przy użyciu usługi Dynamics 365 (online)
Za pomocą łącznika usługi Dynamics 365 możesz utworzyć przepływy, które będą inicjowane w momencie wystąpienia zdarzenia w usłudze Dynamics 365 lub innej, a następnie będą wykonywać akcję w usłudze Dynamics 365 lub innej. 

W usłudze Microsoft Flow możesz skonfigurować zautomatyzowane przepływy pracy między ulubionymi aplikacjami, a także synchronizować pliki, uzyskiwać powiadomienia, gromadzić dane i wykonywać wiele innych operacji. Więcej informacji znajduje się w temacie [Wprowadzenie do usługi Microsoft Flow](getting-started.md).

## <a name="create-a-flow-from-a-template"></a>Utwórz przepływ na podstawie szablonu
Możesz utworzyć przepływ, korzystając z jednego z wielu dostępnych szablonów, np. poniższych:

* Po utworzeniu obiektu w usłudze Dynamics 365 utwórz element listy w programie SharePoint.
* Utwórz rekordy potencjalnych klientów usługi Dynamics 365 na podstawie tabeli programu Excel.
* Skopiuj konta usługi Dynamics 365 do klientów w usłudze Dynamics 365 do wykonania operacji.

Aby utworzyć przepływ na podstawie szablonu, wykonaj następujące kroki.

1. Zaloguj się do [witryny sieci Web usługi Microsoft Flow](https://flow.microsoft.com/).
2. Kliknij lub naciśnij pozycję **Usługi**, a następnie kliknij lub naciśnij opcję **Dynamics 365**.
3. Dostępnych jest kilka szablonów. Aby rozpocząć, wybierz szablon, którego chcesz użyć.

## <a name="create-a-task-from-a-lead"></a>Tworzenie zadania na podstawie potencjalnego klienta
Jeśli nie ma dostępnego szablonu spełniającego dane wymagania, utwórz szablon od podstaw. W tym przewodniku zawarto informacje dotyczące tworzenia zadania w usłudze Dynamics 365 za każdym razem, gdy w usłudze Dynamics 365 zostaje utworzony potencjalny klient.

1. Zaloguj się do [witryny sieci Web usługi Microsoft Flow](https://flow.microsoft.com/).
2. Kliknij lub naciśnij pozycję **Moje przepływy**, a następnie kliknij lub naciśnij pozycję **Utwórz z pustego**.
3. Na liście wyzwalaczy przepływu kliknij lub naciśnij pozycję **Dynamics 365 — podczas tworzenia rekordu**.
4. Jeśli zostanie wyświetlony monit, zaloguj się do usługi Dynamics 365.
5. W obszarze **Nazwa organizacji** wybierz wystąpienie usługi Dynamics 365, którego ma nasłuchiwać przepływ.
6. W obszarze **Nazwa jednostki** wybierz jednostkę, której chcesz nasłuchiwać. Będzie ona działać jak wyzwalacz inicjujący przepływ.
   
     Na potrzeby tego przewodnika wybierz opcję **Potencjalni klienci**.
   
    ![Szczegóły przepływu](./media/connection-dynamics365/flow-details.png)
7. Kliknij lub naciśnij przycisk **Nowy krok**, a następnie kliknij lub naciśnij przycisk **Dodaj akcję**.
8. Kliknij lub naciśnij pozycję **Dynamics 365 — utwórz nowy rekord**.
9. W obszarze **Nazwa organizacji** wybierz wystąpienie usługi Dynamics 365, w którym przepływ ma utworzyć rekord. Należy zauważyć, że nie musi to być to samo wystąpienie, z którego jest wyzwalane zdarzenie.
10. W obszarze **Nazwa jednostki** wybierz jednostkę, która utworzy rekord po wystąpieniu zdarzenia.
    
     Na potrzeby tego przewodnika wybierz opcję **Zadania**.
11. Pojawi się okno **Podmiot**. Po kliknięciu lub dotknięciu okna pojawi się okienko zawartości dynamicznej, w którym możesz wybrać jedno z poniższych pól.
    
    * **Nazwisko**. Jeśli wybierzesz to pole, po utworzeniu zadania do pola **Podmiot** zadania zostanie wstawione nazwisko potencjalnego klienta.
    * **Temat**. Jeśli wybierzesz to pole, po utworzeniu zadania do pola **Podmiot** zadania zostanie wstawione pole **Temat**.
    
    Na potrzeby tego przewodnika wybierz opcję **Temat**.
    
    ![Dodawanie tematu przepływu](./media/connection-dynamics365/flow-addtopic.png)
    
    > **Porada:** w okienku zawartości dynamicznej kliknij lub naciśnij pozycję **Zobacz więcej**, aby wyświetlić więcej pól skojarzonych z jednostką. Przykładowo możesz wypełnić pole **Podmiot** zadania polem **Nazwa firmy**, **Klient**, **Opis** lub **E-mail** potencjalnego klienta.
    > 
    > 
12. Kliknij lub naciśnij pozycję **Utwórz przepływ**.

## <a name="create-a-wunderlist-task-from-a-dynamics-365-task"></a>Tworzenie zadania programu Wunderlist na podstawie zadania usługi Dynamics 365
W tym przewodniku zawarto informacje dotyczące tworzenia zadania w programie [Wunderlist](https://www.wunderlist.com) za każdym razem, gdy w usłudze Dynamics 365 zostaje utworzone zadanie. Wunderlist jest usługą internetową, dzięki której możesz tworzyć listy zadań do wykonania, dodawać przypomnienia lub śledzić zadania.

1. Zaloguj się do [witryny sieci Web usługi Microsoft Flow](https://flow.microsoft.com/).
2. Kliknij lub naciśnij pozycję **Moje przepływy**, a następnie kliknij lub naciśnij pozycję **Utwórz z pustego**.
3. Na liście wyzwalaczy przepływu kliknij lub naciśnij pozycję **Dynamics 365 — podczas tworzenia rekordu**.
4. W obszarze **Nazwa organizacji** wybierz wystąpienie usługi Dynamics 365, którego ma nasłuchiwać przepływ.
5. W obszarze **Nazwa jednostki** wybierz jednostkę, której chcesz nasłuchiwać. Będzie ona działać jak wyzwalacz inicjujący przepływ.
   
    Na potrzeby tego przewodnika wybierz opcję **Zadania**.
6. Kliknij lub naciśnij przycisk **Nowy krok**, a następnie kliknij lub naciśnij przycisk **Dodaj akcję**.
7. Wpisz *utwórz zadanie*, a następnie kliknij lub naciśnij pozycję **Wunderlist — utwórz zadanie**.
8. W obszarze **Identyfikator listy** wybierz opcję **skrzynka odbiorcza**.
9. W obszarze **Tytuł** wybierz opcję **Podmiot** w okienku zawartości dynamicznej.
10. Kliknij lub naciśnij pozycję **Utwórz przepływ**.  

## <a name="specify-advanced-options"></a>Określanie opcji zaawansowanych
Po dodaniu kroku do przepływu możesz kliknąć lub nacisnąć pozycję **Pokaż opcje zaawansowane**, aby dodać zapytanie filtru lub ustalania kolejności, które kontroluje sposób filtrowania danych w przepływie.

Przykładowo możesz użyć zapytania filtru, aby odebrać tylko aktywne kontakty, a następnie uporządkować je według nazwiska. Aby to zrobić, wprowadź zapytanie filtru OData **statuscode eq 1** i wybierz pozycję **Nazwisko** w okienku zawartości dynamicznej. Aby uzyskać więcej informacji o zapytaniach filtru i ustalania kolejności, zobacz [MSDN: $filter](https://msdn.microsoft.com/library/gg309461.aspx#Anchor_1) i [MSDN: $orderby](https://msdn.microsoft.com/library/gg309461.aspx#Anchor_2).

  ![Zapytanie ustalania kolejności przepływu](./media/connection-dynamics365/flow-orderby-query.png)

### <a name="best-practices-when-using-advanced-options"></a>Najlepsze rozwiązania związane z używaniem opcji zaawansowanych
Gdy dodajesz wartość do pola, musisz dopasować ją do typu pola, niezależnie od tego, czy wpisujesz wartość, czy wybierasz jedną z wartości w okienku zawartości dynamicznej.

| Typ pola | Sposób użycia | Gdzie można to znaleźć | Nazwa | Typ danych |
| --- | --- | --- | --- | --- |
| Pola tekstowe |Pola tekstowe wymagają jednego wiersza tekstu lub zawartości dynamicznej, która jest polem tekstowym. Przykładowo będą to pola **Kategoria** i **Podkategoria**. |**Ustawienia** > **Dostosowania** > **Dostosuj system** > **Jednostki** > **Zadanie** > **Pola** |**category** |**Jeden wiersz tekstu** |
| Pola liczb całkowitych |Niektóre pola wymagają liczby całkowitej lub zawartości dynamicznej, która jest polem wartości całkowitych. Przykładowo będą to pola **Procent wykonania** i **Czas trwania**. |**Ustawienia** > **Dostosowania** > **Dostosuj system** > **Jednostki** > **Zadanie** > **Pola** |**percentcomplete** |**Liczba całkowita** |
| Pola daty |Niektóre pola wymagają daty wprowadzonej w formacie mm/dd/rrrr lub zawartości dynamicznej, która jest polem daty. Przykładowo będą to pola **Utworzono**, **Data rozpoczęcia**, **Rozpoczęcie rzeczywiste**, **Ostatni czas wstrzymania**, **Zakończenie rzeczywiste** oraz **Data ukończenia**. |**Ustawienia** > **Dostosowania** > **Dostosuj system** > **Jednostki** > **Zadanie** > **Pola** |**createdon** |**Data i godzina** |
| Pola, które wymagają identyfikatora rekordu i typu wyszukiwania |Niektóre pola odwołujące się do innego rekordu jednostki wymagają zarówno identyfikatora rekordu, jak i typu wyszukiwania. |**Ustawienia** > **Dostosowania** > **Dostosuj system** > **Jednostki** > **Konto** > **Pola** |**accountid** |**Klucz podstawowy** |

### <a name="more-examples-of-fields-that-require-both-a-record-id-and-lookup-type"></a>Więcej przykładów pól, które wymagają identyfikatora rekordu i typu wyszukiwania
W ramach uzupełnienia poprzedniej tabeli oto więcej przykładów pól, które nie działają z wartościami wybranymi z listy zawartości dynamicznej. Zamiast tego pola te wymagają wprowadzenia identyfikatora rekordu i typu wyszukiwania w pola w usłudze PowerApps.

* **Właściciel** i **Typ właściciela**.
  
  * Pole **Właściciel** musi być prawidłowym identyfikatorem rekordu użytkownika lub zespołu.
  * Pole **Typ właściciela** musi mieć wartość **użytkownicy systemowi** lub **zespoły**.
* **Klient** i **Typ klienta**.
  
  * Pole **Klient** musi być prawidłowym identyfikatorem rekordu konta lub kontaktu.
  * Pole **Typ klienta** musi mieć wartość **konta** lub **kontakty**.
* **Dotyczy** i **Typ obiektu Dotyczy**.
  
  * Pole **Dotyczy** musi być prawidłowym identyfikatorem rekordu, np. identyfikatorem rekordu konta lub kontaktu.
  * Pole **Typ obiektu Dotyczy** musi być typem wyszukiwania dla rekordu, np. **konta** lub **kontakty**.

W tym przykładzie rekord konta, który odpowiada identyfikatorowi rekordu, zostaje dodany do pola **Dotyczy** zadania.

  ![Identyfikator rekordu i typ konta przepływu](./media/connection-dynamics365/flow-recordid-account.png)

W tym przykładzie zadanie zostaje przypisane do określonego użytkownika w oparciu o identyfikator rekordu użytkownika.

  ![Identyfikator rekordu i typ użytkownika przepływu](./media/connection-dynamics365/flow-recordid-user.png)

Aby znaleźć identyfikator rekordu, zobacz sekcję [Znajdowanie identyfikatora rekordu](#find-the-records-id) w dalszej części tego tematu.

> **Ważne:** pola nie powinny zawierać wartości, jeśli mają opis „Tylko do użytku wewnętrznego”. Pola te obejmują między innymi następujące: **Pokonana ścieżka**, **Dodatkowe parametry** i **Numer wersji reguły strefy czasowej**.
> 
> 

## <a name="find-the-records-id"></a>Znajdowanie identyfikatora rekordu
1. W aplikacji sieci Web usługi Dynamics 365 otwórz rekord, np. rekord konta.
2. Na pasku narzędzi Akcje kliknij lub naciśnij pozycję **Otwórz w nowym oknie**
   ![Otwórz rekord w nowym oknie](./media/connection-dynamics365/popout.png) (ewentualnie kliknij lub naciśnij pozycję **WYŚLIJ LINK POCZTĄ E-MAIL**, aby skopiować pełny adres URL do domyślnego programu poczty e-mail).
   
    Na pasku adresu przeglądarki sieci Web adres URL zawiera identyfikator rekordu między znakami kodowania %7b i %7d.
   
   ![Identyfikator rekordu](./media/connection-dynamics365/recordid.png)

## <a name="related-topics"></a>Tematy pokrewne
[Rozwiązywanie problemów z przepływem](fix-flow-failures.md)

[Usługa Flow w organizacji — pytania i odpowiedzi](organization-q-and-a.md)

[Często zadawane pytania](frequently-asked-questions.md)

