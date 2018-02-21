---
title: "Tworzenie pętli zatwierdzania za pomocą usługi Common Data Service | Microsoft Docs"
description: "Utwórz jednostkę, przepływ i aplikację, które współpracują ze sobą tak, aby recenzenci mogli zatwierdzać lub odrzucać pliki dodane do usługi Dropbox."
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/22/2016
ms.author: stepsic
ms.openlocfilehash: f56b109cc0263c8464d6d7475421ab32af8888d5
ms.sourcegitcommit: f3261717768177e03e825c0dd2e3ba736dc9b94d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2018
---
# <a name="build-an-approval-loop-by-using-microsoft-flow-and-the-microsoft-common-data-service"></a>Tworzenie pętli zatwierdzania za pomocą usługi Microsoft Flow i usługi Microsoft Common Data Service
Usługa Common Data Service umożliwia tworzenie przepływów, których informacje są przechowywane w bazie danych niezależnej od przepływu. Najlepszym przykładem są zatwierdzenia. Jeśli stan zatwierdzania zostanie zapisany w jednostce, przepływ może działać na jego podstawie.

W tym przykładzie utworzysz proces zatwierdzania, który rozpoczyna się, gdy użytkownik doda plik do usługi Dropbox. Po dodaniu pliku informacja o nim znajdzie się w aplikacji, gdzie recenzent może zatwierdzić lub odrzucić zmianę. Gdy recenzent zaakceptuje lub odrzuci zmianę, wysyłana jest wiadomość e-mail z powiadomieniem, a odrzucone pliki są usuwane z usługi Dropbox.

Wykonując kroki opisane w tej sekcji, utworzysz następujące elementy:

* **Jednostka niestandardowa**, która będzie zawierać informacje o każdym pliku dodanym do usługi Dropbox i o tym, czy plik jest w stanie zatwierdzonym, odrzuconym, czy oczekującym.
* **Przepływ**, który dodaje informacje do jednostki niestandardowej po dodaniu pliku do usługi Dropbox, wysyła wiadomość e-mail, gdy plik zostanie zatwierdzony lub odrzucony, oraz usuwa odrzucone pliki. Za pomocą tych kroków pokazano, jak utworzyć taki przepływ od początku, ale podobny przepływ możesz utworzyć na podstawie szablonu.
* **Aplikacja**, w której recenzent może zatwierdzać lub odrzucać pliki dodane do usługi Dropbox. Za pomocą usługi PowerApps możesz automatycznie wygenerować tę aplikację na podstawie pól w jednostce niestandardowej.

**Wymagania wstępne**

