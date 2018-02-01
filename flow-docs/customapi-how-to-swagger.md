---
title: "Rozszerzenia OpenAPI dla łączników niestandardowych usługi Microsoft Flow| Microsoft Docs"
description: "Wyświetl rozszerzenia schematu wymagane przez standard OpenAPI do współpracy z usługą Microsoft Flow"
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: sunaysv
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/19/2017
ms.author: sunayv
ms.openlocfilehash: b8fdc04c16701c876d84e9761a48093fa5fb195c
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2018
---
# <a name="openapi-extensions-for-custom-connectors-in-microsoft-flow"></a>Rozszerzenia OpenAPI dla łączników niestandardowych usługi Microsoft Flow
## <a name="introduction"></a>Wprowadzenie
Aby tworzyć niestandardowe łączniki dla usług Microsoft Flow, Azure Logic Apps i Microsoft PowerApps, należy dostarczyć plik definicji OpenAPI, czyli niezależny od języka, czytelny dla komputerów dokument opisujący operacje i parametry interfejsu API. Przy okazji tworzenia niestandardowych łączników dla usług Logic Apps i Flow obok gotowej funkcjonalności OpenAPI możesz także skorzystać z następujących rozszerzeń OpenAPI:

* `summary`
* `x-ms-summary`
* `description`
* `x-ms-visibility`
* `x-ms-dynamic-values`
* `x-ms-dynamic-schema`

Oto więcej informacji na temat tych rozszerzeń:

<a name="summary"></a>

## <a name="summary"></a>summary
Określa tytuł dla akcji (operacji). </br>
Dotyczy: operacji </br>
Zalecane: użyj *wielkości liter jak w zdaniu* dla rozszerzenia `summary`. </br>
Przykład: „Po dodaniu zdarzenia do kalendarza” lub „Wyślij wiadomość e-mail”

![dla rozszerzenia „summary” każdej operacji](./media/custom-connector-openapi-extensions/summary.png)

``` json
"actions" {
  "Send_an_email": {
    /// Other action properties here...
    "summary": "Send an email",
    /// Other action properties here...
  }
},
```

## <a name="x-ms-summary"></a>x-ms-summary
Określa tytuł dla jednostki. </br>
Dotyczy: parametrów, schematu odpowiedzi </br>
Zalecane: użyj *wielkości liter jak z nazwach własnych* dla rozszerzenia `x-ms-summary`. </br>
Przykład: „Identyfikator Kalendarza”, „Temat”, „Opis Zdarzenia” itd.

![dla rozszerzenia „x-ms-summary” każdej jednostki](./media/custom-connector-openapi-extensions/x-ms-summary.png)

``` json
"actions" {
  "Send_an_email": {
    /// Other action properties here...
    "parameters": [ 
      {
        /// Other parameters here...
        "x-ms-summary": "Subject",
        /// Other parameters here...
      }
    ]
  }
},
```
<a name="description"></a>

## <a name="description"></a>description
Określa pełne wyjaśnienie funkcjonalności operacji lub formatu i funkcji jednostki. </br>
Dotyczy: operacji, parametrów, schematu odpowiedzi </br>
Zalecane: użyj *wielkości liter jak w zdaniu* dla rozszerzenia `description`. </br>
Przykład: „Ta operacja jest wywoływana po dodaniu nowego zdarzenia do kalendarza”, „Podaj temat wiadomości e-mail” itd.

![dla rozszerzenia „description” każdej operacji lub jednostki](./media/custom-connector-openapi-extensions/description.png)

``` json
"actions" {
  "Send_an_email": {
     "description": "Specify the subject of the mail",
     /// Other action properties here...
  }
},
```

<a name="visibility"></a>

## <a name="x-ms-visibility"></a>x-ms-visibility
Określa widoczność względem użytkownika dla jednostki. </br>
Możliwe wartości: `important`, `advanced` i `internal` </br>
Dotyczy: operacji, parametrów, schematów

* Operacje i parametry `important` są zawsze pokazywane użytkownikowi jako pierwsze.
* Operacje i parametry `advanced` są ukryte w dodatkowym menu.
* Operacje i parametry `internal` są ukryte przed użytkownikiem.

> [!NOTE]
> W przypadku parametrów, które są `internal` i `required`, **musisz** podać domyślne wartości tych parametrów.
> 
> 

Przykład: menu **Zobacz więcej** i menu **Pokaż opcje zaawansowane** ukrywają operacje i parametry `advanced`.

![Rozszerzenie „x-ms-visibility” do pokazywania lub ukrywania operacji i parametrów](./media/custom-connector-openapi-extensions/x-ms-visibility.png)

``` json
"actions" {
  "Send_an_email": {
     /// Other action properties here...
     "parameters:": [
         {
           "name": "Subject",
           "type": "string",
           "description": "Specify the subject of the mail",
           "x-ms-summary": "Subject",
           "x-ms-visibility": "important",
           /// Other parameter properties here
         }
     ]
     /// Other action properties here...
  }
},
```

