---
title: Informacje o wersji | Microsoft Docs
description: "Typowe problemy i nowości w wydaniach usługi Microsoft Flow"
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
ms.date: 02/12/2018
ms.author: stepsic
ms.openlocfilehash: 3687266e84c06c37ac6ae0ee3d89aae0814158f3
ms.sourcegitcommit: 28b6b09c9f3dd98a64492668d9a3b8c7bfbd6ce3
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2018
---
# <a name="release-notes"></a>Informacje o wersji
## <a name="top-questions"></a>Najczęściej zadawane pytania
1. Mój przepływ zakończył się niepowodzeniem. Jak go naprawić?
   
   1. Zidentyfikuj problem. Zacznij od wybrania ikony powiadomień u góry portalu sieci Web lub karty **Działanie** w aplikacji mobilnej. Twój przepływ powinien być tam widoczny i można będzie go wybrać.
   2. Zostaną wyświetlone szczegóły przepływu. Znajdź krok z ikoną czerwonego wykrzyknika. Powinien tam być wyświetlany komunikat o błędzie dotyczący przepływu.
   3. W zależności od komunikatu o błędzie powinno być możliwe zmodyfikowanie przepływu za pomocą opcji **Edytuj** i usunięcie problemu. [Przeczytaj więcej na temat naprawiania typowych błędów przepływów](fix-flow-failures.md).
2. Jak mogę użyć zaawansowanego warunku lub wyrażenia?
   
   * Przeczytaj o [dodawaniu warunków](add-condition.md).
   * Jeśli w przepływach chcesz mieć wiele przypadków, kliknij lub naciśnij pozycję **Dodaj warunek** wewnątrz istniejącego warunku.
   * Zaawansowane wyrażenie możesz utworzyć przez odwołanie się do [funkcji usługi Logic Apps](https://docs.microsoft.com/rest/api/logic/definition-language).
3. Jak działa licencjonowanie w usłudze Office 365?
   
   * Jeśli jesteś użytkownikiem usługi Office 365, uzyskujesz pełen dostęp za pośrednictwem planu usługi Microsoft Flow dla usługi Office 365. Aby uzyskać więcej informacji, zobacz [plany cenowe usługi Microsoft Flow](https://flow.microsoft.com/pricing/) .
   * Jeśli jesteś administratorem, zapoznaj się z informacjami na temat [licencjonowania usługi Microsoft Flow](organization-q-and-a.md), również w ramach usługi Office 365.

## <a name="known-issues-and-resolutions"></a>Znane problemy i rozwiązania
1. Listy programu SharePoint w obszarze Moje witryny i te, które nie są typu *Lista niestandardowa*, nie są obsługiwane. Aby obejść ten problem, utwórz listę niestandardową w standardowej witrynie programu SharePoint.
2. Przepływy nie mogą zapisywać informacji w polach Taksonomia na listach programu SharePoint. Do czasu rozwiązania tego problemu zalecamy używanie prostego pola ciągu.
3. Wyzwalacze plików nie będą uruchamiane w przypadku plików dodawanych wewnątrz folderów zagnieżdżonych w wybranym folderze.

## <a name="whats-new"></a>Co nowego

### <a name="release-2018-02-09"></a>Wersja 2018-02-09

- **Wysoka dostępność bramy** — tworzenie klastrów o wysokiej dostępności obejmujących lokalne bramy danych, aby utrzymać połączenia w przypadku awarii pojedynczych maszyn.
- **Ulepszona funkcja Zastosuj do każdego** — proces planu przepływu 1 lub planu przepływu 2 obejmuje maksymalnie 100 000 elementów w jednym przebiegu i 50 akcji wykonywanych równolegle w pętli Zastosuj do każdego. 

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/gateway-ha-increased-apply-to-each/) na temat tej wersji.

### <a name="release-2018-01-29"></a>Wersja 2018-01-29

- **Przepływ wewnątrz obszaru Microsoft Teams** — w obszarze Teams można tworzyć przepływy i zarządzać nimi, przeglądać otrzymane i wysłane zatwierdzenia oraz uruchamiać przepływy bezpośrednio w aplikacji klasycznej Teams lub w witrynie teams.microsoft.com — [więcej informacji tutaj](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/).
- **Udostępnione powiadomienia o edycji** — za każdym razem, gdy przepływ należący do użytkownika zostanie zmieniony przez współpracownika, otrzymasz wiadomość e-mail z powiadomieniem o autorze zmiany.
- **Nowe wyrażenia** — dodano dwa nowe zestawy wyrażeń: jeden służący do analizowania adresów URL i drugi do współpracy z obiektami JSON.
- **Trzy nowe łączniki** — w tym tygodniu wprowadzono dwa nowe łączniki Plumsail: Plumsail SP oraz Plumsail Forms, a także nowy łącznik do platformy kintone.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/shared-notifications-and-expressions/) na temat tej wersji.

### <a name="release-2018-01-17"></a>Wersja 2018-01-17

- **Informacje o profilu usługi Office 365** — dodano nowe akcje do łącznika użytkowników usługi Office 365, które obsługują profile i zdjęcia użytkowników.
- **Dołączanie do zmiennych ciągu** — można dodawać elementy do ciągów wewnątrz pętli, aby tworzyć tabele lub inne listy.
- **Łącznik Infobip** — Infobip to usługa, która umożliwia komunikację na poziomie przedsiębiorstwa, m.in. połączenia głosowe i wyzwalanie akcji za pomocą przychodzących wiadomości SMS.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/o365-profile-infobip/) na temat tej wersji.

### <a name="release-2017-12-20"></a>Wersja 2017-12-20

Usługa Microsoft Flow Analytics jest teraz dostępna we wszystkich regionach usługi Microsoft Flow, co oznacza, że możesz uzyskać lepszy wgląd w kondycję przepływów uruchomionych w środowisku.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/announcing-microsoft-flow-analytics/) na temat tej wersji.


### <a name="release-2017-12-14"></a>Wersja 2017-12-14

- **Ulepszenia łącznika programu Outlook** — możesz zapisywać wiadomości e-mail jako pliki „eml”, automatycznie odpowiadać na zaproszenia kalendarza i wyzwalać przepływy, gdy wzmiankowano o Tobie w wątku wiadomości e-mail.
- **Ulepszenia połączeń** — usługa Microsoft Flow pamięta ostatnio używane połączenia i pokazuje wszystkie nowo dodane łączniki.
- **Pięć nowych łączników** — dodano łączniki usług Azure Container Instances, Azure Kusto, Metatask, Microsoft To-Do i Plumsail Documents.
- **Ulepszenia HTTP** — teraz akcja HTTP obsługuje kodowanie fragmentaryczne.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/outlook-connector-more/) na temat tej wersji.

### <a name="release-2017-12-05"></a>Wersja 2017-12-05

Panel uruchamiania usługi Microsoft Flow jest teraz dostępny we wszystkich regionach. Ten panel umożliwia dodawanie wartości do przepływu uruchamianego wewnątrz biblioteki dokumentów lub listy programu SharePoint.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/introducing-flow-launch-panel-in-sharepoint-lists-and-libraries/) na temat tej wersji.


### <a name="release-2017-11-28"></a>Wersja 2017-11-28

