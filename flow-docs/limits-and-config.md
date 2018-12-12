---
title: Limity i konfiguracja | Microsoft Docs
description: Limity i konfiguracja
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/04/2018
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 8a8a6561840f91ab61b8d7440f1620c2e7cd0076
ms.sourcegitcommit: a505b0aac796960d57fccee92eb18c6566ac9c35
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2018
ms.locfileid: "53006960"
---
# <a name="limits-and-configuration-in-microsoft-flow"></a>Limity i konfiguracja w usłudze Microsoft Flow
Ten temat zawiera informacje o obecnych limitach i szczegóły konfiguracji dla przepływów.

## <a name="request-limits"></a>Limity żądań
Są to limity dotyczące pojedynczego żądania wychodzącego.

### <a name="timeout"></a>Limit czasu

| Nazwa | Limit |
| --- | --- |
| Limit czasu żądania dla wywołań synchronicznych |120 sekund |
| Limit czasu żądania dla wywołań asynchronicznych|Można skonfigurować. Maksymalna wartość to 30 dni. |

### <a name="message-size"></a>Rozmiar komunikatu

| Nazwa | Limit | Uwagi |
| --- | --- | --- |
| Rozmiar komunikatu |100 MB |Nie wszystkie interfejsy API obsługują pełne 100 MB. |
| Limit oceniania wyrażeń |131 072 znaki |Wyrażenia `@concat()`, `@base64()` i typu `string` nie mogą przekroczyć tego limitu. |

### <a name="retry-policy"></a>Zasady ponawiania

| Nazwa | Limit |
| --- | --- |
| Ponowne próby |90 | Wartość domyślna to 4. Aby zmienić wartość domyślną, użyj ustawień akcji | 
| Maksymalna opóźnienie ponowienia próby |1 dzień | |
| Minimalne opóźnienie ponowienia próby |5 sekund | |

## <a name="run-duration-and-retention"></a>Czas trwania i przechowywanie przebiegu
Są to limity dotyczące pojedynczego przebiegu przepływu.

| Nazwa | Limit | Uwagi |
| --- | --- | --- |
| Czas trwania przebiegu |30 dni |Zawiera przepływy pracy z oczekującymi krokami, takimi jak zatwierdzenia. Limit czasu dla oczekujących kroków upłynie po 30 dniach. Zatwierdzenia, dla których upłynął limit czasu, zostaną usunięte z centrum zatwierdzeń. Próba zatwierdzenia żądania, dla którego upłynął limit czasu, spowoduje wyświetlenie komunikatu o błędzie. |
| Przechowywanie w magazynie |30 dni |Od czasu rozpoczęcia przebiegu. |
| Minimalny interwał cyklu |1 minuta | |
| Maksymalny interwał cyklu |500 dni | |
| Maksymalny okres przechowywania historii uruchamiania |28 dni zgodnie z wymogami RODO. | |

## <a name="looping-and-debatching-limits"></a>Limity pętli i dzielenia partii na elementy
Są to limity dotyczące pojedynczego przebiegu przepływu.

| Nazwa | Limit | Uwagi |
| --- | --- | --- |
| Elementy akcji Zastosuj do każdego |100 000 |Wartość 100 000 jest dostępna tylko w przypadku planów w warstwie premium. W przeciwnym razie ograniczenie wynosi 5000. Akcji filtrowania możesz używać do filtrowania większych tablic zgodnie z potrzebami. |
| Iteracje Until |5000 | |
| Elementy SplitOn |100 000 |Podobnie jak w przypadku akcji Zastosuj do każdego, limit wynosi 5000, o ile nie masz planu w warstwie premium. |
| Równoległość akcji Zastosuj do każdego |50 |Domyślnie pętle są uruchamiane kolejno (istotnie równoległość wynosi 1). Można skonfigurować maksymalnie 50 równoległych. |
| Wykonania akcji na 5 minut | 100 000 | Ponadto można rozłożyć obciążenie na więcej niż jeden przepływ, zgodnie z potrzebami. |
| Połączenia wychodzące jednoczesnych akcji | ~2500 | Zmniejsz liczbę jednoczesnych żądań lub skróć czas trwania, zgodnie z potrzebami. | 

## <a name="definition-limits"></a>Limity definicji
Są to limity dotyczące pojedynczego przepływu.

| Nazwa | Limit | Uwagi |
| --- | --- | --- |
| Akcje na przepływ pracy |250 |Aby zwiększyć tę liczbę, możesz dodać zagnieżdżone przepływy pracy zgodnie z potrzebami. |
| Dozwolona głębokość zagnieżdżenia akcji |5 |Aby zwiększyć tę liczbę, możesz dodać zagnieżdżone przepływy pracy zgodnie z potrzebami. |
| Maksymalna liczba znaków w wyrażeniu |8192 | |
| Limit nazw elementów `action`/`trigger` |80 | |
| Limit długości elementów `description` |256 | |