## <a name="x-ms-dynamic-values"></a>x-ms-dynamic-values
Pokazuje użytkownikowi wypełnioną listę, umożliwiając wybór parametrów wejściowych dla operacji. </br>
Dotyczy: parametrów </br>
Sposób użycia: dodaj obiekt `x-ms-dynamic-values` do definicji parametru. Aby zobaczyć przykład, wyświetl ten [przykładowy plik OpenAPI](https://procsi.blob.core.windows.net/blog-images/sampleDynamicSwagger.json).

![Rozszerzenie „x-ms-dynamic-values” do pokazywania list](./media/custom-connector-openapi-extensions/x-ms-dynamic-values.png)

### <a name="properties-for-x-ms-dynamic-values"></a>Właściwości dla rozszerzenia x-ms-dynamic-values
| Nazwa | Wymagane lub opcjonalne | Opis |
| --- | --- | --- |
| **operationID** |Wymagane |Operacja wywołująca wypełnienie listy. |
| **value-path** |Wymagane |Ciąg ścieżki w obiekcie wewnątrz elementu `value-collection` odwołujący się do wartości parametru. Jeśli element `value-collection` nie jest określony, odpowiedź jest obliczana jako tablica. |
| **value-title** |Opcjonalne |Ciąg ścieżki w obiekcie wewnątrz elementu `value-collection` odwołujący się do opisu parametru. Jeśli element `value-collection` nie jest określony, odpowiedź jest obliczana jako tablica. |
| **value-collection** |Opcjonalne |Ciąg ścieżki, który oblicza tablicę obiektów w ładunku odpowiedzi |
| **parameters** |Opcjonalne |Obiekt, którego właściwości określają parametry wejściowe wymagane do wywołania operacji rozszerzenia „dynamic-values” |

Oto przykład, w którym są wyświetlane właściwości w rozszerzeniu `x-ms-dynamic-values`:

``` json
"x-ms-dynamic-values": {
  "operationId": "PopulateDropdown",
  "value-path": "name",
  "value-title": "properties/displayName",
  "value-collection": "value",
  "parameters": {
     "staticParameter": "{value}",
     "dynamicParameter": {
        "parameter": "{value-to-pass-to-dynamicParameter}"
     }
  }
}
```

## <a name="example-all-the-openapi-extensions-up-to-this-point"></a>Przykład: wszystkie rozszerzenia OpenAPI do tej chwili
``` json
"/api/lists/{listID-dynamic}": {
    "get": {
        "description": "Get items from a single list - uses dynamic values and outputs dynamic schema",
        "summary": "Gets items from the selected list",
        "operationID": "GetListItems",
        "parameters": [
           {
             "name": "listID-dynamic",
             "type": "string",
             "in": "path",
             "description": "Select the list from where you want outputs",
             "required": true,
             "x-ms-summary": "Select List",
             "x-ms-dynamic-values": {
                "operationID": "GetLists",
                "value-path": "id",
                "value-title": "name"
             }
           }
        ]
    }
}
```

## <a name="x-ms-dynamic-schema"></a>x-ms-dynamic-schema
Wskazuje, że schemat dla bieżącego parametru lub odpowiedzi jest dynamiczny. Ten obiekt może wywołać operację zdefiniowaną przez wartość tego pola, dynamicznie odnaleźć schemat i wyświetlić odpowiedni interfejs użytkownika, aby pobrać dane wejściowe od użytkownika lub wyświetlić dostępne pola. 

Dotyczy: parametrów, odpowiedzi

Sposób użycia: dodaj obiekt `x-ms-dynamic-schema` do definicji treści odpowiedzi lub parametru żądania. Aby zobaczyć przykład, wyświetl ten [przykładowy plik OpenAPI](https://procsi.blob.core.windows.net/blog-images/sampleDynamicSwagger.json).

Ten przykład pokazuje, jak zmienia się formularz wejściowy w zależności od elementu wybieranego przez użytkownika z listy rozwijanej:

![Rozszerzenie „x-ms-dynamic-schema” dla parametrów dynamicznych](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema.png)

Zaś ten przykład pokazuje, jak zmieniają się dane wyjściowe w zależności od wybieranego przez użytkownika elementu z listy rozwijanej. W tej wersji użytkownik wybiera element „Cars”:

![Rozszerzenie „x-ms-dynamic-schema-response” dla wybranego elementu „Cars”](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema-output1.png)

W tej wersji użytkownik wybiera element „Food”:

![Rozszerzenie „x-ms-dynamic-schema-response” dla wybranego elementu „Food”](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema-output2.png)

### <a name="properties-for-x-ms-dynamic-schema"></a>Właściwości dla rozszerzenia x-ms-dynamic-schema
| Nazwa | Wymagane lub opcjonalne | Opis |
| --- | --- | --- |
| **operationID** |Wymagane |Operacja wywołująca pobieranie schematu |
| **parameters** |Wymagane |Obiekt, którego właściwości określają parametry wejściowe wymagane do wywołania operacji rozszerzenia „dynamic-schema” |
| **value-path** |Opcjonalne |Ciąg ścieżki odwołujący się do właściwości, w której jest przechowywany schemat. </br>Jeśli nie jest określony, przyjmuje się, że odpowiedź zawiera schemat we właściwościach obiektu głównego. |
|  | | |

Oto przykład parametru dynamicznego:

``` json
{
  "name": "dynamicListSchema",
  "in": "body",
  "description": "Dynamic schema for items in the selected list",
  "schema": {
    "type": "object",
    "x-ms-dynamic-schema": {
        "operationID": "GetListSchema",
        "parameters": {
          "listID": {
            "parameter": "listID-dynamic"
          }
        },
        "value-path": "items"
    }
  }
}
```

Oto przykład odpowiedzi dynamicznej:

``` json
"DynamicResponseGetListSchema": {
   "type": "object",
   "x-ms-dynamic-schema": {
      "operationID": "GetListSchema",
      "parameters": {
         "listID": {
            "parameter": "listID-dynamic"
         }
      },
      "value-path": "items"
    }
}
```

## <a name="next-steps"></a>Następne kroki
[Rejestrowanie łącznika niestandardowego](register-custom-api.md).

[Używanie interfejsu API sieci Web platformy ASP.NET](customapi-web-api-tutorial.md).

[Rejestrowanie interfejsu API usługi Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