* Zarejestruj się w programie [Microsoft Flow](sign-up-sign-in.md) oraz w usłudze [PowerApps](https://powerapps.microsoft.com/tutorials/signup-for-powerapps/).
* Utwórz połączenia z usługą Dropbox i Office 365 Outlook zgodnie z opisem w temacie [Manage your connections](https://powerapps.microsoft.com/tutorials/add-manage-connections/) (Zarządzanie połączeniami).

## <a name="build-the-entity"></a>Tworzenie jednostki
1. Zaloguj się w witrynie [powerapps.com](https://web.powerapps.com).
2. Jeśli lewy pasek nawigacyjny nie jest domyślnie wyświetlany, kliknij lub naciśnij ikonę z trzema liniami poziomymi w lewym górnym rogu.
   
    ![Otwieranie lewego paska nawigacyjnego](./media/common-data-model-approve/hamburger-icon.png)
3. Na lewym pasku nawigacyjnym kliknij lub naciśnij pozycję **Zarządzaj**, a następnie kliknij lub naciśnij pozycję **Jednostki**.
   
    ![Zarządzanie jednostkami](./media/common-data-model-approve/manage-entities.png)
4. Jeśli zostanie wyświetlony monit, kliknij lub naciśnij przycisk **Utwórz moją bazę danych**.
   
    ![Tworzenie bazy danych](./media/common-data-model-approve/create-database.png)
5. W pobliżu prawego górnego rogu kliknij lub naciśnij przycisk **Nowa jednostka**.
   
    ![Tworzenie jednostki](./media/common-data-model-approve/new-entity.png)
   
    Jeśli okno przeglądarki nie jest zmaksymalizowane, ten przycisk może zostać wyświetlony w innym miejscu.
6. W obszarze **Nazwa jednostki** podaj unikatową nazwę jednostki. Nazwa nie może zawierać spacji.
   
    Aby postępować dokładnie zgodnie z przykładem, podaj nazwę **PrzeglądPlikówDropbox**.
   
    ![Podawanie nazwy jednostki](./media/common-data-model-approve/entity-name.png)
7. W obszarze **Nazwa wyświetlana** podaj przyjazną nazwę.
   
    ![Podawanie nazwy wyświetlanej](./media/common-data-model-approve/display-name.png)
8. Kliknij lub naciśnij przycisk **Dalej**.
   
    ![Przycisk Dalej](./media/common-data-model-approve/next-button.png)

## <a name="add-fields-to-the-entity"></a>Dodawanie pól do jednostki
1. W pobliżu prawego górnego rogu kliknij lub naciśnij przycisk **Dodaj pole**.
   
    ![Dodawanie pola](./media/common-data-model-approve/add-field.png)
2. W pustym wierszu, który pojawi się w dolnej części listy pól, ustaw właściwości pola **Osoba zatwierdzająca**. (Po ustawieniu tych właściwości możesz przejść do następnej kolumny, naciskając klawisz Tab).
   
   * W kolumnie **Nazwa wyświetlana** wpisz **Osoba zatwierdzająca**.
   * W kolumnie **Nazwa** wpisz **AdresEmailOsobyZatwierdzającej**.
   * W kolumnie **Typ** kliknij lub naciśnij opcję **Adres e-mail**.
   * W kolumnie **Wymagane** zaznacz pole wyboru.
     
     ![Pole Osoba zatwierdzająca](./media/common-data-model-approve/approver-field.png)
3. W kolejnym wierszu ustaw właściwości pola **Stan**:
   
   * W kolumnie **Nazwa wyświetlana** wpisz **Stan**.
   * W kolumnie **Nazwa** wpisz **Stan**.
   * W kolumnie **Typ** kliknij lub naciśnij opcję **Tekst**.
   * W kolumnie **Właściwości** pozostaw wartość domyślną.
   * W kolumnie **Wymagane** zaznacz pole wyboru.
     
     ![Pole Stan](./media/common-data-model-approve/status-field.png)
4. W kolejnym wierszu ustaw właściwości pola **IDPliku**:
   
   * W kolumnie **Nazwa wyświetlana** wpisz **Identyfikator pliku**.
   * W kolumnie **Nazwa** wpisz **IDPliku**.
   * W kolumnie **Typ** kliknij lub naciśnij opcję **Tekst**.
   * W kolumnie **Właściwości** pozostaw wartość domyślną.
   * W kolumnie **Unikatowe** zaznacz pole wyboru.
   * W kolumnie **Wymagane** zaznacz pole wyboru.
     
     ![Pole IDPliku](./media/common-data-model-approve/fileid-field.png)
5. Blisko prawej krawędzi kliknij lub naciśnij przycisk wielokropka (...) dla pola **IDPliku**, a następnie kliknij lub naciśnij pozycję **Ustaw jako pole tytułu**.
   
    ![Ustawianie pola tytułu](./media/common-data-model-approve/set-title-field.png)
6. W pobliżu lewego dolnego rogu kliknij lub naciśnij przycisk **Utwórz**.
   
    ![Tworzenie jednostki](./media/common-data-model-approve/create-button.png)
7. (opcjonalnie) Po ponownym wyświetleniu listy jednostek zmaksymalizuj okno przeglądarki, o ile nie jest jeszcze zmaksymalizowane, a następnie kliknij lub naciśnij nagłówek kolumny **Typ**. Lista jest posortowana w taki sposób, że jednostki niestandardowe, takie jak właśnie utworzona, znajdują się na jej początku.

## <a name="sign-in-and-create-a-flow"></a>Logowanie i tworzenie przepływu
1. Otwórz [portal usługi Microsoft Flow](https://flow.microsoft.com).
2. Zmaksymalizuj okno przeglądarki, jeśli nie jest jeszcze zmaksymalizowane, a następnie kliknij lub naciśnij przycisk **Zaloguj** w pobliżu prawego górnego rogu.
   
    ![Przycisk Zaloguj dla usługi Microsoft Flow](./media/common-data-model-approve/signin-flow.png)
3. W prawym górnym menu wybierz środowisko, w którym utworzono bazę danych w witrynie powerapps.com.
   
    **Uwaga**: jeśli nie zostanie wybrane to samo środowisko, odpowiednia jednostka nie będzie widoczna.
4. W pobliżu lewego górnego rogu kliknij lub naciśnij przycisk **Moje przepływy**.
   
    ![Przycisk Moje przepływy](./media/common-data-model-approve/myflows-button.png)
5. W pobliżu prawego górnego rogu kliknij lub naciśnij przycisk **Utwórz nowy przepływ**.
   
    ![Przycisk Utwórz nowy przepływ](./media/common-data-model-approve/create-flow.png)

## <a name="start-when-a-file-is-added"></a>Uruchamianie po dodaniu pliku
1. W polu zawierającym wartość **Wyszukaj więcej wyzwalaczy** wpisz lub wklej ciąg **Dropbox**, a następnie kliknij lub naciśnij pozycję **Dropbox — po utworzeniu pliku**.
   
    ![Tworzenie wyzwalacza](./media/common-data-model-approve/create-trigger.png)
2. W obszarze **Folder** kliknij lub naciśnij ikonę folderu, a następnie przejdź do folderu, do którego pliki zostaną dodane.
   
    ![Wybieranie folderu](./media/common-data-model-approve/folder-icon.png)

## <a name="add-data-to-the-entity"></a>Dodawanie danych do jednostki
1. Kliknij lub naciśnij przycisk **Nowy krok**, a następnie kliknij lub naciśnij przycisk **Dodaj akcję**.
   
    ![Dodawanie akcji](./media/common-data-model-approve/add-action.png)
2. W polu zawierającym wartość **Wyszukaj więcej akcji** wpisz lub wklej ciąg **Common Data Service**, a następnie kliknij lub naciśnij pozycję **Common Data Service — Utwórz obiekt**.
   
    ![Tworzenie obiektu w usłudze Common Data Service](./media/common-data-model-approve/cdm-create-object.png)
3. W obszarze **Jednostka** wpisz lub wklej ciąg **Przegląd**, a następnie kliknij lub naciśnij pozycję **Przegląd plików Dropbox**.
   
    ![Wybieranie jednostki](./media/common-data-model-approve/choose-entity-flow.png)
4. W obszarze **Tytuł** kliknij lub naciśnij pole, a następnie kliknij lub naciśnij pozycję **Nazwa pliku** na liście tokenów parametrów, aby dodać token do pola.
   
    ![Dodawanie tokenu Nazwa pliku](./media/common-data-model-approve/add-filename-token.png)
5. W obszarze **Osoba zatwierdzająca** wpisz lub wklej adres e-mail osoby, która będzie przeglądała pliki.
   
    **Uwaga**: Aby ułatwić testowanie przepływu, podaj własny adres. Możesz go zmienić później, gdy przepływ będzie gotowy do rzeczywistego użycia.
   
    ![Dodawanie osoby zatwierdzającej](./media/common-data-model-approve/add-approver.png)
6. W obszarze **Stan** wpisz lub wklej ciąg **Oczekujące**.
   
    ![Dodawanie domyślnego stanu](./media/common-data-model-approve/add-default-status.png)
7. W obszarze **Identyfikator pliku** kliknij lub naciśnij pole, a następnie kliknij lub naciśnij pozycję **Identyfikator pliku** na liście tokenów parametrów, aby dodać token do pola.
   
    ![Dodawanie tokenu Identyfikator pliku](./media/common-data-model-approve/add-file-identifier.png)

## <a name="check-whether-the-file-has-been-reviewed"></a>Sprawdzanie, czy plik został przejrzany
1. W obszarze akcji **Utwórz obiekt** kliknij lub naciśnij przycisk **Nowy krok**, kliknij lub naciśnij pozycję **Więcej**, a następnie kliknij lub naciśnij polecenie **Dodaj akcję Wykonuj, dopóki**.
   
    ![Dodawanie akcji Wykonuj, dopóki](./media/common-data-model-approve/add-do-until.png)
2. W lewym górnym rogu akcji **Wykonuj, dopóki** kliknij lub naciśnij pole zawierające ciąg **Wybierz wartość**.
   
    ![Wybieranie wartości](./media/common-data-model-approve/choose-value.png)
   
    **Uwaga**: jeśli okno przeglądarki nie jest zmaksymalizowane, kliknij lub naciśnij górne pole, które zawiera ciąg **Wybierz wartość**.
3. W obszarze **Dane wyjściowe akcji Utwórz obiekt** kliknij lub naciśnij pozycję **Stan**, aby dodać token parametru do pola.
   
    ![Dodawanie tokenu Stan](./media/common-data-model-approve/add-status.png)
4. Otwórz listę w pobliżu środka akcji **Wykonuj, dopóki**, a następnie kliknij lub naciśnij pozycję **nie jest równe**.
   
    ![Określanie opcji „nie jest równe”](./media/common-data-model-approve/is-not-equal.png)
5. W prawym górnym rogu akcji **Wykonuj, dopóki** wpisz lub wklej wartość **Oczekujące** w polu zawierającym ciąg **Wybierz wartość**.
   
    ![Określanie stanu do obserwowania](./media/common-data-model-approve/do-until-not-pending.png)
   
    **Uwaga**: jeśli okno przeglądarki nie jest zmaksymalizowane, kliknij lub naciśnij dolne pole, które zawiera ciąg **Wybierz wartość**.
6. W pobliżu dolnej części akcji **Wykonuj, dopóki** kliknij lub naciśnij przycisk **Dodaj akcję**.
   
    ![Dodawanie akcji wewnątrz akcji Wykonuj, dopóki](./media/common-data-model-approve/add-action-in-dountil.png)
7. W polu zawierającym wartość **Wyszukaj więcej akcji** wpisz ciąg **Common**, a następnie kliknij lub naciśnij pozycję **Common Data Service — Pobierz obiekt**.
   
    ![Pobieranie obiektu](./media/common-data-model-approve/get-object.png)
8. W obszarze **Przestrzeń nazw** kliknij lub naciśnij bazę danych.
9. W obszarze **Jednostka** wpisz lub wklej ciąg **Przegląd**, a następnie kliknij lub naciśnij pozycję **Przegląd plików Dropbox**.
   
    ![Wybieranie jednostki](./media/common-data-model-approve/choose-entity-flow.png)
10. W obszarze **Identyfikator obiektu** kliknij lub naciśnij pole, a następnie kliknij lub naciśnij token parametru **Identyfikator pliku**, aby dodać go do pola.
    
     ![Dodawanie identyfikatora obiektu](./media/common-data-model-approve/add-object-id.png)

## <a name="check-whether-the-item-has-been-approved"></a>Sprawdzanie, czy element został zatwierdzony
1. W obszarze akcji **Wykonuj, dopóki** kliknij lub naciśnij przycisk **Nowy krok**, a następnie kliknij lub naciśnij pozycję **Dodaj warunek**.
   
    ![Dodawanie warunku](./media/common-data-model-approve/add-condition.png)
2. W lewym górnym rogu warunku kliknij lub naciśnij pole zawierające ciąg **Wybierz wartość**.
   
    ![Lewy górny róg warunku](./media/common-data-model-approve/condition-upper-left.png)
   
    **Uwaga**: jeśli okno przeglądarki nie jest zmaksymalizowane, kliknij lub naciśnij górne pole, które zawiera ciąg **Wybierz wartość**.
3. W obszarze **Dane wyjściowe akcji Pobierz obiekt** kliknij lub naciśnij token parametru **Stan**, aby dodać go do pola.
   
    ![Dodawanie stanu do warunku](./media/common-data-model-approve/add-status-to-condition.png)
4. W prawym górnym rogu warunku wpisz lub wklej wartość **Zatwierdzone** w polu zawierającym ciąg **Wybierz wartość**.
   
    ![Sprawdzanie, czy ustawiono stan Zatwierdzone](./media/common-data-model-approve/status-equals-approved.png)
   
    **Uwaga**: jeśli okno przeglądarki nie jest zmaksymalizowane, wpisz lub wklej wartość **Zatwierdzone** w dolnym polu, które zawiera ciąg **Wybierz wartość**.

## <a name="send-notification-mail"></a>Wysyłanie wiadomości e-mail z powiadomieniem
1. W obszarze **Jeśli tak, nic nie rób** kliknij lub naciśnij przycisk **Dodaj akcję**.
   
    ![Jeśli tak, dodaj akcję](./media/common-data-model-approve/if-yes-action.png)
2. W polu zawierającym wartość **Wyszukaj więcej akcji** wpisz lub wklej ciąg **wyślij wiadomość**, a następnie kliknij lub naciśnij pozycję **Office 365 Outlook — Wyślij wiadomość e-mail**.
   
    ![Jeśli tak, wyślij wiadomość e-mail](./media/common-data-model-approve/if-yes-send-mail.png)
3. W obszarze **Do** wpisz lub wklej adres osoby, która ma być powiadamiana o zaakceptowaniu elementu.
   
    **Uwaga**: Aby ułatwić testowanie przepływu, podaj własny adres. Możesz go zmienić, gdy przepływ będzie gotowy do rzeczywistego użycia.
   
    ![Adresat zatwierdzenia](./media/common-data-model-approve/approval-recipient.png)
4. W obszarze **Temat** kliknij lub naciśnij pole, a następnie kliknij lub naciśnij token parametru **Nazwa pliku**, aby dodać go do pola.
   
    ![Określanie nazwy pliku jako tematu wiadomości e-mail](./media/common-data-model-approve/subject-is-file-name.png)
5. W obszarze **Treść** wpisz lub wklej ciąg **Element został zatwierdzony.**
   
    ![Treść wiadomości e-mail dotyczącej zatwierdzenia](./media/common-data-model-approve/approval-body.png)
6. W obszarze **Jeśli nie, nic nie rób** powtórz kroki 1–5 tej procedury, ale podaj następującą treść wiadomości e-mail: **Element został odrzucony.**
   
    ![Treść wiadomości e-mail dotyczącej odrzucenia](./media/common-data-model-approve/rejection-body.png)

## <a name="delete-rejected-files"></a>Usuwanie odrzuconych plików
1. W polach wiadomości e-mail dotyczącej odrzucenia kliknij lub naciśnij pozycję **Dodaj akcję**.
   
    ![Dodawanie akcji Usuń](./media/common-data-model-approve/add-delete-action.png)
2. W polu zawierającym wartość **Wyszukaj więcej akcji** wpisz lub wklej ciąg **Dropbox**, a następnie kliknij lub naciśnij pozycję **Dropbox — Usuń plik**.
   
    ![Usuwanie pliku z usługi Dropbox](./media/common-data-model-approve/dropbox-delete-file.png)
3. W obszarze **Plik** kliknij lub naciśnij pole, a następnie kliknij lub naciśnij token parametru **Identyfikator pliku**, aby dodać go do pola.
   
    ![Identyfikowanie pliku do usunięcia](./media/common-data-model-approve/identify-file-delete.png)

## <a name="save-the-flow"></a>Zapisywanie przepływu
1. W górnej części ekranu wpisz lub wklej nazwę tworzonego przepływu, a następnie kliknij lub naciśnij przycisk **Utwórz przepływ**.
   
    ![Zapisywanie przepływu](./media/common-data-model-approve/save-flow.png)
2. Kliknij lub naciśnij pozycję **Zamknij**, a następnie kliknij lub naciśnij przycisk **Gotowe**.
3. W usłudze Dropbox dodaj co najmniej dwa pliki do określonego folderu: jeden w celu przetestowania zatwierdzenia i jeden w celu przetestowania odrzucenia.

## <a name="build-the-app"></a>Tworzenie aplikacji
1. Zaloguj się w witrynie [powerapps.com](https://web.powerapps.com), a następnie kliknij lub naciśnij przycisk **Nowa aplikacja** w pobliżu dolnej części lewego paska nawigacyjnego.
   
    ![Tworzenie aplikacji w przeglądarce](./media/common-data-model-approve/new-app-button.png)
2. W wyświetlonym oknie dialogowym kliknij lub naciśnij odpowiednią opcję, aby otworzyć program PowerApps Studio dla systemu Windows albo usługę PowerApps Studio dla sieci web.
3. Jeśli otworzysz program PowerApps Studio dla systemu Windows, kliknij lub naciśnij przycisk **Nowy** na lewym pasku nawigacyjnym.
4. W obszarze **Tworzenie aplikacji na podstawie danych** kliknij lub naciśnij pozycję **Układ telefonu** na kafelku **Common Data Service**.
   
    ![Tworzenie aplikacji](./media/common-data-model-approve/afd-cdm.png)
5. W polu **Wyszukaj** wpisz lub wklej ciąg **Przegląd**.
   
    ![Wyszukiwanie jednostki](./media/common-data-model-approve/search-entities.png)
6. W obszarze **Wybieranie jednostki** kliknij lub naciśnij pozycję **Przegląd plików Dropbox**.
   
    ![Wybieranie jednostki](./media/common-data-model-approve/choose-entity.png)
7. W pobliżu prawego dolnego rogu kliknij lub naciśnij przycisk **Połącz**.
   
    ![Przycisk Połącz](./media/common-data-model-approve/connect-button.png)
8. Jeśli pojawi się ekran powitalny przewodnika wprowadzającego, skorzystaj z niego, aby zapoznać się z usługą PowerApps (albo kliknij lub naciśnij przycisk **Pomiń**).
   
    ![Przewodnik wprowadzający](./media/common-data-model-approve/quick-tour.png)
   
    Z przewodnika możesz zawsze skorzystać później, klikając lub naciskając ikonę znaku zapytania w pobliżu lewego górnego rogu, a następnie klikając lub naciskając pozycję **Uruchom przewodnik wprowadzający**.
9. (opcjonalnie) W pobliżu dolnej części ekranu przeciągnij suwak, aby powiększyć i poprawić widoczność aplikacji.
   
    ![Kontrolka powiększenia](./media/common-data-model-approve/zoom-control.png)

## <a name="customize-the-app"></a>Dostosowywanie aplikacji
1. Na prawym pasku nawigacyjnym kliknij lub naciśnij układ zawierający nagłówek i opis.
   
    ![Przycisk Połącz](./media/common-data-model-approve/choose-layout.png)
2. Na ekranie **BrowseScreen** kliknij lub naciśnij pozycję znajdującą się tuż poniżej paska wyszukiwania, aby wybrać kontrolkę większego pola tekstowego.
   
    ![Wybieranie nagłówka](./media/common-data-model-approve/select-header.png)
3. W okienku po prawej stronie otwórz dolną listę, klikając lub naciskając jej strzałkę w dół.
   
    ![Otwieranie listy rozwijanej](./media/common-data-model-approve/open-dropdown.png)
4. Na dolnej liście kliknij lub naciśnij polecenie **Tytuł**, aby wyświetlić nazwy dodanych plików.
   
    ![Ustawianie danych nagłówka](./media/common-data-model-approve/set-heading.png)
5. W okienku po prawej stronie otwórz górną listę, a następnie kliknij lub naciśnij pozycję **Stan**, aby wyświetlić stan każdego pliku.
   
    ![Ustawianie danych treści](./media/common-data-model-approve/set-body.png)

## <a name="test-the-overall-solution"></a>Testowanie całego rozwiązania
1. W usłudze PowerApps włącz tryb podglądu, klikając lub naciskając przycisk odtwarzania w pobliżu lewego górnego rogu.
   
    ![Włączanie trybu podglądu](./media/common-data-model-approve/open-preview.png)
2. Dla pierwszego pliku na liście kliknij lub naciśnij strzałkę, aby wyświetlić szczegółowe informacje o tym pliku.
   
    ![Otwieranie ekranu Szczegóły](./media/common-data-model-approve/open-details.png)
3. W prawym górnym rogu kliknij lub naciśnij ikonę ołówka, aby zmienić szczegóły dotyczące pliku.
   
    ![Otwieranie ekranu Edycja](./media/common-data-model-approve/edit-record.png)
4. W polu **Stan** wpisz lub wklej ciąg **Zatwierdzone**.
   
    ![Zatwierdzanie pliku](./media/common-data-model-approve/change-status.png)
5. W prawym górnym rogu kliknij lub naciśnij ikonę znacznika wyboru, aby zapisać zmiany i powrócić do ekranu szczegółów.
   
    ![Zapisywanie zmian](./media/common-data-model-approve/save-record.png)
   
    W ciągu kilku minut otrzymasz wiadomość e-mail informującą o tym, że plik został zatwierdzony.
6. W prawym górnym rogu kliknij lub naciśnij przycisk Wstecz, aby powrócić do ekranu przeglądania.
   
    ![Powrót do ekranu przeglądania](./media/common-data-model-approve/back-arrow.png)
7. Dla drugiego pliku na liście kliknij lub naciśnij strzałkę, aby wyświetlić szczegółowe informacje o tym pliku.
   
    ![Otwieranie ekranu Szczegóły](./media/common-data-model-approve/open-details.png)
8. W prawym górnym rogu kliknij lub naciśnij ikonę ołówka, aby zmienić szczegóły dotyczące pliku.
   
    ![Otwieranie ekranu Edycja](./media/common-data-model-approve/edit-record.png)
9. W polu **Stan** wpisz lub wklej ciąg **Odrzucone** (albo jakikolwiek inny ciąg poza **Zatwierdzone**, w tym **Zatwiardzone** bądź **Zatwiierdzone**).
   
    ![Odrzucanie pliku](./media/common-data-model-approve/reject-file.png)
10. W prawym górnym rogu kliknij lub naciśnij ikonę znacznika wyboru, aby zapisać zmiany i powrócić do ekranu szczegółów.
    
     ![Zapisywanie zmian](./media/common-data-model-approve/save-record.png)
    
     W ciągu kilku minut otrzymasz wiadomość e-mail informującą o tym, że plik został odrzucony, a plik zostanie usunięty z usługi Dropbox.

