W poprzednim temacie pokazano, jak w prosty sposób publikować na kanale w usłudze Twitter przy użyciu listy programu SharePoint. W ramach tego tematu nauczysz się, jak tworzyć bardziej biznesowe scenariusze z użyciem zatwierdzeń. Dzięki temu każda osoba mająca dostęp do listy programu SharePoint może współtworzyć tweety, a zespół ds. mediów społecznościowych może te tweety zatwierdzać lub odrzucać. Zespół zachowuje kontrolę nad kontem i treścią, która trafia do klientów. 

## <a name="create-an-approval-request-flow"></a>Tworzenie przepływu żądania zatwierdzenia
1. Na stronie głównej usługi **Microsoft Flow** wybierz opcję **Zatwierdzenia**, wybierz pozycję **Utwórz przepływ zatwierdzenia**, a następnie przewiń w dół i wybierz szablon **Publikuj elementy listy w usłudze Twitter po zatwierdzeniu**. 
   
    ![Wybieranie szablonu](./media/learning-approval-center/create-approval.png)
2. Sprawdź poświadczenia konta dla pozycji **SharePoint**, **Zatwierdzenia** i **Twitter**, a następnie wybierz pozycję **Kontynuuj**. 
   
    ![Weryfikowanie poświadczeń](./media/learning-approval-center/verify-credentials.png)

Domyślnie ten szablon uruchamia proces zatwierdzania za każdym razem, gdy na określonej liście zostanie utworzony nowy element, a jeśli ten element zostanie zatwierdzony, publikuje tweet w usłudze Twitter. W ramach niniejszego tematu zmodyfikujesz ten proces, dodając kroki, które aktualizują listę programu SharePoint o odpowiedź na żądanie zatwierdzenia, wskazują, czy żądanie zostało zatwierdzone, i dodają ewentualne komentarze, które osoba zatwierdzająca mogła dodać do proponowanego tweetu. 

1. Dodaj dwie nowe kolumny do utworzonej wcześniej listy programu SharePoint **Tweety Contoso**:
   
   1. Wybierz znak plus „**+**” i wybierz pozycję **Tak/Nie**
   2. Wprowadź **Stan zatwierdzenia** i wybierz pozycję **Utwórz**
   3. Wybierz znak plus „**+**” i wybierz pozycję **Jeden wiersz tekstu**
   4. Wprowadź **Komentarze osoby zatwierdzającej** i wybierz pozycję **Zapisz**
      
      ![Dodawanie kolumn](./media/learning-approval-center/new-columns.png)
2. W usłudze **Microsoft Flow**, w akcji **Po utworzeniu nowego elementu** wprowadź następujące wartości:
   
   * **Adres witryny**: adres URL programu SharePoint Twojego zespołu
   * **Nazwa listy**: Tweety Contoso
     
     ![Witryna i lista](./media/learning-approval-center/site-address.png)
3. W akcji **Rozpocznij zatwierdzanie** wybierz pozycję **Edytuj**, aby wyświetlić wszystkie pola. 
   
    ![Edytowanie pól](./media/learning-approval-center/edit-all-fields.png)
4. W pozycji **Tytuł** wprowadź wartość **Nowy tweet dla** i wybierz pozycję **Tytuł** z listy zawartości dynamicznej. 
   
    ![Tytuł](./media/learning-approval-center/tweet-title.png)
5. W pozycji **Przypisano do** wprowadź i wybierz swoje imię i nazwisko lub nazwę użytkownika testowego. 
   
    ![Przypisano do](./media/learning-approval-center/tweet-assigned-to.png)
6. W sekcji **Szczegóły** usuń elementy domyślne i dodaj pozycje **Treść tweetu**, **Data tweetu** i **Utworzony przez Nazwa wyświetlana** z listy zawartości dynamicznej, łącząc je słowami **dnia** i **autor:**. 
   
    ![Szczegóły](./media/learning-approval-center/tweet-details.png)
7. W pozycji **Link do elementu** skopiuj i wklej adres URL listy programu SharePoint, a w pozycji **Opis linku do elementu** wprowadź wartość **Lista tweetów Contoso**. 
   
    ![Link do elementu](./media/learning-approval-center/tweet-item-link.png)
8. W akcji **Warunek** najedź kursorem na pole **JEŚLI TAK**, wybierz znak plus „**+**” i wybierz pozycję **Dodaj akcję**. 
   
    ![Dodawanie akcji](./media/learning-approval-center/add-an-action.png)
9. Wyszukaj ciąg **aktualizuj element**, wybierz łącznik **SharePoint**, a następnie wybierz akcję **SharePoint — Aktualizuj element**.
   
    ![Aktualizacja elementu programu SharePoint](./media/learning-approval-center/update-item.png)
10. W polach **Adres witryny** i **Nazwa listy** ponownie wprowadź adres URL swojej witryny i listę **Tweety Contoso**, a w polu **Identyfikator** wprowadź **Identyfikator** z listy zawartości dynamicznej. 
    
     ![Witryna, lista i identyfikator](./media/learning-approval-center/address-list-id.png)
11. Wybierz pole **Tytuł** i na liście zawartości dynamicznej wyszukaj pozycję **Tytuł**. Dodaj element **Tytuł** z akcji **Po utworzeniu nowego elementu**. 
    
     ![Nowy tytuł](./media/learning-approval-center/add-title.png)
12. Wybierz parametr **Stan zatwierdzenia** i ustaw wartość **Tak**, a następnie wybierz pozycję **Komentarze osoby zatwierdzającej** i ustaw wartość **Komentarze** z listy zawartości dynamicznej. 
    
     ![Stan i komentarze](./media/learning-approval-center/approver-status.png)
13. W pobliżu dolnej części pola **JEŚLI NIE, NIC NIE RÓB** wybierz pozycję **Dodaj akcję**.
    
     ![Dodawanie braku akcji](./media/learning-approval-center/add-a-no-action.png)
14. Używając tych samych kroków, jak w przypadku konfiguracji **JEŚLI TAK**, utwórz akcję **SharePoint — Aktualizuj element** i skonfiguruj pola z użyciem tych samych wartości, z wyjątkiem ustawienia wartości **Nie** dla parametru **Stan zatwierdzenia**. 
    
     ![Stan = nie](./media/learning-approval-center/status-no.png)
15. Wybierz akcję **Wyślij tweet**, wybierz pozycję **Edytuj** i ustaw parametr **Tekst tweetu** na **Treść tweetu** z listy zawartości dynamicznej.  W górnej części strony wybierz pozycję **Utwórz przepływ**, aby zapisać swoją pracę. 
    
     ![Wysyłanie i zapisywanie](./media/learning-approval-center/post-tweet.png)

To tylko jeden ze sposobów, w jaki usługa Microsoft Flow może zwiększyć produktywność Twojego zespołu. Twój zespół może współtworzyć pomysły, ważne wiadomości lub wskazówki dotyczące produktów, a Ty nadal zachowasz kontrolę nad treścią tweetów, które czytają klienci.

W ramach następnego tematu pokażemy, co się dzieję, gdy osoba zatwierdzająca otrzymuje nowe żądanie dotyczące proponowanego tweetu. 

