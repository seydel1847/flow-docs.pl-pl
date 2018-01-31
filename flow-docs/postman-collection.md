---
title: "Opisywanie łącznika niestandardowego za pomocą narzędzia Postman | Microsoft Docs"
description: "Tworzenie kolekcji Postman Collection na potrzeby rejestracji łączników niestandardowych"
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/28/2017
ms.author: sunayv
ms.openlocfilehash: fe98999ea307367c7f3b032974fef9be6ca3f388
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2018
---
# <a name="describe-a-custom-connector-with-postman"></a>Opisywanie łącznika niestandardowego za pomocą narzędzia Postman
Narzędzie [Postman](https://www.getpostman.com/) umożliwia przyspieszenie i ułatwienie opracowywania interfejsów API. Ten samouczek pokazuje, jak utworzyć kolekcję Postman Collection, której można następnie użyć do łatwego utworzenia [łączników niestandardowych](register-custom-api.md) w usłudze Microsoft Flow.

## <a name="prerequisites"></a>Wymagania wstępne
* Zainstaluj [aplikację Postman](https://www.getpostman.com/apps).

## <a name="create-a-postman-collection"></a>Tworzenie kolekcji Postman Collection
Utwórzmy kolekcję Postman Collection na potrzeby [interfejsu API analizy tekstu](https://www.microsoft.com/cognitive-services/text-analytics-api) usługi Azure Cognitive Services. Ten interfejs API umożliwia identyfikowanie języka, opinii i kluczowych fraz w przekazanym do niego tekście.

1. Pierwszy krok tworzenia kolekcji Postman Collection to utworzenie żądania. Podczas tworzenia żądania można ustawić czasownik HTTP, adres URL żądania, parametry zapytania lub ścieżki, nagłówki i treść. Aby uzyskać więcej informacji, zobacz [Sending Requests](https://www.getpostman.com/docs/requests) (Wysyłanie żądań) w dokumentacji narzędzia Postman. Dla punktu końcowego interfejsu API wykrywania języka ustaw następujące wartości:
   
    ![Żądanie narzędzia Postman](./media/postman-collection/request.png)
   
    Szczegóły użytych parametrów i wartości:
   
   | Parametr | Wartość |
   | --- | --- |
   | Czasownik |POST |
   | Adres URL żądania |https://westus.api.cognitive.microsoft.com/text/analytics/v2.0/languages |
   | Parametry |numberOfLanguagesToDetect |
   | Uwierzytelnianie |“No Auth” |
   | Nagłówki |Ocp-Apim-Subscription-Key = <your subscription key> <br/>Content-Type = application/json |
   | Treść |<code>{<br/>&nbsp;&nbsp;&nbsp;"documents": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": "1",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Hello World"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}<code> |
2. Kliknij pozycję **Wyślij**, aby wysłać żądanie i otrzymać odpowiedź zwrotną.
3. Kliknij pozycję **Zapisz**, aby zapisać żądanie w kolekcji Postman Collection.
   
    ![Odpowiedź narzędzia Postman](./media/postman-collection/request-response-save.png)
4. Podaj wartości **Nazwa żądania** i **Opis żądania** w oknie dialogowym **Zapisywanie żądania**. Użyjesz tych wartości w Twoim łączniku niestandardowym.
   
    ![Zapisanie kolekcji w narzędziu Postman](./media/postman-collection/save-request-note.png)
   
    Możesz także zapisać odpowiedź na żądanie. Łączniki niestandardowe aktualnie obsługują tylko jedną odpowiedź dla żądania. Jeśli zapiszesz wiele odpowiedzi dla żądania, tylko pierwsza z nich zostanie użyta.
   
    ![Zapisanie odpowiedzi w narzędziu Postman](./media/postman-collection/save-response.png)
5. Kontynuuj tworzenie kolekcji Postman Collection, tworząc i zapisując inne żądania i odpowiedzi.
6. Po zakończeniu tworzenia kolekcji Postman Collection dla wszystkich żądań i odpowiedzi wyeksportuj kolekcję.
   
    ![Eksportowanie w narzędziu Postman](./media/postman-collection/export.png)
7. Wybierz format eksportu **Plik Collection wersja 1**.
   
    ![Eksportowanie w narzędziu Postman](./media/postman-collection/export2.png)

Teraz możesz użyć kolekcji narzędzia Postman do utworzenia łącznika niestandardowego w usłudze Microsoft Flow.

> [!IMPORTANT]
> Podczas tworzenia niestandardowego łącznika z kolekcji Postman pamiętaj o usunięciu nagłówka `Content-type` z akcji i wyzwalaczy, ponieważ zostanie on automatycznie dodany przez usługę Microsoft Flow. Nagłówki uwierzytelniania (np. `Ocp-Apim-Subscription-Key`) powinny zostać zdefiniowane w sekcji **Zabezpieczenia** i muszą zostać usunięte z akcji i wyzwalaczy. 
> 
> 

Aby uzyskać więcej informacji, zobacz [Register and use custom connectors in Microsoft Flow](register-custom-api.md) (Rejestrowanie i używanie łączników niestandardowych w usłudze Microsoft Flow).

