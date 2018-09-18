---
title: Integrowanie usługi Microsoft Flow z aplikacjami i witrynami internetowymi | Microsoft Docs
description: Osadź środowiska usługi Microsoft Flow w witrynie sieci Web lub aplikacji.
services: ''
suite: flow
documentationcenter: na
author: bbarath
manager: erikre
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/09/2017
ms.author: barathb
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: aa5e0a7d143e0e1486533131f90d6b04c6fbc20c
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690019"
---
# <a name="integrate-microsoft-flow-with-websites-and-apps"></a>Integrowanie usługi Microsoft Flow z witrynami sieci Web i aplikacjami
Osadź usługę Microsoft Flow bezpośrednio w aplikacji lub witrynie sieci Web w celu udostępnienia użytkownikom łatwego sposobu automatyzacji zadań osobistych lub zawodowych.

Aby tworzyć przepływy, użytkownicy potrzebują **konta Microsoft** albo konta służbowego w usłudze **Azure Active Directory**. Usługa Microsoft Flow nie obsługuje, na przykład, rozwiązania sprzedawanego pod marką dystrybutora, które obsługuje dowolną tożsamość używaną przez system (chyba że używa już kont Microsoft lub usługi AAD).

## <a name="prerequisites"></a>Wymagania wstępne
* [Utwórz łącznik niestandardowy](register-custom-api.md) łączący Twoją usługę z usługą Microsoft Flow.
* [Utwórz i opublikuj co najmniej jeden szablon](../publish-a-template.md) korzystający z utworzonego interfejsu API.

## <a name="show-templates-for-your-scenarios"></a>Wyświetlanie szablonów dla Twoich scenariuszy
Aby rozpocząć, dodaj następujący kod w celu wyświetlenia szablonów przepływu bezpośrednio w swojej witrynie sieci Web:

```html
<iframe src="https://flow.microsoft.com/{locale}/widgets/templates/?q={search term}
&pagesize={number of templates}&destination={destination}"></iframe>
```

**Uwaga**: dodaliśmy podział wiersza, aby kod był lepiej wyświetlany na stronie.

| Parametr | Opis |
| --- | --- |
| locale |Czteroliterowy kod języka i regionu dla widoku szablonu. Na przykład `en-us` reprezentuje język angielski (USA), a `de-de` — niemiecki. |
| search term |Wyszukiwany termin dla szablonów, które mają być wyświetlane w widoku. Na przykład wyszukaj ciąg `wunderlist`, aby wyświetlić szablony dla aplikacji Wunderlist. |
| number of templates |Liczba szablonów, które mają być wyświetlane w widoku. |
| destination |Strona otwierana, gdy użytkownik kliknie szablon. Podaj wartość `details`, aby wyświetlić szczegółowe informacje o szablonie, lub `new`, aby otworzyć projektanta usługi Microsoft Flow. |
| parameters.{nazwa} |Dodatkowy kontekst, który ma być przekazywany do przepływu. |

Jeśli parametr destination ma wartość `new`, usługa Microsoft Flow zostanie otwarta, gdy użytkownik kliknie szablon, po czym umożliwi ona utworzenie przepływu w projektancie. Zobacz następną sekcję, jeśli chcesz mieć dostęp do pełnego środowiska pracy z poziomu aplikacji.

### <a name="passing-additional-parameters-to-the-flow"></a>Przekazywanie dodatkowych parametrów do przepływu
Jeśli użytkownik znajduje się w pewnym kontekście witryny sieci Web lub aplikacji, możesz przekazać ten kontekst do przepływu. Na przykład użytkownik może otworzyć szablon pozycji *Powiadamiaj mnie, gdy element zostanie dodany do listy* podczas przeglądania określonej listy w aplikacji Wunderlist. Wykonując poniższe kroki, możesz wprowadzić do przepływu identyfikator listy jako *parametr*:

1. Zdefiniuj parametr w szablonie przepływu przed jego opublikowaniem. Parametr ma postać podobną do następującej: `@{parameters('parameter_name')}`.
2. Przekaż parametr w atrybucie iframe src. Na przykład dodaj ciąg `&parameters.listName={the name of the list}` w przypadku parametru o nazwie **listName**.

### <a name="full-sample"></a>Pełny przykład
Aby wyświetlić pierwsze cztery szablony dla aplikacji Wunderlist w języku niemieckim i po uruchomieniu wyświetlać użytkownikowi listę **myCoolList**:

```html
<iframe src="https://flow.microsoft.com/de-de/widgets/templates/?q=wunderlist
&pagesize=4&destination=details&parameters.listName=myCoolList"></iframe>
```

## <a name="embed-the-management-of-flows"></a>Osadzanie zarządzania przepływami
Użyj uwierzytelnionego zestawu SDK przepływu, aby umożliwić użytkownikom tworzenie przepływów oraz zarządzanie nimi bezpośrednio z witryny sieci Web lub aplikacji (zamiast przechodzenia do portalu usługi Microsoft Flow). Musisz zalogować użytkownika do konta Microsoft lub usługi Azure Active Directory, aby użyć uwierzytelnionego zestawu SDK.

> [!NOTE]
> Wszyscy użytkownicy korzystający z usługi Microsoft Flow w Twojej aplikacji będą użytkownikami usługi Microsoft Flow. Nie ma możliwości ukrycia oznakowania usługi Microsoft Flow.
> 
> 

### <a name="include-the-javascript-for-the-authenticated-sdk"></a>Uwzględnianie języka JavaScript dla uwierzytelnionego zestawu SDK
Uwzględnij zestaw SDK w kodzie HTML, postępując zgodnie z tym przykładem. Możesz też pobrać i zmniejszyć zestaw SDK oraz utworzyć jego pakiet za pomocą produktu.

```javascript
<script src="https://flow.microsoft.com/content/msflowsdk-1.1.js" async defer></script>
```

### <a name="create-a-container-to-contain-the-view"></a>Tworzenie kontenera zawierającego widok
Dodaj tag div języka HTML:

```html
<div id="flowDiv" class="flowContainer"></div>
```

Zalecamy dopasowanie stylu tego kontenera tak, aby miał on rozmiar odpowiedni dla używanego środowiska:

```html
<head>
    <style>
        .flowContainer iframe {
            width: 400px;
            height: 1000px;
            border: none;
            overflow: hidden;
    }
    </style>
</head>
```

Pamiętaj, że element iframe nie będzie poprawnie renderowany poniżej 320 pikseli szerokości i nie będzie wypełniony zawartością powyżej 1200 pikseli szerokości. Nie ma ograniczeń wysokości.

### <a name="authentication-against-the-sdk"></a>Uwierzytelnianie względem zestawu SDK
Aby wyświetlić listę przepływów, które użytkownik już utworzył, oraz aby utworzyć przepływy z szablonów, podaj element authToken z usługi AAD.

```javascript
<script>
    window.msFlowSdkLoaded = function() {
        var sdk = new MsFlowSdk({
            hostName:'https:/flow.microsoft.com'
        });
        var widget = sdk.renderWidget('flows', {
            container: 'flowDiv'
            environmentId: '[environmentId]'    // find environment id from browser URL when you 
                                                // click on 'my flows'
                                                //ex: https://flow.microsoft.com/manage/environments/[environmentId]/flows
        });
        widget.callbacks.GET_ACCESS_TOKEN = function(requestParam, widgetDoneCallback)
       {
            var authCallback = function(token) {
                widgetDoneCallback(null, {
                    token: token // Get AAD access token from your backend system
                });
            };
        }
    }
</script>
```

Element `environmentId` możesz znaleźć, wykonując następujące wywołanie interfejsu API, które zwraca listę środowisk dostępnych dla użytkownika:

```http
GET https://management.azure.com/providers/Microsoft.ProcessSimple/environments
?api-version=2016-11-01 
```

Zwraca odpowiedź JSON z listą środowisk, z której można wybrać dowolne środowisko. Możesz wyszukać domyślne środowisko użytkownika, zaznaczając właściwość `properties.isDefault=true`.

W tym przykładzie element `requestParam` jest zdefiniowany jako:

```javascript
export interface IRpcRequestParam {
    callInfo: IRpcCallInfo,
    data?: any;
}
```

Z kolei element `widgetDoneCallback` to funkcja wywołania zwrotnego, którą należy wywołać, gdy host ma już token. Przyczyną jest to, że uzyskanie tokenu jest prawdopodobnie procesem asynchronicznym. Parametry, które należy przekazać przy wywołaniu tej funkcji, to `(errorResult: any, successResult: any)`. Wartość successResult zależy od typu wywołania zwrotnego. Dla elementu `GetAccessToken` typ to:

```javascript
export interface IGetAccessTokenResult {
    token: string;
}
```