- **Zarządzane metadane** — odczytywanie i zapisywanie danych w kolumnach w programie SharePoint, które obsługują typ (taksonomię) Zarządzane metadane.
- **Dołączanie do tablic** — dodawaj elementy na końcu tablic przy użyciu nowej akcji Dołącz do zmiennej tablicowej.
- **Tago** — nowy łącznik do usługi Tago, który zapewnia łatwe łączenie urządzeń elektronicznych z danymi zewnętrznymi w celu podejmowania lepszych decyzji na podstawie analizy kontekstowej.
- **iPhone X** — nowa wersja aplikacji Microsoft Flow używa pełnego ekranu na telefonie iPhone X i poprawiono w niej szybkość przekazywania obrazów.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/managed-metadata-tago/) na temat tej wersji.

### <a name="release-2017-11-09"></a>Wersja 2017-11-09

- **Integracja z usługą OneDrive dla Firm** — [teraz w usłudze OneDrive dla Firm jest przycisk przepływu](https://flow.microsoft.com/blog/microsoft-flow-integration-in-one-drive-for-business-and-new-connector-actions/), który umożliwia tworzenie lub wyzwalanie przepływów dla wybranych plików lub folderów.
- **Wyzwalacze aplikacji Planner** — uruchamiaj przepływy, gdy zostanie utworzone nowe zadanie, gdy zadanie zostanie przypisane do Ciebie lub gdy zostanie ukończone.
- **Załączniki programu SharePoint** — pracuj z załącznikami w elementach listy programu SharePoint: wymieniaj je na liście, pobieraj, dodawaj lub usuwaj załączniki.
- **Łącznik zarządzania przepływem** — twórz przepływy, które automatyzują zarządzanie innymi przepływami w danym środowisku (na przykład automatycznie dodawaj uprawnienia do przepływów).
- **Cztery nowe łączniki** — dodano łączniki usług Azure Custom Vision Service, D&B Optimizer, Enadoc i Derdak SIGNL4. 
- **Więcej akcji łącznika** — uruchamiaj zapytania SQL, uzyskuj szybsze wyzwalacze poczty e-mail, używaj dowolnej metody z protokołem HTTP w usłudze Azure AD i nie tylko.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/planner-triggers-connector-improvements/) na temat tej wersji.

### <a name="release-2017-11-02"></a>Wersja 2017-11-02

- **Rejestrowanie inspekcji** — zdarzenia inspekcji usługi Microsoft Flow są teraz dostępne w Centrum zabezpieczeń i zgodności usługi Office 365 dla wszystkich dzierżaw.
- **Poprawki widżetu usługi Flow** — rozwiązano problem w aplikacji mobilnej Flow, który powodował, że przyciski nie były ładowane w widżecie.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/security-and-compliance-center/) na temat tej wersji.

### <a name="release-2017-10-19"></a>Wersja 2017-10-19

- **Zagnieżdżona akcja Zastosuj do każdego** — możesz dodawać akcje Zastosuj do każdego, filtrować i wybierać w innych kontenerach akcji Zastosuj do każdego.
- **Akcje data/godzina** — nowe akcje do pobierania czasu lokalnego, dodawania, odejmowania lub formatowania godzin.
- **Cztery nowe łączniki** — dodano łączniki usług Content Moderator, Docparser, Microsoft Kaizala i Pitney Bowes Data Validation.
- **Ulepszone środowisko połączenia** — powiadomienia w portalu Flow, gdy połączenie jest przerwane, oraz dokładniejsze szczegóły połączenia.
- **Kolekcja W drodze** — nowa kolekcja szablonów dla [pracowników w drodze](https://flow.microsoft.com/collections/onthego/).
- **Dane wejściowe przycisku adresu e-mail** — zbieraj adresy e-mail od użytkowników, gdy uruchamiają oni przyciski.
- **Dane wejściowe przycisku pliku** — pobieraj przekazane pliki, takie jak zdjęcia, od użytkowników, gdy uruchamiają oni przyciski.
- **Pierwsze uruchomienie i automatyczne logowanie się** — ulepszone pierwsze uruchomienie w aplikacji mobilnej wraz z automatycznym logowaniem się.
- **Szybsze wyzwalacze programu Microsoft Forms** — program Forms będzie wyzwalał przepływy znacznie szybciej niż dotąd (przedtem raz na godzinę).
- **Dane wejściowe przycisku między sesjami** — przyciski wyzwalane na telefonie komórkowym będą zapamiętywać poprzednie dane wejściowe.
- **Mobilny kanał aktywności** — ulepszony kanał aktywności zawierający bardziej szczegółowe podsumowania przebiegu i szczegóły dotyczące rozwiązywania problemów.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/nested-apply-to-each/) na temat tej wersji.

### <a name="release-2017-10-03"></a>Wersja 2017-10-03

- **Wszyscy muszą zatwierdzić** — wymagaj wysyłania żądania zatwierdzenia do więcej niż jednej osoby, aby każdy, kto odebrał żądanie, zatwierdził je.
- **Nowe akcje usługi OneDrive dla Firm** — generowanie dokumentów PDF dla plików przechowywanych w usłudze OneDrive dla Firm i cztery inne nowe akcje.
- **Łącznik Apache Impala** — Apache Impala (wersja inkubacyjna) to natywna analityczna baza danych typu open source dla platformy Apache Hadoop.
- **Dodawanie opisów przepływów** — nadaj przepływom opisy, aby po ich udostępnieniu współpracownicy mogli zobaczyć podsumowanie działania przepływu.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/all-must-approve-and-onedrive/) na temat tej wersji.

### <a name="release-2017-09-25---q3-update-for-microsoft-flow"></a>Wersja 2017-09-25 — aktualizacja z 3. kwartału dla usługi Microsoft Flow

- **Głębsza integracja z programem SharePoint w ramach udostępniania natychmiastowego** — udostępniono nowe „wbudowane” przepływy wysyłania do przeglądu oraz panel Przepływ do zbierania danych wejściowych po uruchomieniu przepływu dla dzierżaw w ramach udostępniania natychmiastowego.
- **Dynamics 365 for Customer Engagement** — usługa Flow jest teraz zintegrowana z interfejsem użytkownika usługi Dynamics 365 for Customer Engagement.
- **Centrum zaufania firmy Microsoft** — usługa Flow jest wymieniona w Centrum zaufania firmy Microsoft z certyfikatami, takimi jak HIPAA, ISO i SOC.
- **Analiza użycia** — każdy przepływ ma osadzony pulpit nawigacyjny usługi Power BI z podstawową analizą użycia.
- **Rejestrowanie inspekcji w ramach udostępniania natychmiastowego** — wszystkie zdarzenia zarządzania przepływem są rejestrowane w Centrum zabezpieczeń i zgodności usługi Office 365 dla dzierżaw w ramach udostępniania natychmiastowego.
- **Sześć nowych łączników** — dodano łączniki usług LinkedIn, Grupy usługi Office 365, Skype dla firm, Adobe Sign, Bizzy i Azure Log Analytics Data Collection.
- **Wyzwalacze SQL** — uruchamiaj przepływy po dodaniu nowego wiersza lub zaktualizowaniu wiersza w tabeli SQL.
- **Lokalne łączniki niestandardowe** — łączniki niestandardowe mogą teraz używać lokalnej bramy danych do nawiązywania połączenia z wewnętrznymi punktami końcowymi w Twojej sieci.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/q3-2017-update/) na temat tej wersji.

### <a name="release-2017-09-21"></a>Wersja 2017-09-21

