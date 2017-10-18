---
title: "Często zadawane pytania | Microsoft Docs"
description: "Odpowiedzi na kilka często zadawanych pytań dotyczących usługi Microsoft Flow"
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
ms.date: 03/15/2017
ms.author: stepsic
ms.openlocfilehash: 5b8deda5f22bcc1fa7cfa37a0d4244f26c2004a4
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania
## <a name="audience-and-strategy"></a>Odbiorcy i strategia
### <a name="what-is-microsoft-flow"></a>Co to jest usługa Microsoft Flow?
Microsoft Flow to usługa oparta na chmurze, która pozwala użytkownikom biznesowym w praktyczny i prosty sposób tworzyć przepływy pracy w celu automatyzacji czasochłonnych zadań i procesów obejmujących wiele aplikacji i usług.

### <a name="who-is-the-intended-audience-for-microsoft-flow"></a>Jaka jest grupa docelowa odbiorców usługi Microsoft Flow?
Microsoft Flow ma dwie odrębne grupy odbiorców:

* Biznesowi „integratorzy obywatelscy” w przedsiębiorstwach, którzy współpracują z informatykami, aby przenieść odpowiedzialność za rozwiązania biznesowe bliżej samego biznesu.
* Decydenci IT, którzy chcą wyposażyć partnerów biznesowych w możliwości tworzenia własnych rozwiązań, aby informatycy i specjaliści od integracji mogli skoncentrować swoją wiedzę na bardziej zaawansowanych narzędziach, takich jak usługa Azure Logic Apps.

