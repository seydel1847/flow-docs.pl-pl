---
title: Zastępowanie okien dialogowych za pomocą przepływów procesów biznesowych lub aplikacji kanwy | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- flow
ms.assetid: 046480e6-f2ff-4c56-9e03-f642c982ff7d
caps.latest.revision: 12
author: Mattp123
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 87a12345c72fd3dd3e93c1afecd282a688e4d4d1
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691094"
---
# <a name="replace-dialogs-with-business-process-flows-or-canvas-apps"></a>Zastępowanie okien dialogowych za pomocą przepływów procesów biznesowych lub aplikacji kanwy

[Okna dialogowe są przestarzałe](https://docs.microsoft.com/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#dialogs-are-deprecated), dlatego powinny zostać zastąpione przepływami procesów biznesowych lub aplikacjami kanwy. W tym temacie opisano różne możliwości udostępniane przez te opcje oraz przedstawiono sytuacje, w których można zastąpić istniejące okno dialogowe za pomocą przepływu procesów biznesowych lub aplikacji kanwy osadzonej w formularzu opartym na modelu.

## <a name="feature-capability-comparison"></a>Porównanie funkcji

Poniższa tabela zawiera zestaw funkcji okna dialogowego oraz odpowiadających im funkcji udostępnianych przez przepływy procesów biznesowych oraz aplikacje kanwy.


|Funkcja okna dialogowego  | Dostępność funkcji w przepływach procesów biznesowych  | Dostępność funkcji w aplikacjach kanwy  |
|---------|---------|---------|
|Strona     | Tak <br/> (etap procesu biznesowego)    | Tak <br/> (ekran aplikacji)        |
|Tylko monit   |  Nie    |  Tak <br/> (etykiety)        |
|Monit i odpowiedź     |  Tak <br/> (tylko atrybuty encji)    | Tak <br/> (etykiety i pola wejściowe)    |
|Argumenty wejściowe     |  Ograniczone <br/> (kroki etapu procesu biznesowego)    | Tak <br/> (parametry ciągu zapytania)     |
|Zmienne   |  Nie     |  Tak       |
|Zmienne zapytania    |  Nie     |  Tak     |
|Logika rozgałęziania warunkowego    |  Tak     | Tak <br/>  (przechodzenie do dowolnego ekranu w aplikacji)    |
|Ponowne użycie <br/> (uruchamianie jako okno podrzędne)   |  Nie     | Tak <br/> (przechodzenie do dowolnego ekranu w aplikacji, uruchamianie innej aplikacji w nowym oknie)     |
|Uruchamianie przepływów pracy na początku/na końcu    |   Tak      |  Nie <br/> (należy użyć przepływu)  |
|Uruchamianie przepływów pracy przy wprowadzeniu danych    | Tak    | Nie <br/> (należy użyć przepływu)   |
|Uruchamianie przepływów pracy przy przejściu do strony   |  Tak       | Nie <br/> (należy użyć przepływu)    |
|Uruchamianie przy użyciu adresu URL  |   Nie      |  Tak     |
|Rejestrowanie sesji    |  Tak       |  Nie     |
|Obsługa zestawu SDK   |  Tak     |  Tak     |

### <a name="additional-capabilities-with-business-process-flows"></a>Dodatkowe funkcje udostępniane przez przepływy procesów biznesowych
- Analiza procesów (widoki, wykresy i czas korzystania z etapu)
- Kontrolki niestandardowe

### <a name="additional-capabilities-with-canvas-apps"></a>Dodatkowe funkcje udostępniane przez aplikacje kanwy
- Analiza aplikacji (użycie i wydajność aplikacji)
- Kompozycja strony obejmująca wiele encji
- Uruchamianie przepływów
- Łączniki danych (standardowe i niestandardowe)
- Uruchamianie jako aplikacji autonomicznej
- Możliwość konfigurowania układu

## <a name="choosing-between-a-business-process-flow-or-canvas-app"></a>Przepływ procesów biznesowych a aplikacja kanwy — co wybrać?
Podczas wybierania metody zastępowania okna dialogowego należy uwzględnić środowisko, w którym będzie pracować użytkownik. Należy również pamiętać o tym, że prawie wszystkie okna dialogowe można modelować przy użyciu aplikacji kanwy.

Przepływy procesów biznesowych sprawdzają się w przypadku zastępowania okien dialogowych służących do modelowania procesów, które udostępniają wskazówki w ogólnym strumieniu pracy wymagającym współpracy między grupami osób i kontekstu aplikacji Dynamics 365. Przykłady obejmują przeglądy i kierowanie ofert. 

Z kolei aplikacji kanwy można użyć do zastępowania okien dialogowych służących do modelowania zadań normatywnych, takich jak skrypt rozmów umożliwiający pozyskiwanie potencjalnych klientów lub upraszczanie środowiska użytkownika na potrzeby wykonywania innych zadań, na przykład aktualizowania szansy sprzedaży. Zwróć uwagę, że w tych scenariuszach korzystne może być nawet używanie autonomicznej aplikacji kanwy. 

## <a name="dialog-replacement-using-business-process-flow-scenario"></a>Zastępowanie okna dialogowego w scenariuszu z użyciem przepływu procesów biznesowych
Wyobraźmy sobie okno dialogowe, które zawiera wiele stron. Umożliwia ono wprowadzanie małych porcji kluczowych informacji, generowanie oferty oraz wysyłanie wiadomości e-mail do weryfikatorów, którzy akceptują lub odrzucają tę ofertę przed jej wysłaniem do klienta. Modelowanie tego rodzaju procesu jest bardziej efektywne w przypadku korzystania z przepływu procesów biznesowych. 

Aby zastąpić okno dialogowe, należy zacząć od zidentyfikowania kluczowych etapów procesu. Mogą one obejmować etap *przygotowywania zawartości*, który zapewnia uwzględnienie wszystkich produktów i zastosowanie rabatów, etap *generowania oferty*, w którym utworzona oferta jest sprawdzana pod kątem poprawności formatu, etap *głównej weryfikacji*, w którym oferta jest wysyłana do zatwierdzenia, etap *dodatkowej weryfikacji*, w którym oferta jest sprawdzana w określonych okolicznościach, oraz końcowy etap — *dostarczania oferty* — w którym oferta jest wysyłana do klienta.

Następnie należy zidentyfikować kluczowe kroki, które użytkownicy muszą wykonać w procesie. Na przykład etap *przygotowywania zawartości* może zawierać prosty krok logiczny umożliwiający użytkownikowi sprawdzenie produktów zawartych w ofercie, obowiązkowy krok wyszukiwania służący do wybrania cennika oraz krok liczbowy, który pozwala wprowadzić rabat przed przejściem do kolejnego etapu. Etap *generowania oferty* może zawierać [krok akcji](create-business-process-flow.md#add-an-on-demand-action-to-a-business-process-flow) umożliwiający utworzenie oferty na podstawie wszystkich informacji pobranych na etapie *przygotowywania zawartości* oraz powiązanego rekordu usługi Dynamics 365. Etapy *głównej weryfikacji* i *dodatkowej weryfikacji* mogą zawierać kilka kroków logicznych ułatwiających przegląd oferty oraz wymagany krok umożliwiający przechwycenie stanu zatwierdzenia oraz zapewnienie, że do kolejnego etapu procesu można przejść dopiero po otrzymaniu zatwierdzenia. Skonfigurowanie [zabezpieczeń na poziomie pola](/customer-engagement/admin/field-level-security) pozwala zagwarantować zatwierdzanie ofert tylko przez autoryzowanych weryfikatorów.  Ponadto do etapów *głównej weryfikacji* i *dodatkowej weryfikacji* można dodać przepływ pracy, który wysyła wiadomości e-mail z powiadomieniami do wszystkich weryfikatorów. 

Na koniec należy skonfigurować etapy i kroki przepływu procesów biznesowych oraz logikę warunkową sterującą przepływem procesów. W tym przykładzie po etapie *głównej weryfikacji* można dodać [gałąź warunkową](enhance-business-process-flows-branching.md) — jeśli krok wskazuje na potrzebę drugiej weryfikacji, kolejnym etapem procesu jest *dodatkowa weryfikacja*; w przeciwnym razie kolejnym etapem jest *dostarczanie oferty*.

Aby udostępnić przepływ procesów biznesowych innym osobom, upewnij się, że odpowiedni użytkownicy mają uprawnienia do tego przepływu, a następnie aktywuj go.

Aby uzyskać więcej informacji o tworzeniu przepływu procesów biznesowych, zobacz [Samouczek: tworzenie przepływu procesów biznesowych umożliwiającego standaryzowanie procesów](create-business-process-flow.md).

## <a name="dialog-replacement-using-canvas-app-scenario"></a>Zastępowanie okna dialogowego w scenariuszu z użyciem aplikacji kanwy

Załóżmy, że mamy okno dialogowe, które działa zgodnie ze skryptem rozmów ułatwiającym sprzedawcom prowadzenie akwizycji telefonicznej. Ten proces można łatwo przechwycić za pomocą aplikacji kanwy.

Najpierw trzeba się połączyć ze źródłami danych, z których będą odczytywane i do których będą zapisywane dane. W tym przykładzie do uzyskiwania informacji o klientach i potencjalnych klientach oraz danych kontaktowych jest używane [połączenie z usługą Dynamics 365](/powerapps/maker/canvas-apps/connections/connection-dynamics-crmonline).

Na początku ustal, ile ekranów będzie potrzebnych. W tym przykładzie może to być pięć ekranów. 
-   Ekran 1. Wybieranie potencjalnego klienta z listy kontaktów do akwizycji telefonicznej.
-   Ekran 2. Przedstawianie się, sprawdzanie możliwości przeprowadzenia rozmowy oraz planowanie kolejnej rozmowy za kilka dni. 
-   Ekran 3. Ustalanie budżetu, upoważnień, wymagań i osi czasu. 
-   Ekran 4. Przechwytywanie następnych kroków i planowanie kolejnych rozmów. 
-   Ekran 5. Podziękowanie potencjalnemu klientowi za poświęcenie czasu na rozmowę.

Kolejnym krokiem jest utworzenie poszczególnych ekranów. Na pierwszym ekranie [utwórz galerię](/powerapps/maker/canvas-apps/customize-layout-sharepoint) potencjalnych klientów, do których należy zadzwonić. Na drugim ekranie utwórz tytuły za pomocą etykiet oraz podaj skrypt rozmów. Użyj kontrolek, takich jak przyciski radiowe, w celu ustalenia, czy celowe jest prowadzenie rozmowy w danym momencie. Jeśli tak, za pomocą logiki warunkowej włącz przycisk umożliwiający przejście do następnego ekranu. W przeciwnym razie na bieżącym ekranie wyświetl skrypt, który pozwala zaplanować rozmowę z klientem w późniejszym czasie. W podobny sposób zdefiniuj skrypt rozmów na następnych ekranach.

Na koniec [zdefiniuj mechanizm nawigacji między ekranami](/powerapps/maker/canvas-apps/functions/function-navigate). W tym przykładzie oprócz sekwencyjnego nawigowania po ekranach możesz chcieć przechodzić od drugiego do ostatniego ekranu (koniec skryptu z podziękowaniem za poświęcony czas), jeśli potencjalny klient nie jest zainteresowany rozmową.

Aby udostępnić tę aplikację użytkownikom, musisz ją opublikować. Zastanów się, jak można przekształcić taki scenariusz dzięki dostępności aplikacji autonomicznej, która udostępnia skrypty rozmów oraz umożliwia szybkie wprowadzanie danych.

Załóżmy, że chcesz osadzić to środowisko w usłudze Dynamics 365 for Sales. Aby to zrobić, najpierw utwórz element iframe na formularzu usługi Dynamics 365 for Sales. Następnie przejdź do sekcji **Aplikacje** w menu usługi PowerApps, wybierz opublikowaną aplikację, skopiuj link internetowy z karty **Szczegóły** i wklej go jako adres URL elementu iframe. 

Można pójść o krok dalej — załóżmy, że chcesz, aby ta aplikacja była dostępna bezpośrednio na głównym formularzu potencjalnego klienta i znajdowała się w kontekście potencjalnego klienta, tak aby użytkownik nie musiał go wybierać na pierwszym ekranie. Aby przekazać odpowiednie informacje do aplikacji, wystarczy po prostu zmodyfikować adres URL elementu iframe, dołączając ciąg zapytania zawierający te informacje, na przykład identyfikatory klienta lub potencjalnego klienta, przy użyciu języka JavaScript uruchamianego po wystąpieniu określonego zdarzenia, takiego jak załadowanie formularza. Następnie należy zaktualizować aplikację, usuwając pierwszy ekran (do wybierania potencjalnego klienta). Dostęp do wartości przekazywanych do aplikacji będzie realizowany za pośrednictwem ciągu zapytania za pomocą [funkcji Param](/powerapps/maker/canvas-apps/functions/function-param).

## <a name="dialog-replacement-faq"></a>Zastępowanie okien dialogowych — często zadawane pytania

Czy są śledzone zależności w aplikacjach kanwy? 
- Zależności w aplikacjach kanwy są śledzone tak samo jak zależności w usłudze Dynamics 365 for Customer Engagement.

Czy można uruchomić aplikację kanwy jako okno podręczne, korzystając z przycisku na pasku poleceń?
- Tak. Aby to zrobić, wystarczy ustawić docelowy adres URL na adres aplikacji kanwy uzyskany w sekcji **Szczegóły** aplikacji zgodnie z wcześniejszymi instrukcjami.

Czy można wywoływać przepływy pracy w aplikacji kanwy?
- To nie jest obsługiwane. Zamiast tego zalecamy użycie przepływu. Aby uzyskać więcej informacji, zobacz: [Wprowadzenie do przepływów przycisku z danymi wejściowymi użytkownika](button-flow-with-user-input-tokens.md).

Czy można automatycznie konwertować okna dialogowe na przepływy procesów biznesowych lub aplikacje kanwy?
- Nie można przekonwertować okien dialogowych na przepływy procesów biznesowych lub aplikacje kanwy w sposób automatyczny.


## <a name="see-also"></a>Zobacz także
[Samouczek: tworzenie przepływu procesów biznesowych umożliwiającego standaryzowanie procesów](create-business-process-flow.md) </br>
[What are canvas apps in PowerApps? (Co to są aplikacje kanwy w usłudze PowerApps?)](/powerapps/maker/canvas-apps/getting-started)