- **Pobieranie historii usługi Flow** — pobierz historię uruchamiania usługi Flow w postaci pliku CSV do otwierania w programie Excel.
- **Zaawansowany cykl** — twórz cykliczne harmonogramy, aby wyzwalać przepływy, na przykład tylko w dni robocze.
- **Funkcja IntelliSense** — gdy wpiszesz wyrażenia, funkcja IntelliSense wyświetli sugestie dotyczące parametrów.
- **Cztery nowe łączniki** — dodano łączniki usług HTTP usługi Azure AD, Amazon Redshift, Azure Event Grid Publish i FlowForma.
- **Linki do udostępniania** — nowa akcja do generowania linków, które można udostępnić, dla plików usługi OneDrive lub obiektów blob usługi Azure Storage.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/download-history-recurrence/) na temat tej wersji.


### <a name="release-2017-08-25"></a>Wersja 2017-08-25
* **Właściwości dokumentów i nie tylko dla programu SharePoint** - [Odczytuj i ustawiaj właściwości biblioteki dokumentów programu SharePoint](https://flow.microsoft.com/blog/support-for-sharepoint-document-library-properties/), a także korzystaj z pól dodatkowych, takich jak linki do elementów programu SharePoint.
* **Kolekcje przepływów** — kolekcje przepływów to zestaw kolekcji szablonów uporządkowanych według roli lub specjalizacji.
* **Udostępnianie przycisków dalej** — gdy udostępnisz przyciski współpracownikom, mogą oni udostępnić je dalej innym osobom.
* **Listy do zbierania danych z przycisków** — zdefiniuj listy rozwijane z opcjami, które użytkownicy mogą wybierać po naciśnięciu przycisku.
* **Siedem nowych łączników** — AWeber, Azure Log Analytics, Azure Tables, DocFusion365, Azure Event Grid, Azure Event Hubs i StaffHub. 
* **Ulepszenia dotyczące programów Slack i MySQL** — możesz tworzyć kanały w programie Slack i dołączać do takich kanałów oraz zapisywać informacje w bazach danych MySQL.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/button-updates-seven-connectors/) na temat tej wersji.

### <a name="release-2017-08-02"></a>Wersja 2017-08-02
* **Zapisywanie w polach Osoba, Wybór i Wyszukaj** — funkcje programu SharePoint Utwórz element i Zaktualizuj element [obsługują teraz możliwość](https://flow.microsoft.com/blog/setting-sharepoint-s-person-choice-and-lookup-fields/) ustawienia pól Osoba, Wybór i Wyszukaj.
* **Więcej ustawień akcji** — masz teraz większą kontrolę nad uruchamianiem wyzwalaczy i akcji oraz konfigurowaniem zasad ponawiania i dzielenia na strony.
* **Cztery nowe łączniki** — możesz teraz używać usług Azure File Storage, Elastic Forms, Plivo i Video Indexer.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/four-connector-action-settings/) na temat tej wersji.

### <a name="release-2017-07-27---q2-update-for-microsoft-flow"></a>Wersja 2017-07-27 — aktualizacja z 2. kwartału dla usługi Microsoft Flow
* **Importowanie i eksportowanie** — eksportuj i importuj rozwiązania dotyczące przepływów pomiędzy środowiskami lub między środowiskiem testowym i produkcyjnym. 
* **Używanie wyrażeń w akcjach** — wprowadzaj wyrażenia w dowolnej akcji i korzystaj z wbudowanej pomocy dotyczącej korzystania z nich.
* **Rozwój do usługi Azure Logic Apps** — zapisuj przepływy jako zasób usługi Azure Logic Apps, który można wdrożyć za pośrednictwem programu Visual Studio lub witryny Azure Portal.
* **Widoczność administratora** — pobierz dane dotyczące użycia usługi Microsoft Flow w dzierżawie, aby dowiedzieć się, gdzie i w jaki sposób są wykorzystywane przepływy.
* **Przepływy w usłudze Dynamics 365** — używaj przepływów w usłudze Dynamics 365 w wersjach Operations & Financials oraz Business Edition.
* **Łatwiejsze wyszukiwanie scenariuszy** — przejrzyj wszystkie możliwości łącznika, a następnie użyj dowolnego wyzwalacza jako punktu wyjścia do tworzenia przepływów.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/q2-2017-update/) na temat tej wersji.

### <a name="release-2017-07-13"></a>Wersja 2017-07-13
* **Ulepszone publikowanie szablonów** — opublikuj dowolny utworzony przez siebie przepływ, wraz z jego kategoriami, w publicznej galerii.
* **Pobieranie zdarzeń w kalendarzu programu Outlook** — nowa akcja zwracająca wszystkie zdarzenia pomiędzy dwoma terminami w kalendarzu.
* **Nowe funkcje mobilne** — uruchamiaj w aplikacji mobilnej przepływy na żądanie i przesyłaj ponownie przebiegi zakończone niepowodzeniem.
* **Dynamiczne listy rozwijane w łącznikach niestandardowych** — twórz dynamiczne listy rozwijane i wyzwalacze sondowania oraz testuj łączniki niestandardowe.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/publishing-and-custom-connectors/) na temat tej wersji.

### <a name="release-2017-06-28"></a>Wersja 2017-06-28
* **Aktualizacja ustawień języka** — w menu Ustawienia możesz dostosowywać język i region, z których korzysta usługa Microsoft Flow.
* **Pięć nowych łączników** — dodano obsługę usług Adobe Creative Cloud, Mapy Bing, Wyszukiwarka Bing, JotForm i Freshservice.
* **Konfigurowanie limitów czasu** — zmień czas, przez jaki długo trwające akcje, takie jak zatwierdzenia, mogą działać, zanim przekroczą limit czasu i przepływ będzie kontynuowany.
* **Dodawanie komentarzy do żądań zatwierdzenia w programie Outlook** — gdy otrzymasz żądanie zatwierdzenia, możesz napisać komentarze bez wychodzenia z programu Outlook.
* **Kolory firmowe łączników niestandardowych** — możesz teraz wprowadzić kolor dla łączników niestandardowych, który będzie używany w tle.
* **Funkcja Zapisz jako dla przepływów zespołów** — twórz kopie dowolnych przepływów, w tym przepływów zespołów
* **Usuwanie informacji o przepływie** — po usunięciu przepływu będzie wyświetlana lista wszystkich oczekujących uruchomień dla tego przepływu.
* **Filtrowanie na stronie Łączniki** —żądane łączniki można wyszukiwać na stronie Łączniki i filtrować według typu łącznika.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/language-settings-3-connectors/) na temat tej wersji.

### <a name="release-2017-06-19"></a>Wersja 2017-06-19
Można teraz wyświetlać stan wszystkich wysłanych przez siebie oczekujących żądań zatwierdzenia. Dodatkowo możesz przeglądać oczekujące zatwierdzenia i podejmować względem nich akcje bezpośrednio z urządzenia przenośnego.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/sent-requests-flow-mobile/) na temat tej wersji.

### <a name="release-2017-06-15"></a>Wersja 2017-06-15
* **Konwersja zawartości** — nowy łącznik mogący konwertować zawartość HTML na zwykły tekst, przydatny do obsługi wiadomości e-mail w formacie HTML.
* **Trzy nowe łączniki bazy danych** — dodano obsługę tylko do odczytu baz danych MySQL, PostgreSQL i Teradata. Te łączniki nawiązują połączenie za pośrednictwem lokalnej bramy danych.
* **Trzy inne łączniki** — umożliwiają nawiązywanie połączenia z usługami Azure Application Insights, Calendly i Teamwork Projects.
* **Lepsze wizualizacje na potrzeby obsługi błędów** — kroki uruchamiane po wystąpieniu błędów są teraz pokazywane za pomocą czerwonych kropkowanych strzałek, dzięki czemu można je łatwo zidentyfikować.
* **Okienko szczegółów uruchomienia** — gdy przepływ nie powiedzie się, nowe okienko po prawej stronie zawiera kroki pomocne w jego naprawianiu.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/seven-connectors-and-html/) na temat tej wersji.

