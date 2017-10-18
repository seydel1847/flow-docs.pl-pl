---
title: Limity i konfiguracja | Microsoft Docs
description: Limity i konfiguracja
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
ms.date: 08/02/2017
ms.author: stepsic
ms.openlocfilehash: 27e12df6ae5754f921d37992fa6759d152fd1afc
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="limits-and-configuration-in-microsoft-flow"></a>Limity i konfiguracja w usłudze Microsoft Flow
Ten temat zawiera informacje o obecnych limitach i szczegóły konfiguracji dla przepływów.

## <a name="request-limits"></a>Limity żądań
Są to limity dotyczące pojedynczego żądania wychodzącego.

### <a name="timeout"></a>Limit czasu
| Nazwa | Limit |
| --- | --- |
| Limit czasu żądania |120 sekund |

### <a name="message-size"></a>Rozmiar komunikatu
| Nazwa | Limit | Uwagi |
| --- | --- | --- |
| Rozmiar komunikatu |100 MB |Nie wszystkie interfejsy API obsługują pełne 100 MB. |
| Limit oceniania wyrażeń |131 072 znaki |Wyrażenia `@concat()`, `@base64()` i typu `string` nie mogą przekroczyć tego limitu. |

### <a name="retry-policy"></a>Zasady ponawiania
| Nazwa | Limit |
| --- | --- |
| Ponowne próby |4 |

## <a name="run-duration-and-retention"></a>Czas trwania i przechowywanie przebiegu
Są to limity dotyczące pojedynczego przebiegu przepływu.

| Nazwa | Limit | Uwagi |
| --- | --- | --- |
| Czas trwania przebiegu |30 dni |Zawiera przepływy pracy z oczekującymi krokami, takimi jak zatwierdzenia. Limit czasu dla oczekujących kroków upłynie po 30 dniach. |
| Przechowywanie w magazynie |30 dni |Od czasu rozpoczęcia przebiegu. |
| Minimalny interwał cyklu |1 minuta | |
| Maksymalny interwał cyklu |500 dni | |

## <a name="looping-and-debatching-limits"></a>Limity pętli i dzielenia partii na elementy
Są to limity dotyczące pojedynczego przebiegu przepływu.

| Nazwa | Limit | Uwagi |
| --- | --- | --- |
| Elementy ForEach |5000 |Akcji filtrowania możesz używać do filtrowania większych tablic zgodnie z potrzebami. |
| Iteracje Until |5000 | |
| Elementy SplitOn |5000 | |
| Równoległość ForEach |1 | |

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

### <a name="logic-app-service"></a>Usługa Logic Apps
Wywołania z przepływu przechodzą bezpośrednio przez usługę Azure Logic Apps. Przykłady takich wywołań to wywołania HTTP lub HTTP + OpenAPI. Pochodzą one z następujących adresów IP:

| Region | Wychodzący adres IP |
| --- | --- |
| Azja |168.63.200.173, 13.75.89.159, 23.97.68.172, 13.75.94.173, 40.83.127.19, 52.175.33.254, 52.163.93.214, 52.187.65.81, 52.187.65.155, 13.76.133.155, 52.163.228.93, 52.163.230.166 |
| Australia |13.75.153.66, 104.210.89.222, 104.210.89.244, 13.75.149.4, 104.210.91.55, 104.210.90.241, 13.73.115.153, 40.115.78.70, 40.115.78.237, 13.73.114.207, 13.77.3.139, 13.70.159.205 |
| Kanada |52.233.29.92, 52.228.39.241, 52.228.39.244, 52.232.128.155, 52.229.120.45, 52.229.126.25 |
| Europa |13.79.173.49, 52.169.218.253, 52.169.220.174, 40.113.12.95, 52.178.165.215, 52.178.166.21, 13.95.155.53, 52.174.54.218, 52.174.49.6, 40.68.222.65, 40.68.209.23, 13.95.147.65 |
| Indie |52.172.157.194, 52.172.184.192, 52.172.191.194, 52.172.154.168, 52.172.186.159, 52.172.185.79, 52.172.9.47, 52.172.49.43, 52.172.51.140, 52.172.50.24, 52.172.55.231, 52.172.52.0 |
| Japonia |13.71.146.140, 13.78.84.187, 13.78.62.130, 13.71.158.3, 13.73.4.207, 13.71.158.120, 40.74.140.173, 40.74.81.13, 40.74.85.215, 40.74.140.4, 104.214.137.243, 138.91.26.45 |
| Stany Zjednoczone |137.135.106.54, 40.117.99.79, 40.117.100.228, 13.92.98.111, 40.121.91.41, 40.114.82.191, 52.160.90.237, 138.91.188.137, 13.91.252.184, 52.160.92.112, 40.118.244.241, 40.118.241.243 |

### <a name="services"></a>Usługi
Wywołania wykonywane z interfejsu API połączonego za pośrednictwem przepływu (takiego jak np. interfejs API SQL czy interfejs API programu SharePoint) będą pochodzić z poniższego adresu IP:

| Region | Wychodzący adres IP |
| --- | --- |
| Azja |52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124 |
| Australia |13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35 |
| Kanada |52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56 |
| Europa |52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254 |
| Indie |52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245 |
| Japonia |104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229 |
| Stany Zjednoczone |104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191 |
| Stany Zjednoczone (wczesny dostęp) |52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29 |

Na przykład jeśli trzeba umieścić adresy IP na liście dozwolonych adresów dla bazy danych usługi Azure SQL, należy użyć tych adresów.

