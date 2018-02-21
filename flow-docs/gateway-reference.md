---
title: Informacje o lokalnych bramach danych | Microsoft Docs
description: "Informacje referencyjne oraz informacje dotyczące instalacji lokalnych bram danych i rozwiązywania problemów, które ich dotyczą"
services: 
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/15/2017
ms.author: deonhe
ms.openlocfilehash: 73567d4d553ceac1d2cee46feb07ad9a6e7ade33
ms.sourcegitcommit: 0b7964058416fd8d5e355913eea27172f1c61992
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="understand-on-premises-data-gateways-for-microsoft-flow"></a>Informacje o lokalnych bramach danych dla programu Microsoft Flow
Przy użyciu lokalnych bram danych w usłudze Microsoft Flow możesz ustanawiać bezpieczne połączenia z lokalnymi źródłami danych, takimi jak program Microsoft SQL Server.

## <a name="installation-and-configuration"></a>Instalacja i konfiguracja
### <a name="prerequisites"></a>Wymagania wstępne
Minimalne:

* [.NET Framework 4.6](https://www.microsoft.com/download/details.aspx?id=48130)
* 64-bitowa wersja systemu Windows 7 lub Windows Server 2008 R2 (lub nowszego)

Zalecane:

* 8-rdzeniowy procesor CPU
* 8 GB pamięci RAM
* 64-bitowa wersja systemu Windows Server 2012 R2 (lub nowszego)

Zagadnienia powiązane:

* Bramy nie można instalować na kontrolerze domeny.
* Bramy nie należy instalować na komputerze, takim jak laptop, który może zostać wyłączony, uśpiony lub może utracić połączenie z Internetem.
* Wydajność bramy może ulec pogorszeniu w przypadku korzystania z sieci bezprzewodowej.

## <a name="install-a-gateway"></a>Instalowanie bramy
> [!IMPORTANT]
> Bramy danych programu Microsoft SharePoint obsługują teraz zarówno ruch HTTP, jak i HTTPS.
> 
> 

1. [Pobierz instalator](https://go.microsoft.com/fwlink/?LinkID=820931), a następnie go uruchom.
   
    ![Uruchamianie instalatora](./media/gateway-reference/run-installer.png)
2. Na pierwszym ekranie kreatora instalacji wybierz przycisk **Dalej**, aby potwierdzić przypomnienie dotyczące instalowania bramy na laptopie.
   
    ![Ekran przypomnienia](./media/gateway-reference/laptop-reminder.png)
3. Wybierz lokalizację instalacji.
4. Zaakceptuj warunki użytkowania i zasady zachowania poufności.
5. Wybierz przycisk **Zainstaluj**.
   
    ![ekran lokalizacji](./media/gateway-reference/location.png)
6. W oknach dialogowych **Kontrola konta użytkownika** wybierz przycisk **Tak**, aby kontynuować.
7. Na ekranie **Lokalna brama danych** wpisz adres e-mail konta, przy użyciu którego zalogujesz się do bramy, wybierz pozycję **Zaloguj**, a następnie dokończ proces logowania.
   
    ![Logowanie](./media/gateway-reference/sign-in.png)

## <a name="register-new-gateway-or-take-over-existing-gateway"></a>Rejestrowanie nowej bramy lub przejmowanie istniejącej bramy
1. Wybierz pozycję **Zarejestruj nową bramę na tym komputerze** lub **Zmigruj, przywróć lub przejmij istniejącą bramę**, a następnie wybierz przycisk **Dalej**.
   
    ![Wybór nowej lub istniejącej bramy](./media/gateway-reference/new-existing.png)
2. Aby skonfigurować nową bramę, wprowadź nazwę w polu **Nazwa nowej lokalnej bramy danych**, wprowadź klucz odzyskiwania w polu **Klucz odzyskiwania** i wprowadź ten sam klucz w polu **Potwierdź klucz odzyskiwania**. Wybierz pozycję **Skonfiguruj**, a następnie pozycję **Zamknij**.
   
    ![Konfigurowanie nowej bramy](./media/gateway-reference/configure-new.png)
3. Podaj klucz odzyskiwania zawierający co najmniej osiem znaków i zapisz go w bezpiecznym miejscu. Ten klucz będzie potrzebny, jeśli zdecydujesz się na migrację, przywrócenie lub przejęcie przypisanej do niego bramy.
4. Aby zmigrować, przywrócić lub przejąć istniejącą bramę, podaj jej nazwę i jej klucz odzyskiwania, wybierz przycisk **Dalej**, a następnie postępuj zgodnie z wszelkimi dodatkowymi monitami.
   
    ![Odzyskiwanie istniejącej bramy](./media/gateway-reference/recover-existing.png)

## <a name="restart-the-gateway"></a>Ponowne uruchomienie bramy
Brama działa jako usługa systemu Windows i, podobnie jak w przypadku wszelkich innych usług systemu Windows, można uruchamiać i zatrzymywać ją na wiele sposobów. Można na przykład otworzyć wiersz polecenia z podwyższonym poziomem uprawnień na maszynie, na której działa brama, a następnie uruchomić jedno z następujących poleceń:

* Aby zatrzymać usługę, uruchom następujące polecenie:

```batchfile
    net stop PBIEgwService
```

* Aby uruchomić usługę, uruchom następujące polecenie:

```batchfile
    net start PBIEgwService
```

## <a name="configure-a-firewall-or-proxy"></a>Konfigurowanie zapory lub serwera proxy
Wskazówki dotyczące podawania informacji dotyczących serwera proxy dla bramy zawiera temat [Konfigurowanie ustawień serwera proxy](https://powerbi.microsoft.com/documentation/powerbi-gateway-proxy/).

Aby sprawdzić, czy zapora lub serwer proxy blokuje połączenia, należy uruchomić poniższą komendę z wiersza polecenia programu PowerShell. To polecenie spowoduje przetestowanie łączności z usługą Azure Service Bus. Przy użyciu tego polecenia można sprawdzić tylko połączenie sieciowe. Polecenie to nie ma wpływu na usługę serwera w chmurze ani na bramę. W ten sposób można ustalić, czy maszyna ma łączność z Internetem.

```powershell
Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350
```

Wynik powinien wyglądać jak poniższe dane wyjściowe. Jeśli parametr **TcpTestSucceeded** nie ma wartości *true*, może to oznaczać, że ruch jest blokowany przez zaporę.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

W celu sprawdzenia wszystkich możliwości należy zastąpić wartości parametrów **ComputerName** i **Port** wartościami z sekcji **Konfigurowanie portów** w dalszej części niniejszego tematu.

Zapora może również blokować połączenia, które usługa Azure Service Bus nawiązuje z centrami danych platformy Azure. Jeśli tak jest rzeczywiście, wszystkie [adresy IP](https://www.microsoft.com/download/details.aspx?id=41653) z regionu dla tych centrów danych należy umieścić na liście dozwolonych adresów IP (należy je odblokować).

## <a name="configure-ports"></a>Konfigurowanie portów
Brama tworzy połączenie wychodzące do usługi Azure Service Bus. Komunikuje się na portach wyjściowych: TCP 443 (domyślnie), 5671, 5672 i od 9350 do 9354. Brama nie wymaga portów wejściowych.

Dowiedz się więcej o [rozwiązaniach hybrydowych](https://azure.microsoft.com/documentation/articles/service-bus-fundamentals-hybrid-solutions/).

| Nazwy domen | Porty wyjściowe | Opis |
| --- | --- | --- |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443, 9350-9354 |Odbiorniki usługi Service Bus Relay przez TCP (wymagany jest port 443 w celu pozyskania tokenu kontroli dostępu) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| *.msftncsi.com |443 |Służy do testowania łączności z Internetem, gdy brama jest nieosiągalna. |

Jeśli na liście dozwolonych adresów konieczne jest umieszczenie adresów IP zamiast domen, wówczas można pobrać i używać [listy zakresów IP centrum danych platformy Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653). W niektórych przypadkach połączenia usługi Azure Service Bus będą nawiązywane z adresami IP zamiast z w pełni kwalifikowanymi nazwami domen.

## <a name="sign-in-account"></a>Konto logowania
Użytkownicy będą się logować za pomocą konta służbowego. Jest to Twoje konto organizacji. Jeśli zarejestrujesz się, aby skorzystać z oferty Office 365, ale nie podasz służbowego adresu e-mail, może to być adres podobny do nancy@contoso.onmicrosoft.com. Konto w ramach usługi w chmurze jest przechowywane w dzierżawie w usłudze Azure Active Directory (AAD). W większości przypadków główna nazwa użytkownika konta usługi AAD będzie zgodna z adresem e-mail.

## <a name="windows-service-account"></a>Konto usługi systemu Windows
Lokalna brama danych jest skonfigurowana do używania identyfikatora *NT SERVICE\PBIEgwService* jako poświadczeń logowania do usługi systemu Windows. Domyślnie ten identyfikator ma uprawnienia do logowania się jako usługa. Jest to w kontekście maszyny, na której instalujesz bramę.

Nie jest to konto używane do nawiązywania połączenia z lokalnymi źródłami danych ani konto służbowe używane do logowania się w usługach w chmurze.

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="general-questions"></a>Pytania ogólne
**Pytanie:** Jakie źródła danych obsługuje brama?
**Odpowiedź:**

* SQL Server
* SharePoint
* Oracle
* Informix
* System plików
* DB2

**Pytanie:** Czy potrzebuję bramy w przypadku źródeł danych w chmurze, takich jak usługa SQL Azure?
**Odpowiedź:** Nie. Brama łączy się tylko z lokalnymi źródłami danych.

**Pytanie:** Jak nazywa się rzeczywista usługa systemu Windows?
**Odpowiedź:** W obszarze Usługi brama ma nazwę **Power BI Enterprise Gateway Service**.

**Pytanie:** Czy istnieją jakiekolwiek połączenia przychodzące do bramy z chmury?
**Odpowiedź:** Nie. Brama używa połączeń wychodzących do usługi Azure Service Bus.

**Pytanie:** Co zrobić po zablokowaniu połączeń wychodzących? Co muszę otworzyć?
**Odpowiedź:** Sprawdź [porty](gateway-reference.md#configure-ports) i hosty, których używa brama.

**Pytanie:** Czy brama musi być zainstalowana na tej samej maszynie co źródło danych?
**Odpowiedź:** Nie. Brama połączy się ze źródłem danych przy użyciu podanych informacji o połączeniu. W tym kontekście bramę należy traktować jako aplikację kliencką. Należy tylko zadbać o możliwość jej połączenia z serwerem o podanej nazwie.

**Pytanie:** Jakie jest opóźnienie, po jakim uruchamiane są zapytania względem źródła danych z bramy? Jaka jest najlepsza architektura?
**Odpowiedź:** Aby zmniejszyć opóźnienia sieci, należy zainstalować bramę tak blisko źródła danych, jak to możliwe. Opóźnienia zostaną zminimalizowane, jeśli można zainstalować bramę na rzeczywistym źródle danych. Uwzględnij również centra danych. Jeśli na przykład Twoja usługa używa centrum danych w regionie Zachodnie stany USA, a program SQL Server jest hostowany na maszynie wirtualnej platformy Azure, wówczas maszyna wirtualna platformy Azure również powinna się znajdować w regionie Zachodnie stany USA. Spowoduje to zminimalizowania opóźnień i pozwoli uniknąć opłat za ruch wychodzący na maszynie wirtualnej platformy Azure.

**Pytanie:** Czy istnieją jakieś wymagania dotyczące przepustowości sieci?
**Odpowiedź:** Zalecana jest dobra przepływność na potrzeby połączenia sieciowego. Każde środowisko jest inne, a ilość wysyłanych danych będzie wpływać na wyniki. Korzystanie z usługi ExpressRoute może pomóc w zapewnieniu odpowiedniego poziomu przepływności między lokalnymi centrami danych a centrami danych platformy Azure.

W celu określenia przepustowości sieci można użyć narzędzia innej firmy, którym jest [aplikacja Azure Speed Test](http://azurespeedtest.azurewebsites.net/).

**Pytanie:** Czy usługa systemu Windows bramy może działać z kontem usługi Azure Active Directory?
**Odpowiedź:** Nie. Usługa systemu Windows musi mieć prawidłowe konto systemu Windows. Domyślnie usługa będzie uruchamiana z następującym identyfikatorem SID usługi: *NT SERVICE\PBIEgwService*.

**Pytanie:** W jaki sposób wyniki są wysyłane do chmury?
**Odpowiedź:** Wyniki są wysyłane przy użyciu usługi Azure Service Bus. Aby uzyskać więcej informacji, zobacz [jak to działa](gateway-reference.md#how-the-gateway-works).

**Pytanie:** gdzie przechowywane są moje poświadczenia?
**Odpowiedź:** Wprowadzone poświadczenia dotyczące źródła danych są zaszyfrowane i przechowywane w usłudze bramy w chmurze. Poświadczenia są odszyfrowywane lokalnie w bramie.

### <a name="high-availabilitydisaster-recovery"></a>Wysoka dostępność/odzyskiwanie po awarii
**Pytanie:** Czy jest planowane umożliwienie realizacji scenariuszy wysokiej dostępności w ramach bramy?
**Odpowiedź:** Mamy to w planach, ale nie ustaliliśmy jeszcze terminu realizacji takich założeń.

**Pytanie:** Jakie opcje są dostępne na potrzeby odzyskiwania po awarii?
**Odpowiedź:** w celu przywrócenia lub przeniesienia bramy można użyć klucza odzyskiwania.

**Pytanie:** Jakie korzyści wynikają z korzystania z klucza odzyskiwania?
**Odpowiedź:** Jest to sposób migracji lub odzyskiwania ustawień bramy.

### <a name="troubleshooting-questions"></a>Pytania dotyczące rozwiązywania problemów
**Pytanie:** Gdzie znajdują się dzienniki bramy?
**Odpowiedź:** Zobacz sekcję [Narzędzia](gateway-reference.md#tools) w dalszej części tego tematu.

**Pytanie:** Jak sprawdzić, jakie zapytania są wysyłane do lokalnego źródła danych?
**Odpowiedź:** Można włączyć śledzenie zapytań, co obejmie właśnie wysyłane zapytania. Po zakończeniu rozwiązywania problemów należy przywrócić pierwotną wartość. Pozostawienie włączonego śledzenia zapytań spowoduje, że dzienniki będą większe.

Można również sprawdzać informacje w narzędziach, z których korzysta źródło danych do śledzenia zapytań. Można na przykład korzystać z narzędzia Extended Events, rozwiązania SQL Profiler for SQL Server albo z usług Analysis Services.

## <a name="how-the-gateway-works"></a>Jak działa brama
![Jak to działa](./media/gateway-reference/gateway-arch.png)

Gdy użytkownik użyje elementu, który jest połączony z lokalnym źródłem danych:

1. Usługa w chmurze tworzy zapytanie oraz zaszyfrowane poświadczenia dla źródła danych, a następnie wysyła zapytanie do kolejki, którą przetwarza brama.
2. Usługa bramy w chmurze analizuje zapytanie i wypycha żądanie do usługi [Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/).
3. Lokalna brama danych odpytuje usługę Azure Bus Service pod kątem oczekujących żądań.
4. Brama uzyskuje zapytanie, odszyfrowuje poświadczenia i łączy się ze źródłami danych przy użyciu tych poświadczeń.
5. Brama wysyła zapytanie do źródła danych w celu wykonania.
6. Wyniki są wysyłane ze źródła danych do bramy, a następnie do usługi w chmurze. Następnie usługa korzysta z wyników.

## <a name="troubleshooting"></a>Rozwiązywanie problemów
### <a name="update-to-the-latest-version"></a>Aktualizowanie do najnowszej wersji
Gdy wersja bramy jest nieaktualna, może pojawić się wiele problemów. Upewnij się, że korzystasz z najnowszej wersji.  Jeśli brama nie była ostatnio aktualizowana, warto zainstalować najnowszą wersję i sprawdzić, czy można odtworzyć problem.

#### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Błąd: nie można dodać użytkownika do grupy.  (-2147463168   PBIEgwService   Użytkownicy dzienników wydajności   )
Ten błąd może pojawić się przy próbie zainstalowania bramy na kontrolerze domeny, co nie jest obsługiwane. Bramę należy zainstalować na maszynie, która nie jest kontrolerem domeny.

## <a name="tools"></a>Narzędzia
### <a name="collecting-logs-from-the-gateway-configurator"></a>Zbieranie dzienników z konfiguratora bramy
Istnieje możliwość zebrania kilku dzienników dotyczących bramy. Zawsze zaczynaj od dzienników.

1. Dzienniki instalatora
   
    %localappdata%\Temp\On-premises_data_gateway_*.log
2. Dzienniki konfiguracji
   
    %localappdata%\Microsoft\on-premises data gateway\GatewayConfigurator*.log
3. Dzienniki usługi bramy przedsiębiorstwa
   
    C:\Użytkownicy\PBIEgwService\AppData\Local\Microsoft\on-premises data gateway\Gateway*.log
4. Dzienniki zdarzeń

Dziennik zdarzeń **usługi lokalnej bramy danych** znajdują się w obszarze **Dzienniki aplikacji i usług**.

![Dzienniki zdarzeń](./media/gateway-reference/event-logs.png)

### <a name="fiddler-trace"></a>Narzędzie śledzenia Fiddler
[Fiddler](http://www.telerik.com/fiddler) jest bezpłatnym narzędziem firmy Telerik i służy do monitorowania ruchu HTTP.  Ruch przychodzący i wychodzący można sprawdzać za pomocą usługi Power BI z maszyny klienckiej. W ten sposób można uzyskiwać informacje o błędach oraz inne istotne szczegóły.