### <a name="release-2017-06-04"></a>Wersja 2017-06-04
* **Ogólna dostępność dla systemu Windows Phone** - [Aplikacja mobilna usługi Microsoft Flow została wydana w wersji ogólnie dostępnej dla systemu Windows Phone](https://flow.microsoft.com/blog/announcing-flow-windows-phone-app/).
* **Wiadomości e-mail o niepowodzeniach przepływów** — uzyskiwanie powiadomień e-mail o przepływach, które nie powiodły się. Te wiadomości e-mail z informacjami o niepowodzeniu będą wysyłane jedynie raz w tygodniu i mogą być włączane oraz wyłączane przez użytkownika.
* **Akcja wybierania dla tabel** — nowa akcja wybierania pozwala zmienić zestaw kolumn, które zostaną uwzględnione w tabelach.
* **Łącznik programu Microsoft Forms** — Microsoft Forms to nowa część usługi Office 365 Education, która umożliwia nauczycielom i uczniom szybkie tworzenie niestandardowych testów, ankiet, kwestionariuszy, rejestracji i nie tylko.
* **Plan K1 usługi Office 365 Enterprise** — usługi PowerApps i Microsoft Flow są teraz częścią planu K1 usługi Office 365 Enterprise z określonymi limitami przydziału.
* **Łatwiejsza obsługa nagłówków HTTP** — podobnie jak w przypadku akcji wybierania, można podać nazwę i wartość nagłówka przez proste wypełnienie pól tekstowych akcji.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/microsoft-forms-tables-flow-failures/) na temat tej wersji.

### <a name="release-2017-05-23"></a>Wersja 2017-05-23
* **Łącznik aplikacji Microsoft Teams** - [Microsoft Teams](https://flow.microsoft.com/blog/introducing-the-microsoft-teams-connector-for-flow/) to bazujący na czacie obszar roboczy w usłudze Office 365, który łączy ludzi, rozmowy i zawartość oraz udostępnia narzędzia potrzebne zespołom do łatwej współpracy i osiągania lepszych efektów.
* **Elementy widget w systemach iOS i Android** — elementy widget aplikacji Microsoft Flow to skróty do przycisków, które stanowią łatwiejszy i szybszy sposób wyzwalania przycisków bezpośrednio z ekranu głównego.
* **Tworzenie kroków „obsługi błędów”** — zdefiniuj jeden lub więcej kroków do uruchomienia po niepowodzeniu akcji. Na przykład uzyskaj powiadomienie natychmiast po tym, gdy przepływowi nie uda się utworzyć rekordu w usłudze Dynamics 365.
* **Zmienne w postaci liczb całkowitych i zmiennoprzecinkowych** — inicjuj liczniki i zmniejszaj oraz zwiększaj ich wartość wewnątrz przebiegu przepływu, aby zliczać uruchomienia konkretnego zestawu logiki.
* **Strona szczegółów przepływu** — po wybraniu przepływu z listy **Moje przepływy** zobaczysz stronę z informacjami na temat tego przepływu, takimi jak historia jego uruchamiania oraz to, kto ma do niego dostęp.
* **Limity przydziałów przebiegów przepływów dla administratorów** — administratorzy mogą teraz monitorować użycie przebiegów przepływów w organizacji względem wspólnego limitu przydziału przebiegów dla firmy i uzyskać podział limitów przydziału w celu zrozumienia, które licencje składają się na limit przydziału.
* **Ulepszenia wyzwalacza żądań HTTP** — używaj różnych metod HTTP i dodawaj segmenty ścieżek do wyzwalacza żądań.
* **Dwa łączniki dla partnerów** — usługa Microsoft Flow może teraz łączyć się z usługą Parserr (do analizowania wiadomości e-mail) i usługą Cognito Forms (do obsługi formularzy online).

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/error-handling/) na temat tej wersji.

### <a name="release-2017-05-12"></a>Wersja 2017-05-12
* **Integracja bibliotek dokumentów programu SharePoint** — Można wybrać dowolny plik w bibliotece dokumentów i uruchomić przepływ, na przykład aby wysłać go do przełożonego w celu zatwierdzenia [i nie tylko](https://flow.microsoft.com/blog/flow-in-spo-document-libraries/).
* **Łącznik programu Microsoft Planner**  — Program Microsoft Planner  pozwala łatwiej łączyć zespoły, zadania, dokumenty i konwersacje w celu osiągania lepszych wyników.
* **Wgląd administratorów w licencje** — Administratorzy widzą wszystkie licencje usług Microsoft Flow i PowerApps (w wersji próbnej i płatnej) w Centrum administracyjnym usługi Microsoft Flow.
* **Plan Community usługi PowerApps** — Plan Community usługi PowerApps jest bezpłatnym planem dla użytkowników indywidualnych, który pozwala eksplorować, uczyć się i poszerzać umiejętności w zakresie usług PowerApps, Microsoft Flow i Common Data Service.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/planner-community-and-licenses/) na temat tej wersji.

### <a name="release-2017-05-09"></a>Wersja 2017-05-09
* **Łącznik usługi Azure AD** — dostępny jest nowy łącznik na potrzeby wykonywania akcji administratora z usługi Microsoft Flow, w tym tworzenia użytkowników lub dodawania ich do grup.
* **Ulepszenia programu Outlook w usłudze Office 365** — przepływy mogą być teraz wyzwalane przez udostępnione skrzynki pocztowe i mogą wysyłać wiadomości e-mail do udostępnionej skrzynki pocztowej. Mogą także ustawiać lub odczytywać automatyczne odpowiedzi.
* **Dostępne w Kanadzie** — teraz możesz tworzyć przepływy w Kanadzie.
* **Tworzenie elementów webhook niestandardowego interfejsu API** — deweloperzy łączników niestandardowych mogą teraz dodać wyzwalacze do niestandardowych interfejsów API z elementami webhook.
* **Zarządzanie właścicielami przepływu w centrum administracyjnym** — administratorzy środowiska mogą zarządzać właścicielami przepływu w centrum administracyjnym usługi Microsoft Flow.
* **Dokumentacja referencyjna łącznika** — teraz udostępniamy [pełną dokumentację referencyjną łącznika w witrynie docs.microsoft.com](https://docs.microsoft.com/Connectors/).
* **Dwie usługi partnerów** — opublikowano dwie nowe usługi świadczone przez partnerów: Nexmo i Paylocity.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/canada-mailboxes-aad) na temat tej wersji.

### <a name="release-2017-04-27"></a>Wersja 2017-04-27
* **Tworzenie przepływów z równoległymi krokami** — twórz przepływy z wykonywaniem równoległym: oznacza to, że możesz mieć dwa lub więcej kroków wykonywanych w dokładnie tym samym czasie.
* **Obsługa pięciu nowych usług** — pięć nowych usług to: Approvals, Benchmark Email, Capsule CRM, LiveChat i Outlook Customer Manager.
* **Monitorowanie ponownych prób dla akcji** — usługa Microsoft Flow będzie ponawiać próby w przypadku występowania błędów dotyczących usług. Teraz będzie można sprawdzać, ile automatycznych ponowień miało miejsce, i przeglądać szczegóły tego, co się stało.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/parallel-actions/) na temat tej wersji.

