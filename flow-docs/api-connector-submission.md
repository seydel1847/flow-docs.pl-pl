---
title: "Przesyłanie do certyfikacji jako łącznika interfejsu API | Microsoft Docs"
description: "Po certyfikacji łącznik staje się dostępny dla wszystkich użytkowników usług Microsoft Flow, PowerApps i Logic Apps."
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
ms.date: 09/19/2017
ms.author: astay
ms.openlocfilehash: 7eb357458161ba398864604bfe8912636ddc4d39
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="submit-your-connectors-for-microsoft-certification"></a>Przesyłanie łączników do certyfikacji przez firmę Microsoft
Aby publicznie udostępnić niestandardowe łączniki wszystkim użytkownikom w usługach Microsoft Flow, Azure Logic Apps i Microsoft PowerApps, prześlij swój łącznik do firmy Microsoft w celu dokonania przeglądu, weryfikacji i zgody na opublikowanie. 

## <a name="certification-criteria"></a>Kryteria certyfikacji
| Możliwość | Szczegóły | Wymagane czy zalecane |
| --- | --- | --- |
| Aplikacja typu „oprogramowanie jako usługa” (SaaS, Software as a Service) |Jest zgodna ze scenariuszem użytkownika, który jest odpowiednio dopasowany do usług Logic Apps, Flow i PowerApps. |Wymagane |
| Typ uwierzytelniania |Interfejs API musi obsługiwać uwierzytelnianie OAuth2, klucz interfejsu API lub uwierzytelnianie podstawowe. |Wymagane |
| Pomoc techniczna |Musisz podać kontakt pomocy technicznej, do której klienci mogą zwrócić się o pomoc. |Wymagane |
| Dostępność i czas pracy |Aplikacja ma co najmniej 99,9% czasu pracy. |Zalecane |
|  | | |

Ponadto jeśli nie jesteś partnerem firmy Microsoft ani niezależnym dostawcą oprogramowania i chcesz uzyskać certyfikację łącznika i publicznie go wydać, musisz być właścicielem bazowej usługi lub przedstawić jawne prawa do użycia interfejsu API.

Aby uzyskać certyfikację, Twój łącznik zostanie oceniony w dwóch etapach: 

1. Sprawdzenie funkcjonalności
   
    Łącznik niestandardowy jest oceniany pod kątem:
   
   * Nieprawidłowej struktury Swagger lub błędów pliku JSON w sekcji Definicja w Kreatorze łącznika niestandardowego
   * Błędów środowiska wykonawczego i schematu sprawdzania poprawności w sekcji Testowanie w Kreatorze
     
     W rezultacie każda operacja jest dokładnie testowana w usłudze Flow, Logic Apps i PowerApps pod kątem wszelkich błędów po stronie klienta.
2. Sprawdzanie poprawności zawartości
   
    Dobrze napisany łącznik używa przyjaznych nazw i opisów dla każdej jednostki. Oceniamy strukturę Swagger, aby upewnić się, że każda operacja, parametr wejściowy i atrybut odpowiedzi zawiera:
   
   * [Podsumowanie](../logic-apps/custom-connector-openapi-extensions.md#summary)
   * [Opis](../logic-apps/custom-connector-openapi-extensions.md#description)
   * [Informację o widoczności](../logic-apps/custom-connector-openapi-extensions.md#visibility)

## <a name="nominate-and-submit-your-connector-to-microsoft-for-certification"></a>Nominowanie i przesyłanie łącznika do firmy Microsoft w celu certyfikacji
Aby ubiegać się o certyfikację, wykonaj następujące kroki:

1. **Nominacja**
   
   1. [Prześlij swoją nominację](https://go.microsoft.com/fwlink/?linkid=848754).
   2. Podpisz wzajemną umowę o poufności i umowę partnerską, które otrzymasz. 
      Firma Microsoft wymaga podpisania tych umów przed podjęciem działań. 
      Następnie możemy sprawdzić, czy Twój łącznik spełnia kryteria certyfikacji. 
   3. Jeśli Twój łącznik zostanie zatwierdzony, firma Microsoft przekaże Ci instrukcje dotyczące dołączania.
2. **Przegląd**
   
   1. Prześlij następujące informacje do osoby kontaktowej ds. nominacji w celu wykonania przeglądu:
      
      * Plik OpenAPI opisujący interfejs API
      * Plik ikony (png lub jpg) reprezentującej Twój łącznik. (Ikona powinna zawierać logo o rozmiarze ok. 160 pikseli wewnątrz kwadratu o rozmiarze 230 pikseli. Preferowane jest białe logo na kolorowym tle).
      * Kolor marki ikony w formacie szesnastkowym, który powinien być zgodny z kolorowym tłem w pliku ikony
      * Konto testowe na potrzeby walidacji
      * Kontakt z działem pomocy technicznej
   2. Jeśli będziemy potrzebować więcej informacji, skontaktujemy się z Tobą.
3. **Publikowanie**
   
    Po zweryfikowaniu funkcjonalności łącznika i jego zawartości wdrożymy przejściowo łącznik we wszystkich produktach i regionach. Zwykle proces przyznawania certyfikacji i wdrażania trwa do 3 tygodni.
   
    Domyślnie wszystkie łączniki są publikowane jako „premium”. 
    Jeśli Twoja aplikacja jest zbudowana za pomocą platformy Azure, możesz zgłosić swój łącznik do oznaczenia jako „standardowy”, dostępny dla wszystkich użytkowników planów usługi Office 365 Enterprise. 
    O więcej szczegółów zapytaj osobę kontaktową ds. nominacji.

