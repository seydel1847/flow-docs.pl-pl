---
title: "Opracowywanie łącznika interfejsu API | Microsoft Docs"
description: "Opisz swój interfejs API, określ typ uwierzytelniania, utwórz wyzwalacze i akcje oraz wykonaj test."
services: 
suite: flow
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 8731e8a90a62bac4a05068386d23d2449952860b
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2018
---
# <a name="develop-an-api-connector-microsoft-flow"></a>Opracowywanie łącznika interfejsu API (Microsoft Flow)
Tworzenie łącznika obejmuje wiele kroków. Aby rozpocząć pracę, w usłudze [Microsoft Flow](https://flow.microsoft.com/) kliknij lub naciśnij przycisk **Ustawienia** (ikonę koła zębatego) w prawym górnym rogu strony. Następnie kliknij lub naciśnij pozycję **Łączniki niestandardowe**.

![Znajdowanie łączników interfejsu API](./media/api-connectors-dev/finding-custom-apis.png)

## <a name="describe-your-api"></a>Opisywanie interfejsu API
Łączniki interfejsu API opisuje się za pomocą [standardu OpenAPI](https://swagger.io/) służącego do definiowania interfejsu API protokołu HTTP. Tworzenie można rozpocząć od istniejącego pliku OpenAPI lub zaimportowania kolekcji [Postman Collection](https://www.getpostman.com/docs/collections), co spowoduje automatyczne wygenerowanie pliku OpenAPI. 

![Definiowanie diagramu interfejsu API](./media/api-connectors-dev/build-your-api-updated.png)

Jeśli rozpoczynasz od jednego z tych opisów interfejsu API, pola metadanych w kreatorze będą wypełnione automatycznie. Możesz je zmodyfikować w dowolnym momencie.  

## <a name="build-security"></a>Tworzenie zabezpieczeń
Wybierz typ uwierzytelniania obsługiwany przez Twoją usługę, a następnie podaj dodatkowe szczegóły, aby umożliwić tożsamości odpowiedni przepływ między usługą i wszelkimi klientami. 

![Diagram zabezpieczeń](./media/api-connectors-dev/security.png)

[Dowiedz się więcej](register-custom-api.md) o zabezpieczeniach łącznika.

## <a name="build-triggers-and-actions"></a>Tworzenie wyzwalaczy i akcji
1. Aby utworzyć wyzwalacze i akcje dla łącznika, przejdź na kartę **Definicja**. 
   
    ![Diagram definicji](./media/api-connectors-dev/definition.png)
2. Korzystając z kreatora, możesz dodać nowe operacje lub zmodyfikować schemat i odpowiedzi dla istniejących operacji. **Ogólne** właściwości dla każdej operacji umożliwiają kontrolowanie środowiska użytkownika końcowego dla łącznika. Dowiedz się więcej o różnych typach operacji, korzystając z linków poniżej:
   
   * [Wyzwalacze](customapi-webhooks.md) (nie jest widoczny w usłudze PowerApps)
   * [Akcje](register-custom-api.md)
     
     Aby zaimplementować zaawansowane funkcje usługi Microsoft Flow, zapoznaj się z [rozszerzeniami OpenAPI dla łączników interfejsu API](https://flow.microsoft.com/documentation/customapi-how-to-swagger/). 
3. Na koniec kliknij lub naciśnij polecenie **Utwórz łącznik**, aby zarejestrować łącznik interfejsu API.

W sprawie dodatkowych funkcji niedostępnych w kreatorze skontaktuj się z nami pod adresem [condevhelp@microsoft.com ](mailto:condevhelp@microsoft.com).

## <a name="test-the-connector"></a>Testowanie łącznika
Przed przesłaniem należy przetestować łącznik interfejsu API w co najmniej jeden sposób: 

* Za pomocą [kreatora testowania](https://flow.microsoft.com/blog/new-updates-custom-api/) łącznika interfejsu API możesz wywołać każdą operację, aby zweryfikować jej funkcjonalność i schemat odpowiedzi.
* W projektancie usługi Microsoft Flow możesz graficznie utworzyć przepływy, używając łącznika interfejsu API. Ta metoda testowania daje wgląd w funkcjonalność interfejsu użytkownika i funkcje łącznika.
* W programie PowerApps Studio możesz wywołać każdą operację przy użyciu paska formuły i powiązać odpowiedź z kontrolkami na ekranie.

Ten temat zawiera omówienie. Aby uzyskać więcej informacji, zobacz [Register and use a custom connector](register-custom-api.md) (Rejestrowanie i używanie łącznika niestandardowego).