### <a name="release-2017-04-17---q1-update-for-microsoft-flow"></a>Wersja 2017-04-17 — aktualizacja z 1. kwartału dla usługi Microsoft Flow
* **Nowoczesne funkcje zatwierdzania** — twórz przepływy pracy, w których osoby zatwierdzające mogą bezpiecznie zatwierdzać z aplikacji mobilnej Microsoft Flow lub ujednoliconego centrum zatwierdzenia w witrynie sieci Web Microsoft Flow.
* **Ogólna dostępność przepływów zespołów** — dzięki przepływom zespołów, które są teraz ogólnie dostępne, wiele osób może mieć jeden przepływ i razem nim zarządzać.
* **Tworzenie łączników dla usługi Microsoft Flow** — każdy może bezpłatnie przesłać własny łącznik usługi Microsoft Flow, z którego może korzystać reszta świata.
* **„Odchudzony” projektant** — dla niektórych szablonów nowa wersja projektanta wyświetla jedynie pola wymagane do utworzenia przepływu, co upraszcza pracę.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/q1-2017-update/) na temat tej wersji.

### <a name="release-2017-04-11"></a>Wersja z 11 kwietnia 2017 r.
* **Nowe akcje umożliwiające tworzenie tabel i list** — nowe akcje Utwórz tabelę HTML, Utwórz tabelę CSV i Dołącz, które mogą przetwarzać listy elementów (zamiast poprzedniej pętli Zastosuj do każdego).
* **Wstawianie kroków w dowolnym miejscu** — teraz możesz wstawić nowy krok w dowolnym miejscu w przepływie pracy bez przeciągania i upuszczania.
* **Cztery nowe usługi** — usługa Flow teraz obsługuje usługi 10to8, Act!, Inoreader oraz interfejs API przetwarzania obrazów. Za pomocą interfejsu API przetwarzania obrazów możesz przetwarzać obrazy, aby uzyskać zawartość tekstową (tzw. OCR), lub automatycznie tagować obrazy na podstawie ich zawartości.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/html-tables-csvs-computer-vision/) na temat tej wersji.

### <a name="release-2017-04-03"></a>Wersja 2017-04-03
* **Windows Phone Beta** — program beta aplikacji na Windows Phone umożliwia skorzystanie z wersji zapoznawczej aplikacji w systemie Windows Phone. [Dowiedz się więcej](https://flow.microsoft.com/blog/windows-phone-app-beta-is-now-available/).
* **Muhimbi PDF** — teraz dzięki programowi Muhimbi PDF możesz konwertować pliki programu Microsoft Word do formatu PDF, dodawać znaki wodne, scalać dokumenty i wykonywać wiele innych działań. [Dowiedz się więcej](https://flow.microsoft.com/blog/convert-files-using-muhimbi/).
* **Wyzwalanie przepływów przyciskami fizycznymi** — ogłaszamy partnerstwo z dwoma wiodącymi produktami wśród przycisków fizycznych: Flic firmy Shortcut Labs i Bttn firmy The Button Corporation. [Dowiedz się więcej](https://flow.microsoft.com/blog/physical-buttons/)

### <a name="release-2017-03-22"></a>Wersja 2017-03-22
* **Tworzenie kopii przepływu** — teraz możesz utworzyć kopię przepływu, aby pracować z wersjami roboczymi lub zduplikować przepływ utworzony w przeszłości.
* **Dwie nowe usługi** — obsługa usługi Toodledo umożliwiającej zarządzanie listą zadań do wykonania przez tworzenie i aktualizowanie zadań oraz usługi Zendesk, która zapewnia platformę do obsługi klienta i tworzenia biletów pomocy technicznej.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/make-a-copy/) na temat tej wersji.

### <a name="release-2017-03-15"></a>Wersja 2017-03-15
* **Udostępnianie przycisków współpracownikom** — teraz możesz udostępniać przyciski przepływów innym, co ułatwia użytkownikom biznesowym wykonywanie szybkich zadań.
* **Wyzwalanie przycisków z ekranu głównego** — skróty do przycisków przepływów na ekranie głównym i ekranie blokady urządzeń przenośnych pozwalają wyzwalać przepływ szybciej niż kiedykolwiek wcześniej.
* **Przepływy zespołów w aplikacji usługi Microsoft Flow** — teraz w aplikacji usługi Microsoft Flow dla systemów iOS i Android widzisz przepływy mające innych właścicieli.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/button-sharing/) na temat tej wersji.

### <a name="release-2017-03-10"></a>Wersja 2017-03-10
* **Udoskonalone korzystanie z łączników niestandardowych** — możesz teraz używać kolekcji Postman Collection do tworzenia łączników niestandardowych oraz edytowania, dodawania i testowania akcji.
* **Dwie nowe usługi** — dodano obsługę powiadomień usługi PowerApps oraz oprogramowania PivotalTracker.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/new-updates-custom-api/) na temat tej wersji.

### <a name="release-2017-02-27"></a>Wersja 2017-02-27
* **Wyzwalanie przycisków przepływów** — teraz możesz wyzwalać przyciski przepływów bezpośrednio z witryny sieci Web usługi Microsoft Flow. Po wyświetleniu listy przepływów po prostu wybierz menu „...” i wybierz polecenie Uruchom teraz.
* **Pięć nowych usług** — dodano obsługę usług Oracle Database, Intercom, FreshBooks, LeanKit i WebMerge.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/trigger-flow-buttons-web/) na temat tej wersji.

### <a name="release-2017-02-21"></a>Wersja 2017-02-21
* **Wyświetlanie przepływów środowiska** — administratorzy środowiska mogą teraz wyświetlać pełną listę wszystkich przepływów wewnątrz danego środowiska, a także włączać, wyłączać i usuwać przepływy.
* **Dwie nowe usługi** — dodano obsługę usług Azure Automation i Basecamp 2.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/managing-flow-resources-in-the-admin-center/) na temat tej wersji.

### <a name="release-2017-02-16"></a>Wersja 2017-02-16
* **Pięć nowych usług** — dodano obsługę usług Azure Data Lake, Bitbucket (usługa hostingowa bazująca na sieci Web dla projektów korzystających z kontroli poprawek GIT), Eventbrite, Infusionsoft i Pipedrive.
* **Niestandardowe uwierzytelnianie HTTP** — w projektancie przepływów można teraz używać uwierzytelniania z niestandardowymi punktami końcowymi HTTP.
* **Analizowanie komunikatów JSON** — można teraz analizować dane JSON z wyzwalacza żądania HTTP lub zwrócone z akcji HTTP.
* **Filtrowanie uruchomień przepływów**  — ulepszone filtrowanie uruchomień przepływów z precyzyjniejszymi opcjami, obejmującymi między innymi Uruchomione przepływy lub Anulowane przepływy.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/managing-flow-resources-in-the-admin-center/) na temat tej wersji.