## <a name="sharepoint-limits"></a>Limity programu SharePoint
Istnieją [ograniczenia](https://powerapps.microsoft.com/tutorials/connection-sharepoint-online/) dotyczące używania programu Microsoft SharePoint z usługami Microsoft Flow i PowerApps.

## <a name="ip-address-configuration"></a>Konfiguracja adresu IP
Adres IP, spod którego są wysyłane żądania usługi Microsoft Flow, zależy od [regionu](regions-overview.md), w którym zlokalizowane jest [środowisko](environments-overview-admin.md) zawierające przepływ. Obecnie nie publikujemy nazw FQDN dostępnych dla scenariuszy przepływów.

### <a name="logic-apps"></a>Aplikacje logiki
Wywołania z przepływu przechodzą bezpośrednio przez usługę Azure Logic Apps. Przykłady takich wywołań to wywołania HTTP lub HTTP + OpenAPI. Adresy IP używane przez tę usługę można znaleźć w [dokumentacji usługi Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-limits-and-config#configuration-ip-addresses).

### <a name="connectors"></a>Łączniki
Wywołania z łącznika w przepływie (np. dotyczące interfejsu API SQL lub interfejsu API programu SharePoint) będą pochodzić z adresów IP wymienionych poniżej:

| Region | Wychodzący adres IP |
| --- | --- |
| Azja i Pacyfik | 13.75.36.64–13.75.36.79, 13.67.8.240–13.67.8.255, 52.175.23.169, 52.187.68.19, 52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 52.187.53.78, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124, 23.97.72.250  |
| Australia  | 13.70.72.192–13.70.72.207, 13.72.243.10, 13.77.50.240–13.77.50.255, 13.70.136.174, 13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.188.38, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35, 13.70.88.23 |
| Kanada | 13.71.170.208–13.71.170.223, 13.71.170.224–13.71.170.239, 52.237.24.126, 40.69.106.240–40.69.106.255, 52.242.35.152, 52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56, 52.229.123.161, 52.233.27.68 |
| Europa | 13.69.227.208–13.69.227.223, 52.178.150.68, 13.69.64.208–13.69.64.223, 52.174.88.118, 52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 52.178.37.42, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254, 52.164.249.26, 137.117.161.181 |
| Indie  | 104.211.81.192–104.211.81.207, 52.172.211.12, 40.78.194.240–40.78.194.255, 13.71.125.22, 104.211.146.224–104.211.146.239, 104.211.189.218, 52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.49.180, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245, 52.172.153.107 |
| Japonia | 13.78.108.0–13.78.108.15, 13.71.153.19, 40.74.100.224–40.74.100.239, 104.215.61.248, 104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 104.214.151.229, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229, 13.78.121.151 |
| Ameryka Południowa | 191.233.203.192–191.233.203.207, 104.214.19.48–104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Zjednoczone Królestwo | 51.140.148.0–51.140.148.15, 51.140.80.51, 51.140.211.0–51.140.211.15, 51.141.47.105 |
| Stany Zjednoczone | 13.89.171.80 – 13.89.171.95, 52.173.245.164, 40.71.11.80 – 40.71.11.95, 40.71.249.205, 40.70.146.208 – 40.70.146.223, 52.232.188.154, 52.162.107.160 – 52.162.107.175, 52.162.242.161, 40.112.243.160 – 40.112.243.175, 104.42.122.49, 104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191 |
| Wersja zapoznawcza (Stany Zjednoczone)  | 13.71.195.32–13.71.195.47, 52.161.102.22, 13.66.140.128–13.66.140.143, 52.183.78.157, 52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 52.161.31.35, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29, 13.66.208.24 |

Na przykład jeśli trzeba autoryzować adresy IP dla bazy danych usługi Azure SQL, należy użyć tych adresów.

### <a name="required-services"></a>Wymagane usługi
W poniższej tabeli są wymienione usługi, z którymi łączy się usługa Microsoft Flow. Upewnij się, że żadna z tych usług nie jest blokowana w Twojej sieci.

Domeny | Protokoły | Użycie
--------|  ---------| -----
management.azure.com|https|Dostęp do usługi Azure Resource Manager.
login.microsoft.com</br>login.windows.net</br>login.microsoftonline.com</br>secure.aadcdn.microsoftonline-p.com|https|Dostęp do biblioteki ADAL (Active Directory Authentication Library).
graph.microsoft.com </br>graph.windows.net</br>|https|Dostęp do interfejsu API usługi Azure AD Graph — w celu uzyskiwania informacji o użytkowniku, takich jak zdjęcie w profilu.
*.azure-apim.net|https|Dostęp do środowiska uruchomieniowego dla łączników.
*.flow.microsoft.com|https|Dostęp do witryny usługi Microsoft Flow.
*.powerapps.com|https|Dostęp do witryny aplikacji PowerApps.
*.azureedge.net|https|Dostęp do sieci CDN usługi Microsoft Flow.
nps.onyx.azure.net|https|Dostęp do wyniku NPS (Net Promoter Score).
