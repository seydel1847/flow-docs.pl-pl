W ramach tego tematu dowiesz się, jak **utworzyć przepływ przycisku** dla firmy Contoso Flooring Company. 

Przepływów przycisków można używać do **wysyłania wiadomości e-mail** do zespołu i **powiadamiania o zadaniach** do wykonania. **Własność** przepływów **może zostać przypisana do jednego** pracownika lub **współdzielona przez wielu** członków zespołu.  

1. Przejdź najpierw do [witryny internetowej usługi Microsoft Flow](https://ms.flow.microsoft.com) i zaloguj się.
2. Po zalogowaniu wybierz pozycję **Moje przepływy**, a następnie pozycję **Utwórz z pustego**.
   
    ![Tworzenie z pustego](./media/learning-create-button-flow/2-create-from-blank.png)
   
    W pierwszej kolejności potrzebny jest wyzwalacz. Przepływ przycisku dobrze sprawdza się w tej roli. 
3. Jeśli go nie ma go na liście, wybierz pozycję **Przeszukaj setki łączników i wyzwalaczy** w dolnej części strony, wprowadź tekst **przycisk** a zostanie on wyświetlony. 
4. Wybierz pozycję **Przycisk przepływu dla urządzeń przenośnych**.
   
    ![Wyszukiwanie przycisku](./media/learning-create-button-flow/3-button-flow.png) 
5. Wybierz **Przycisk przepływu dla urządzeń przenośnych — wyzwól przepływ ręcznie**.
   
    ![Wybór ręcznego wyzwalacza](./media/learning-create-button-flow/4-press-it.png)
6. Na ekranie wejściowym wybierz pozycję **Dodaj tekst wejściowy**,
   
    ![Dodawanie danych wejściowych](./media/learning-create-button-flow/5-add-input.png)
7. Wprowadź tekst **Contoso Flooring** w pierwszym polu tekstowym i **Wiadomość e-mail o dostawie do magazynu** w drugim polu tekstowym.
   
    ![Dodawanie danych wejściowych](./media/learning-create-button-flow/6-text-for-flow.png)
8. Wybierz pozycję **Nowy krok**. 
   
    ![Tekst wejściowy](./media/learning-create-button-flow/7-input-description.png)
9. Wybierz pozycję **Dodaj akcję**. 
   
    ![Dodawanie akcji](./media/learning-create-button-flow/8-add-an-action.png)
10. Wybierz łącznik **Office 365 Outlook**. Jeśli nie jest widoczny, wyszukaj tekst **outlook**.
    
     ![Wyszukiwanie usługi outlook](./media/learning-create-button-flow/9-search-outlook.png)
11. Wybierz pozycję **Office 365 Outlook — Wyślij wiadomość e-mail**.
    
     ![Wysyłanie wiadomości e-mail](./media/learning-create-button-flow/10-send-email.png)
    
     Po naciśnięciu przycisku do całego zespołu magazynu firmy Contoso, niezależnie od tego, gdzie się znajdują, jest wysyłana wiadomość e-mail z informacją o dostawie.
12. Rozwiń pola i dostosuj wiadomości e-mail zgodnie z wymaganiami firmy Contoso Flooring.
    
    1. W polu **Do** wprowadź prawidłowy adres e-mail dla Twojej organizacji.
    2. W polu **Temat** wprowadź tekst **Dostawa dotarła**. 
    3. Zwróć uwagę na wyświetlone po prawej stronie okno **zawartości dynamicznej**. Aby w wierszu tematu wyświetlić dokładną datę i godzinę naciśnięcia przycisku, wybierz pozycje **Data** i **Sygnatura czasowa**. 
       
        ![Data i godzina w wiadomości e-mail](./media/learning-create-button-flow/11-email-date-time.png)
13. Teraz wprowadź prostą **Treść** wiadomości e-mail w stylu: **Zespół magazynu proszony o podejście do stanowiska rozładunkowego w związku z dotarciem dzisiejszej dostawy**.
14. Wybierz pozycję **Utwórz przepływ**, aby zapisać przepływ.
    
     ![Tworzenie przepływu](./media/learning-create-button-flow/12-create-flow.png)

## <a name="create-a-team-flow"></a>Tworzenie przepływu zespołu
Ten przepływ przycisku może stanowić przykład sposobu tworzenia przepływu zespołu. Co zrobić, jeśli osoba, która utworzyła ten przepływ, jest na zwolnieniu? Co zrobić, jeśli odejdzie z firmy? Warto upewnić się, że przepływ nadal będzie działać. Aby to zrobić, dodaj współwłaścicieli.

1. Wybierz **ikonę zespołu** na przepływie, aby dodać współwłaściciela.
   
    ![Tworzenie przepływu zespołu](./media/learning-create-button-flow/13-create-team-flow.png) 
2. Wprowadź nazwy, adresy e-mail lub grupy użytkowników, aby dodać współwłaścicieli.
   
    ![Dodawanie współwłaścicieli](./media/learning-create-button-flow/14-add-co-owners.png)
3. Aby usunąć współwłaściciela, wybierz kosz z prawej strony jego nazwy.
   
    ![Usuwanie współwłaścicieli](./media/learning-create-button-flow/15-remove-co-owners.png)
4. Wybierz pozycję **Usuń tego właściciela**, aby zakończyć usuwanie.
   
    ![Usuwanie współwłaścicieli](./media/learning-create-button-flow/16-agree-to-remove.png)

## <a name="summary"></a>Podsumowanie
W ramach tej lekcji przedstawiono, jak **utworzyć przepływ przycisku**. 

W ciągu kilku minut przepływ umożliwił pracownikowi magazynu **zaalarmowanie zespołu** o fakcie **przybycia dostawy**, dzięki czemu zespół nie musiał bezczynnie czekać w pobliżu, marnując cenny czas, który mógł poświęcić na realizację innych zadań. 

Następnie pracownik udostępnił ten przycisk swojemu zespołowi, aby inni mogli także wyzwolić ten przepływ w razie jego nieobecności.

## <a name="next-lesson"></a>Następna lekcja
Sprawdź następną lekcję, aby zobaczyć, jak utworzyć przepływ wykorzystujący **powiadomienia wypychane**.