### <a name="release-2017-02-06"></a>Wersja 2017-02-06
* **Przepływy zespołu** — przepływy zespołu umożliwiają wielu użytkownikom wspólne posiadanie przepływu i zarządzanie nim. W przypadku opuszczenia przez kogoś organizacji przepływy utworzone przez tę osobę mogą nadal działać.
* **Udostępnianie łączników niestandardowych** — łączniki niestandardowe (tak jak przepływy zespołu) mogą być udostępniane i można nimi wspólnie zarządzać w obrębie organizacji.
* **Obsługa usług Gmail i LUIS** — możesz łączyć się z usługą Gmail i usługą Language Understanding Intelligent Service w usługach Azure Cognitive Services.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/team-flows/) na temat tej wersji.

### <a name="release-2017-01-30"></a>Wersja 2017-01-30
* **Dane wejściowe przycisku przepływu** — przyciski przepływu mogą teraz odbierać dane wprowadzane przez użytkownika w czasie wykonywania, dzięki czemu autorzy przepływów mogą definiować informacje przekazywane w przypadku naciśnięcia przycisku.
* **Zadania programu Outlook i rozwiązanie HelloSign** — usługa zadań programu Outlook umożliwia zarządzanie zadaniami, natomiast rozwiązanie HelloSign umożliwia tworzenie bezpiecznych podpisów elektronicznych.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/button-user-inputs/) na temat tej wersji.

### <a name="release-2017-01-23"></a>Wersja 2017-01-23
* **Wyszukiwanie według usługi** — przeglądaj według usługi podczas dodawania wyzwalacza lub akcji w celu wyświetlenia wszystkich akcji dla poszczególnych usług.
* **Przypadek przełącznika** — dodaj bloki przełączników, aby uzyskać kilka gałęzi logiki równoległej.
* **Dodatkowe akcje związane z pocztą e-mail** — nowa funkcjonalność w usługach Office 365 Outlook i Outlook.com na potrzeby pracy z oflagowanymi wiadomościami e-mail.
* **Pięć nowych usług** — łączenie się z lokalnymi lub sieciowymi systemami plików, usługa płatnicza Stripe, bazy danych IBM Informix oraz IBM DB2, a także usługa UserVoice.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/search-by-service/) na temat tej wersji.

### <a name="release-2017-01-14"></a>Wersja 2017-01-14
* **Ponowne przesyłanie przebiegów** — jeśli przepływ zakończył się niepowodzeniem i chcesz spróbować go naprawić i uruchomić ponownie, możesz ponownie przesłać przebieg zakończony niepowodzeniem.
* **Anulowanie przebiegów** — w przypadku zablokowania przepływu możesz go teraz jawnie anulować.
* **Dwie nowe usługi** — dodano obsługę usług GoToTraining i GoToWebinar.
* **Linki mobilne** — możesz udostępniać szablony bezpośrednio z aplikacji mobilnej. Dodaliśmy również link do szybkiego pobierania aplikacji w górnej części witryny sieci Web.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/managing-runs/) na temat tej wersji.

### <a name="release-2016-12-29"></a>Wersja 2016-12-29
Usługa Microsoft Flow obsługuje teraz usługę DocuSign w celu zapewnienia wsparcia dla podpisów elektronicznych i cyfrowego zarządzania transakcjami, usługę SurveyMonkey na potrzeby ankiet w sieci Web oraz aplikację OneNote do tworzenia notatek (tylko konta firmowe).

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/final-2016-services/) na temat tej wersji.

### <a name="release-2016-12-20"></a>Wersja 2016-12-20
* **Uruchom teraz** — obecnie możesz wyzwolić wyzwalacz cykliczny na żądanie. Jeśli na przykład masz zaplanowany raport codzienny, ale musisz go utworzyć również **w danym momencie**.
* **Sześć nowych usług** — twórz przepływy łączące się z usługami MSN Pogoda, Medium, Kontakty Google, Buffer, Harvest i TypeForm.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/run-now-and-six-more-services/) na temat tej wersji.

### <a name="release-2016-12-14"></a>Wersja 2016-12-14
Teraz możesz wykorzystać cenne informacje podczas wyzwalania przepływu przycisku, np. miejsce, w którym wyzwolono przycisk, kto to zrobił, kiedy to zrobił itd.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/button-trigger-tokens/) na temat tej wersji.

### <a name="release-2016-12-06"></a>Wersja 2016-12-06
* **Wprowadzenie nauki z przewodnikiem** — rozpocznij od zbioru kolejnych kursów łączących treści wideo z dokumentacją, które pomagają zrozumieć rozbudowane i zaawansowane możliwości usługi Microsoft Flow.
* **Dwie nowe usługi** — przepływy mogą teraz używać usługi Freshdesk (rozwiązanie do świadczenia pomocy technicznej dla klientów) oraz usługi GoToMeeting (narzędzie do spotkań online).
* **Obsługa elementów webhook protokołu HTTP** — przepływy mogą teraz stanowić element docelowy elementów webhook, które będą się automatycznie rejestrować i wyrejestrowywać.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/guided-learning-and-two-services/) na temat tej wersji.

### <a name="release-2016-11-23"></a>Wersja 2016-11-23
* **Obsługa alertów Power BI w usłudze Flow** — przekształć spostrzeżenia w działania, wyzwalając przepływy przy użyciu alertów danych usługi Power BI.
* **Ulepszenia aplikacji mobilnej** — do istniejącego środowiska tworzenia przepływów na podstawie szablonów dodano możliwość tworzenia ich od podstaw. Poprawiono również wydajność wyświetlania przebiegów przepływów.
* **Osiem nowych usług** — teraz możesz już łączyć się z usługami Azure Resource Manager, Azure Queues, Chatter, Disqus, Azure DocumentDB, Cognitive Services Face API, HipChat oraz Wordpress.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/power-bi-and-eight-other-services/) na temat tej wersji.

### <a name="release-2016-11-15"></a>Wersja 2016-11-15
* **Program partnerski usługi Microsoft Flow** — usługa Microsoft Flow ma teraz certyfikowany program partnerski przeznaczony do nawiązywania kontaktów oraz korzystania z różnorodnych umiejętności i doświadczeń w używaniu usługi Microsoft Flow przez firmy na całym świecie.
* **Sześć nowych usług** — w tym tygodniu udostępniamy też sześć usług: Asana, Campfire, EasyRedmine, JIRA, Redmine i Vimeo.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/partner-program-six-new-services/) na temat tej wersji.

### <a name="release-2016-10-31---general-availability"></a>Wersja 2016-10-31 — dostępność ogólna
* **Ceny i licencjonowanie** — teraz dostępna w planach bezpłatnych i płatnych oraz w ramach usług Office 365 i Dynamics 365.
* **Centrum administracyjne usługi Microsoft Flow** — dzięki nowemu centrum administracyjnemu z usługi mogą korzystać przedsiębiorstwa. W centrum administracyjnym można zarządzać środowiskami wewnątrz organizacji.
* **Zasady ochrony przed utratą danych** — administratorzy mogą tworzyć zasady ochrony przed utratą danych, aby kontrolować przepływ danych między usługami.
* **Dostępność w systemie Android** — aplikacja Microsoft Flow na telefon jest teraz dostępna zarówno dla systemu iOS, jak i Android. Aplikacja umożliwia otrzymywanie powiadomień, monitorowanie aktywności i rozpoczynanie przepływów po naciśnięciu przycisku.
* **Nowe elementy interfejsu projektanta** — można teraz przeszukiwać zawartość dynamiczną przekazywaną z kroku do kroku, aby znacznie szybciej tworzyć odwołania do wybranych danych.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/announcing-ga/) na temat tej wersji.

