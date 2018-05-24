---
title: Grupy danych dla usługi Microsoft Flow | Microsoft Docs
description: Wprowadzenie do grup danych dla usług Microsoft PowerApps i Microsoft Flow.
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/26/2016
ms.author: deonhe
ms.openlocfilehash: fd76c12d1879c9b613ba833d9ef2211cd4aab702
ms.sourcegitcommit: f0202f74ba9a2282a670a1751462f598a5ea0ce5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="learn-all-about-data-groups"></a>Dowiedz się wszystkiego o grupach danych
## <a name="what-is-a-data-group"></a>Co to jest grupa danych?
Grupy danych stanowią prosty sposób kategoryzowania usług z użyciem [zasad ochrony przed utratą danych (DLP)](prevent-data-loss.md). Dostępne są dwie grupy danych: **Business data only** (Tylko dane biznesowe) i **No business data allowed** (Bez danych biznesowych). Organizacje mogą określić, które usługi mają zostać powiązane z poszczególnymi grupami danych. Dobrym sposobem na sklasyfikowanie usług jest umieszczenie ich w grupach w oparciu o ich wpływ na organizację. Domyślnie wszystkie usługi są umieszczane w grupie danych **No business data allowed** (Bez danych biznesowych). Zarządzanie usługami w grupie danych ma miejsce podczas tworzenia lub modyfikowania właściwości zasad DLP w Centrum administracyjnym.

## <a name="how-data-is-shared-between-data-groups"></a>Współdzielenie danych w obrębie grup danych
Dane nie mogą być współdzielone przez usługi należące do różnych grup. Na przykład jeśli umieścisz usługi SharePoint i Salesforce w grupie **Business data only** (Tylko dane biznesowe), a usługi Facebook i Twitter w grupie **No business data allowed** (Bez danych biznesowych), nie będzie można utworzyć przepływu, który przenosiłby dane między usługami SharePoint i Facebook. O ile współdzielenie danych między usługami należącymi do różnych grup nie jest możliwe, istnieje możliwość udostępniania danych między usługami w obrębie danej grupy. Wracając do poprzedniego przykładu, jako że usługi SharePoint i Salesforce zostały umieszczone w tej samej grupie danych, przepływy tworzone przez użytkowników końcowych mogą współdzielić dane między usługami Salesforce i SharePoint. Podobnie użytkownicy końcowi mogą tworzyć przepływy i aplikacje PowerApps, które współdzielą dane z usług Facebook i Twitter. Należy przede wszystkim pamiętać, że w danej grupie możliwe jest współdzielenie danych, natomiast usługi z różnych grup nie mogą współdzielić danych.  

Ponadto jedna grupa danych musi zostać oznaczona jako grupa *domyślna*. Początkowo grupa danych **No business data allowed** (Bez danych biznesowych) jest grupą *domyślną*, do której należą wszystkie usługi. Administrator może zmienić ustawienie domyślnej grupy danych na grupę **Business data only** (Tylko dane biznesowe). **Uwaga**: wszelkie nowe usługi dodane do przepływu zostaną umieszczone w wyznaczonej grupie *domyślnej*. W związku z tym firma Microsoft zaleca zachowanie grupy **No business data allowed** (Bez danych biznesowych) jako grupy domyślnej i ręczne dodawanie usług do grupy **Business data only** (Tylko dane biznesowe) po wcześniejszym przeprowadzeniu oceny wpływu współdzielenia danych biznesowych z nową usługą.

## <a name="add-services-to-a-data-group"></a>Dodawanie usług do grupy danych
W tym przewodniku dodamy usługi SharePoint i Salesforce do grupy danych **business data only** (tylko dane biznesowe) w zasadach ochrony przed utratą danych (DLP). 

1. Wybierz łącze **+ Dodaj** znajdujące się wewnątrz pola grupy **Business data only** (Tylko dane biznesowe) w zasadach DLP:    
   ![Dodawanie — obraz](./media/introduction-to-data-groups/add-to-data-group-1.png)  
2. Wybierz usługi Salesforce i SharePoint, a następnie wybierz opcję **Dodaj usługi**, aby dodać obie usługi do grupy „business data only” (tylko dane biznesowe):    
   ![Dodawanie usług — obraz](./media/introduction-to-data-groups/add-to-data-group-2.png)  
3. Wybierz opcję **Zapisz zasady** z menu widocznego u góry:  
   ![Zapisz zasady](./media/introduction-to-data-groups/add-to-data-group-4.png) 
4. Należy zauważyć, że zarówno usługa SharePoint, jak i Salesforce należą teraz do grupy danych „business data only” (tylko dane biznesowe):  
   ![zaktualizowana grupa danych biznesowych](./media/introduction-to-data-groups/add-to-data-group-3.png)   

W tym przewodniku usługi SharePoint i Salesforce zostały dodane do grupy danych **business data only** (tylko dane biznesowe) w zasadach ochrony przed utratą danych (DLP). Jeśli osoba, która należy do środowiska objętego zasadami DLP, utworzy aplikację, która udostępnia dane między usługą SharePoint lub Salesforce oraz dowolną usługą z grupy danych **No business data allowed** (Bez danych biznesowych), uruchomienie aplikacji nie będzie możliwe.

## <a name="remove-services-from-a-data-group"></a>Usuwanie usług z grupy danych
Jako że wszystkie usługi muszą znajdować się w jednej z dostępnych grup danych, w celu usunięcia usługi z określonej grupy należy po prostu dodać ją do innej grupy, a następnie zapisać zasady.  

## <a name="change-the-default-data-group"></a>Zmiana domyślnej grupy danych
W tym przewodniku domyślna grupa danych zostanie zmieniona z grupy **no business data allowed** (bez danych biznesowych) na grupę **business data only** (tylko dane biznesowe).  

**Ważne**: wszelkie nowe usługi dodane do przepływu zostaną umieszczone w wyznaczonej grupie *domyślnej*. W związku z tym firma Microsoft zaleca zachowanie grupy **No business data allowed** (Bez danych biznesowych) jako grupy domyślnej i ręczne dodawanie usług do grupy **Business data only** (Tylko dane biznesowe).

1. Wybierz opcję **...** znajdującą się w prawym górnym rogu okna grupy danych, która ma zostać wyznaczona jako domyślna grupa danych:    
   ![zmiana grupy domyślnej](./media/introduction-to-data-groups/default-data-group-0.png)  
2. Wybierz opcję **Set as default group** (Ustaw jako grupę domyślną):  
   ![zmiana grupy domyślnej](./media/introduction-to-data-groups/default-data-group-1.png)   
3. Wybierz opcję **Zapisz zasady** z menu widocznego u góry:  
   ![zmiana grupy domyślnej](./media/introduction-to-data-groups/add-to-data-group-4.png) 
4. Należy zauważyć, że ta grupa danych jest teraz wyznaczona jako domyślna grupa danych:  
   ![zmiana grupy domyślnej](./media/introduction-to-data-groups/default-data-group-2.png)   

## <a name="next-steps"></a>Następne kroki
* [Dowiedz się więcej o zasadach ochrony przed utratą danych (DLP)](prevent-data-loss.md)
* [Dowiedz się więcej o środowiskach](environments-overview-admin.md)   