### <a name="how-do-microsoft-flow-and-logic-apps-relate-to-each-other"></a>W jaki sposób usługi Microsoft Flow oraz Logic Apps są ze sobą powiązane?
Usługa Microsoft Flow zawiera funkcje, które ułatwiają użytkownikom biznesowym tworzenie automatycznych przepływów pracy. Logic Apps to usługa platformy Azure, która oferuje te same atrakcyjne funkcje, które są dostępne w usłudze Microsoft Flow, oraz dodatkowe funkcje, takie jak integracja z usługą Azure Resource Manager i witryną Azure Portal, program PowerShell i interfejs wiersza polecenia xPlat, program Visual Studio, a także dodatkowe łączniki. [Dowiedz się więcej o usłudze Logic Apps](https://azure.microsoft.com/services/app-service/logic/).

### <a name="how-does-microsoft-flow-fit-in-microsofts-overall-business-application-platform-strategy"></a>W jaki sposób usługa Microsoft Flow pasuje do ogólnej strategii platformy aplikacji biznesowych?
Usługa Microsoft Flow jest częścią potężnej i pozwalającej na dostosowanie platformy aplikacji biznesowych, która obejmuje usługi PowerApps, Common Data Service, Dynamics 365 i Office 365. Ta platforma pozwala naszym klientom, naszym partnerom i naszym partnerskim niezależnym dostawcom oprogramowania na tworzenie rozwiązań dostosowanych do potrzeb ich własnych firm, ich branży, ról funkcjonalnych, a nawet określonych lokalizacji geograficznych. Użytkownicy biznesowi, którzy najlepiej rozumieją potrzeby swoich firm, mogą teraz łatwo analizować, zestawiać i upraszczać dane oraz procesy. Profesjonalni deweloperzy mogą w prosty sposób rozszerzyć automatyzację, analizę i aplikacje w firmie, aby wykorzystywać usługi Azure takie jak Functions, App Service i Logic Apps. Łączniki interfejsu API, bramy i usługa Microsoft Common Data Service umożliwiają jeszcze lepsze wykorzystanie obecnie używanych usług lub danych, zarówno w chmurze, jak i lokalnie.

## <a name="functionality"></a>Funkcje
### <a name="what-do-i-need-to-use-microsoft-flow"></a>Co jest potrzebne do korzystania z usługi Microsoft Flow?
Do korzystania z usługi Microsoft Flow wystarcza przeglądarka internetowa i adres e-mail.

### <a name="what-browsers-does-microsoft-flow-support"></a>Jakie przeglądarki są obsługiwane przez usługę Microsoft Flow?
Usługa Microsoft Flow obsługuje przeglądarkę Microsoft Edge oraz aktualne wersje przeglądarek Chrome i Safari.

### <a name="which-email-addresses-are-supported"></a>Jakie adresy e-mail są obsługiwane?
Usługa Microsoft Flow obsługuje adresy e-mail z dowolną końcówką inną niż .gov i .mil.  

### <a name="is-microsoft-flow-available-on-premises"></a>Czy usługa Microsoft Flow jest dostępna lokalnie?
Microsoft Flow to usługa dostępna tylko w chmurze publicznej. Pozwala jednak bezpiecznie łączyć się z własnymi usługami lokalnymi za pośrednictwem lokalnej bramy danych.

### <a name="what-services-can-microsoft-flow-connect-to"></a>Z jakimi usługami można połączyć usługę Microsoft Flow?
Usługa Microsoft Flow ma wbudowane możliwości łączenia się z ponad 100 źródłami danych, a ich liczba stale wzrasta. Niektóre przykłady źródeł danych i usług:

* SharePoint
* Dynamics 365
* OneDrive
* OneDrive dla Firm
* Dysk Google
* Arkusze Google
* Trello
* Twitter
* Box
* Facebook
* SalesForce.com
* Mailchimp
* Interfejsy API klienta

Pełną listę dostępnych łączników można znaleźć [tutaj](https://go.microsoft.com/fwlink/?LinkId=832211).

Dostęp do źródeł danych we własnej infrastrukturze informatycznej można uzyskiwać za pośrednictwem [lokalnej bramy danych](gateway-manage.md).

### <a name="what-are-templates"></a>Co to są szablony?
Szablony to wstępnie utworzone przepływy dla popularnych i typowych scenariuszy. Użycie szablonu wymaga jedynie dostępu do usług zawartych w szablonie i podania wymaganych ustawień.

### <a name="what-data-sources-will-i-be-able-to-connect-to"></a>Z jakimi źródłami danych można się łączyć?
Można nawiązać połączenia z ponad 100 standardowymi usługami firmy Microsoft i innych firm, takimi jak Office 365, Twitter, SharePoint, OneDrive, Dropbox, SQL Server itp. Można także nawiązywać połączenie z usługami w warstwie Premium, takimi jak Salesforce i usługa Common Data Service dla aplikacji PowerApps.

### <a name="how-do-i-connect-to-a-rest-api-in-my-flow"></a>Jak połączyć interfejs API REST z moim przepływem?
Aby nawiązać połączenie z dowolnym interfejsem API REST, który używa formatu JSON i obsługuje co najmniej jedną z ponad 10 metod uwierzytelniania, możesz utworzyć [łącznik niestandardowy](register-custom-api.md).

### <a name="how-do-i-connect-to-sql-server-and-other-on-premises-data-sources"></a>Jak połączyć się z programem SQL Server i innymi lokalnymi źródłami danych?
Z usługami w sieci lokalnej można połączyć się przy użyciu [lokalnej bramy danych](gateway-manage.md).

### <a name="can-i-share-the-flows-i-create"></a>Czy mogę udostępniać tworzone przeze mnie przepływy?
Przepływy można udostępniać na jeden z następujących sposobów:

* Można dodawać współpracowników lub grupy ze swojej organizacji jako właścicieli w przepływach, aby też mogli edytować te przepływy i nimi zarządzać.
* W przypadku przepływów, które da się uruchamiać ręcznie, można też przyznawać innym osobom i grupom w organizacji uprawnienie do uruchamiania przepływu.

### <a name="how-many-flows-can-i-have"></a>Ile mogę mieć przepływów?
Usługa Microsoft Flow początkowo obejmuje maksymalnie 50 przepływów. W razie potrzeby możesz zażądać ich więcej.

### <a name="where-do-i-get-started-with-microsoft-flow"></a>Jak rozpocząć pracę z usługą Microsoft Flow?
Rozpocznij od poniższych zasobów:

* [Blog](https://flow.microsoft.com)
* [Kanał YouTube](https://youtube.com/playlist?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF)
* [Temat](getting-started.md)
* [Społeczność](http://powerusers.microsoft.com)

### <a name="what-operating-systems-does-the-mobile-app-for-microsoft-flow-support"></a>Jakie systemy operacyjne obsługuje aplikacja mobilna dla usługi Microsoft Flow?
Aplikacja mobilna usługi Microsoft Flow jest dostępna dla systemów [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) i [Windows Phone](https://aka.ms/flowmobilewindows).

### <a name="what-regions-and-languages-does-microsoft-flow-support"></a>Jakie regiony i języki są obsługiwane przez usługę Microsoft Flow?
Usługa Microsoft Flow jest dostępna w 42 językach i w [sześciu regionach](regions-overview.md).

### <a name="how-does-microsoft-flow-compare-to-sharepoint-designer-2013"></a>Jak wypada usługa Microsoft Flow w porównaniu z programem SharePoint Designer 2013?
Microsoft Flow jest następcą programu SharePoint Designer i umożliwia obsługę wielu typowych scenariuszy biznesowych, takich jak zatwierdzenia, przegląd dokumentów i dołączanie/odłączanie użytkowników. W przyszłości będzie domyślnym narzędziem do tworzenia automatyzacji procesów biznesowych w programie SharePoint.

### <a name="how-does-microsoft-flow-ensure-that-corporate-data-isnt-accidentally-released-to-social-media-services"></a>Jak usługa Microsoft Flow zabezpiecza dane firmowe przed przypadkowym ujawnieniem w mediach społecznościowych?
Administratorzy mogą tworzyć [zasady ochrony przed utratą danych](prevent-data-loss.md), aby zapewnić możliwość korzystania w usłudze Microsoft Flow tylko z zatwierdzonych usług.

## <a name="licensing"></a>Licencjonowanie
### <a name="will-microsoft-flow-still-have-a-free-or-trial-option"></a>Czy usługa Microsoft Flow będzie nadal dostępna w wersji bezpłatnej lub próbnej?
Tak. Możesz skorzystać z bezpłatnej oferty z ograniczonymi prawami użytkownika lub zarejestrować się w celu skorzystania z 90-dniowej bezpłatnej wersji próbnej usługi Microsoft Flow. Subskrypcję możesz aktywować w dowolnym momencie podczas okresu próbnego.

### <a name="what-pricing-plans-do-you-offer"></a>Jakie są dostępne plany cenowe?
Usługa Microsoft Flow oferuje poziomy bezpłatne i płatne. [Dowiedz się więcej o cenach](billing-questions.md).