### <a name="release-2016-10-26"></a>Wersja 2016-10-26
* **Przepływy uruchamiane jednym przyciskiem** — istnieje niezliczona liczba operacji, które chcemy wyzwalać w dowolnym momencie i z dowolnego miejsca. Teraz można to zrobić, klikając przycisk na urządzeniu przenośnym.
* **Środowiska** —środowiska to odrębne miejsca do przechowywania przepływów organizacji i zarządzania nimi. Środowiska są zlokalizowane geograficznie, co oznacza, że przepływy, aplikacje i dane firmy znajdujące się w danym środowisku działają w regionie, w którym jest ono zlokalizowane.
* **Sześć nowych usług** — dodanie obsługi Bit.ly, Cognitive Services Text Analytics, Dynamics NAV, Dynamics 365 dla serwisów Financials, Instapaper i Pinterest.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/environments-for-makers/) na temat tej wersji.

### <a name="release-2016-10-16"></a>Wersja 2016-10-16
* **Łączniki niestandardowe obsługują większą liczbę typów uwierzytelniania** — łączniki niestandardowe obsługują teraz uwierzytelnianie kluczy interfejsu API i mogą uwierzytelniać dowolne usługi obsługujące pełną specyfikację OAuth 2.0.
* **Obsługiwane są trzy nowe usługi** — dodaliśmy obsługę usług Basecamp 3, Blogger i PagerDuty.
* **Ulepszenia projektanta** — wydajność jest teraz wyższa. Można aktualizować i naprawiać połączenia bezpośrednio z poziomu menu „...” dowolnej akcji. Dodaliśmy nowy krok, Przerwij, umożliwiający zakończenie działania przebiegu przepływu.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/early-october-updates/) na temat tej wersji.

### <a name="release-2016-09-25"></a>Wersja 2016-09-25
Przepływy można teraz tworzyć przy użyciu telefonów komórkowych. Przeglądaj naszą obszerną galerię szablonów, przewijaj listę usług lub wybieraj kategorie szablonów, aby przechodzić do szczegółów. [Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/mobile-creation/) na temat tej wersji.

### <a name="release-2016-09-22"></a>Wersja 2016-09-22
* **Selektor osób programu Microsoft Graph** — nowy selektor osób programu Microsoft Graph jest zintegrowany bezpośrednio z interfejsem użytkownika usługi Microsoft Flow, co ułatwia wybieranie odpowiednich osób lub adresów e-mail.
* **Obsługa systemu Microsoft Dynamics AX** — obecnie można wykonywać akcje dotyczące danych operacyjnych systemu Dynamics AX Online z poziomu przepływów (od tworzenia nowych rekordów po uruchamianie zapytań dotyczących danych).
* **Dwie nowe usługi partnerów** — usługi appFigures i Insightly są obecnie dostępne z poziomu przepływów.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/more-september-updates/) na temat tej wersji.

### <a name="release-2016-09-14"></a>Wersja 2016-09-14
* **Osadzanie w witrynie sieci Web lub aplikacji** — deweloperzy mogą obecnie osadzać usługę Microsoft Flow w swoich aplikacjach lub witrynach sieci Web, aby zapewnić użytkownikom łatwy sposób automatyzacji zadań osobistych lub służbowych.
* **Używanie przepływu jako punktu końcowego HTTP** — obecnie można używać samego przepływu jako interfejsu API protokołu HTTP. W przepływie jest dostępny wyzwalacz (Żądanie) i możesz zdecydować się na odpowiedzenie na żądanie przychodzące, dodając kartę Odpowiedź.
* **Obsługa aplikacji Todoist** — aplikacja Todoist umożliwia przegląd wszystkich projektów osobistych i służbowych.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/extend-web-site-application/) na temat tej wersji.

### <a name="release-2016-09-01"></a>Wersja 2016-09-01
Usługa Microsoft Flow jest teraz dostępna dla każdego — na początku udostępniliśmy wersję zapoznawczą tylko osobom korzystającym ze służbowych adresów e-mail (np. używanych w ramach usługi Office 365 Business lub Office 365 Enterprise). Obecnie ogłaszamy powszechną dostępność wersji zapoznawczej — usługa jest dostępna bezpłatnie dla wszystkich użytkowników bez względu na używany adres e-mail. [Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/available-for-everyone/) na temat tej wersji.

### <a name="release-2016-08-31"></a>Wersja 2016-08-31
* **Warunki zagnieżdżone** — teraz można dodać drugi (lub trzeci itd.) warunek wewnątrz innego warunku.
* **Zastosuj do każdego** — pętla Zastosuj do każdego umożliwia sterowanie listą powtarzaną.
* **Wykonuj, dopóki** — pętla Wykonuj, dopóki umożliwia powtarzanie kroku, aż określony warunek zostanie spełniony.
* **Filtrowanie macierzy** — dostępny jest jeden krok filtru natywnego umożliwiający zagwarantowanie, że każdy element na liście odpowiada zdefiniowanemu wyrażeniu.
* **Tworzenie zmiennych ciągu** — obecnie możliwe jest tworzenie zmiennych ciągu.
* **Zakresy** — zakresy umożliwiają proste grupowanie co najmniej dwóch akcji.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/build-advanced-flows/) na temat tej wersji.

### <a name="release-2016-08-27"></a>Wersja 2016-08-27
* **Komentarze dotyczące kroków** — komentarze ułatwiają dodawanie adnotacji do pojedynczych akcji. Dzięki dodawanym uwagom można łatwo zapamiętać wymogi dotyczące danego przepływu.
* **Obsługa usługi Smartsheet** — w tym tygodniu dodaliśmy możliwość nawiązania połączenia z usługą Smartsheet. Smartsheet to usługa, która ułatwia współpracę nad arkuszami w chmurze.
* **Udoskonalenia interfejsu użytkownika w zakresie tworzenia przepływów** — nazwa przepływu znajduje się teraz z przodu i na środku, a przycisk zapisywania został przeniesiony na górę strony, aby był łatwo dostępny.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/add-comments-smartsheet/) na temat tej wersji.

### <a name="release-2016-08-18"></a>Wersja 2016-08-18
Można teraz wyświetlać podgląd nowego środowiska nowoczesnych list usługi SharePoint Online obejmującego integrację z usługą Microsoft Flow. [Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/microsoft-flow-integration-with-sharepoint-modern-lists-preview/) na temat tej wersji.

### <a name="release-2016-08-13"></a>Wersja 2016-08-13
* **Visual Studio Team Services** — usługa Flow zapewnia teraz możliwość połączenia usług VSTS z wieloma różnymi usługami, takimi jak poczta usługi O365, Slack, Trello i Wunderlist.
* **Ulepszenia programu SharePoint** — listy programu SharePoint obsługują wiele różnych typów danych: od prostych obiektów, takich jak Pojedynczy wiersz tekstu oraz Data i godzina, po złożone obiekty, takie jak Osoba lub grupa, Odnośnik i Wybór.
* **Testowanie połączeń aplikacji Outlook w ramach usługi O365** — kiedy tworzysz nowe połączenie aplikacji Outlook w ramach usługi O365, testujemy je, aby sprawdzić, czy możesz zacząć z niego korzystać.
* **Kontrolka Wartość logiczna** — dodaliśmy także kontrolkę wartości logicznej, aby było wiadomo, jakie wartości należy wprowadzić w polach wprowadzania danych logicznych, takich jak Ma załączniki w wyzwalaczu Kiedy przyjdzie nowa wiadomość e-mail.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/visual-studio-team-services-enhancements-to-sharepoint-and-o365-outlook-and-boolean-control/) na temat tej wersji.

### <a name="release-2016-08-08"></a>Wersja 2016-08-08
Publiczna wersja zapoznawcza usługi Microsoft Common Data Service zintegrowana z usługą Microsoft Flow. [Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/flow-and-common-data-model/) na temat tej wersji.

### <a name="release-2016-08-05"></a>Wersja 2016-08-05
* **Lokalny program SharePoint** — tak samo jak w usłudze SharePoint Online, można teraz tworzyć przepływy z użyciem list i bibliotek dokumentów w lokalnym programie SharePoint, korzystając ze wstępnie zdefiniowanych szablonów lub tworząc je od podstaw.
* **Dymki informacyjne w projektancie** — w celu szerszego przedstawienia możliwości poszczególnych wyzwalaczy i akcji dodaliśmy dymki informacyjne nad każdym krokiem przepływu.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/sharepoint-on-premises-and-info-bubbles-2/) na temat tej wersji.

### <a name="release-2016-07-15"></a>Wersja 2016-07-15
* **Dodanie czterech nowych usług** — teraz można połączyć się z usługami Kalendarz Google, Zadania Google, YouTube i SparkPost.
* **Zmienianie nazwy akcji** — obecnie poszczególne akcje można odróżnić, nadając im inne nazwy.
* **Różne wartości opóźnienia** — teraz można wybrać dowolną liczbę sekund, minut, godzin i dni.
* **Łatwiejsza obsługa przeglądarki folderów** — uprościliśmy przeglądarkę folderów — teraz wybranie elementu po lewej stronie spowoduje wybranie danego folderu, a wybranie elementu po prawej stronie spowoduje otwarcie danego folderu, co umożliwi wybranie podfolderów.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/new-google-services-rename-more/) na temat tej wersji.

### <a name="release-2016-07-08"></a>Wersja 2016-07-08
Łączność lokalna w usłudze Microsoft Flow może być obsługiwana przy użyciu lokalnej bramy danych. Umożliwia ona ustanawianie bezpiecznych połączeń z programem SQL Server i zintegrowanie ich z przepływami. [Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/on-premises-data-gateway/) na temat tej wersji.

### <a name="release-2016-07-02"></a>Wersja 2016-07-02
* **Obsługa usługi Arkusze Google** — wcześniej zapewnialiśmy możliwość korzystania z programu Excel i usługi Dysk Google, a w tym tygodniu dodajemy obsługę natywnych arkuszy Google.
* **Szybsze rozpoczynanie pracy z poziomu szablonów** — wprowadziliśmy również pewne optymalizacje w sposobie rozpoczynania pracy z poziomu szablonów. Obecnie można wybrać konta, które mają być używane dla szablonu, bezpośrednio podczas pracy na stronie szablonu.
* **Koniec z wygasaniem autoryzacji programu SharePoint i usługi Office 365** — obecnie usługa Microsoft Flow automatycznie odnawia dostęp do usług opartych na usłudze Azure Active Directory, dzięki czemu wszystkie przepływy będą działać nawet po zmianie hasła.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/more-june-updates/) na temat tej wersji.

### <a name="release-2016-06-20"></a>Wersja 2016-06-20
* **Wprowadzenie nowej aplikacji mobilnej dla usługi Microsoft Flow** — dzisiaj mamy przyjemność wprowadzić kolejny ważny element naszej oferty. Jest to aplikacja mobilna, którą można pobrać w systemie iOS (wkrótce także w systemie Android), umożliwiająca śledzenie i eksplorowanie zautomatyzowanych przepływów pracy oraz zarządzanie nimi w dowolnym miejscu i czasie.  
* **Logowanie jednokrotne** — wprowadziliśmy funkcję logowania jednokrotnego umożliwiającą uwierzytelnianie w usłudze Microsoft Flow za pośrednictwem innych usług firmy Microsoft, takich jak Office 365.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/welcome-to-flow-now-more-mobile/) na temat tej wersji.

### <a name="release-2016-06-18"></a>Wersja 2016-06-18
* **Nowa usługa poczty** — obecnie można wysyłać wiadomości e-mail bezpośrednio z usługi Microsoft Flow bez konieczności łączenia się z osobistym lub służbowym kontem e-mail w usłudze Microsoft Flow.
* **Powiadomienia w portalu** — teraz zawsze, gdy wystąpi jakieś uszkodzenie Twoich przepływów, w górnej części portalu zostanie wyświetlone powiadomienie.
* **Wszystkie działania w portalu** — obecnie można przeglądać działania w ramach wszystkich swoich przepływów, klikając nową kartę działań w witrynie sieci Web przepływów.

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/mail-and-all-activity/) na temat tej wersji.

### <a name="release-2016-05-27"></a>Wersja 2016-05-27
* **Przeglądanie szablonów według usług** — obecnie można wyświetlić wszystkie obsługiwane usługi (bez konieczności logowania się). Na tej stronie można wyświetlić opisy poszczególnych usług i zapoznać się z dostępnymi dla nich szablonami.
* **Tworzenie łączników niestandardowych i korzystanie z nich** — podobnie jak w przypadku tworzenia łączników niestandardowych w usłudze PowerApps, można także połączyć się z własnymi interfejsami API bezpośrednio w witrynie flow.microsoft.com:
* **Testowanie przepływów przed zakończeniem** — po każdym zapisie przepływu można obecnie przeglądać na żywo wyniki przebiegu przepływu na stronie (w przypadku wykonaniu akcji uruchomienia).

[Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/may-updates-to-microsoft-flow/) na temat tej wersji.

### <a name="release-2016-05-07"></a>Wersja 2016-05-07
Dodano dwie nowe usługi: Microsoft Project Online i Mandrill firmy Mailchimp. [Dowiedz się więcej i zadaj pytania](https://flow.microsoft.com/blog/announcing-microsoft-flow-webinars/) na temat tej wersji.

### <a name="release-2016-04-27---public-preview"></a>Wersja 2016-04-27 — publiczna wersja zapoznawcza
Jeśli używasz przepływów logiki w ramach usługi [Microsoft PowerApps](https://powerapps.microsoft.com), wersja zapoznawcza usługi Microsoft Flow oferuje kilka nowych funkcji:

* Przeglądanie galerii dziesiątek szablonów i sortowanie ich według popularności, nazwy lub daty publikacji.
* Po dostosowaniu przepływu możesz [publikować własne szablony](publish-a-template.md) w galerii.
* Wyświetlanie historii dla każdego sprawdzenia i uruchomienia przepływu.
* Po zapisaniu przepływu możesz [natychmiast obejrzeć go w działaniu](see-a-flow-run.md), po prostu wykonując akcję wyzwalacza.
* Mamy dla Ciebie [nową społeczność](https://go.microsoft.com/fwlink/?LinkID=787467) umożliwiającą dyskutowanie na temat usługi Flow oraz [przesyłanie pomysłów](https://go.microsoft.com/fwlink/?LinkID=787474).

## <a name="next-steps"></a>Następne kroki
Jeśli masz jakiekolwiek problemy, które nie zostały już omówione w tych informacjach o wersji ani w [często zadawanych pytaniach](frequently-asked-questions.md), [dołącz do naszej społeczności](https://go.microsoft.com/fwlink/?LinkID=787467), aby zadawać pytania, lub [skontaktuj się z pomocą techniczną](http://go.microsoft.com/fwlink/?LinkID=787479).

