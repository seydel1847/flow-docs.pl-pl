---
title: "Wprowadzenie do zasad ochrony przed utratą danych (DLP). | Microsoft Docs"
description: "Wprowadzenie do zasad ochrony przed utratą danych dla usługi Microsoft Flow."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/24/2016
ms.author: deonhe
ms.openlocfilehash: 29eaa9299e09c641538ab8f9dfbc9954bca66a3b
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="data-loss-prevention-dlp-policies"></a>Zasady ochrony przed utratą danych (DLP)
## <a name="what-is-a-data-loss-prevention-policy"></a>Czym są zasady ochrony przed utratą danych?
Dane organizacji mają bardzo istotne znaczenie dla jej sukcesu. Dane muszą być łatwo dostępne, by łatwiej było podejmować decyzje, ale należy je chronić, by nie zostały udostępnione osobom, które nie powinny mieć do nich dostępu. W celu ochrony danych usługa Microsoft Flow (Flow) zapewnia możliwość tworzenia i egzekwowania zasad określających, którym usługom dla klientów/łącznikom mogą być udostępniane określone dane firmy. Zasady określające sposób udostępniania danych nazywamy zasadami ochrony przed utratą danych (DLP).

## <a name="why-create-a-dlp-policy"></a>Dlaczego należy utworzyć zasady DLP?
Zasady DLP należy utworzyć, aby wyraźnie określić, którym usługom dla klientów można udostępnić dane firmy. Na przykład organizacja korzystająca z usługi Flow może nie chcieć, by dane firmy przechowywane w programie SharePoint były automatycznie publikowane w serwisie Twitter. Aby temu zapobiec, można utworzyć zasady DLP, które zablokują korzystanie z danych programu SharePoint jako źródła tweetów.

## <a name="benefits-of-a-dlp-policy"></a>Zalety zasad DLP
* Gwarantują, że dane są zarządzane w jednolity sposób w całej organizacji.  
* Uniemożliwiają przypadkowe publikowanie ważnych danych firmy w takich serwisach jak witryny mediów społecznościowych.   

## <a name="managing-dlp-policies"></a>Zarządzanie zasadami DLP
**Wymagania wstępne**  
Do utworzenia, edycji lub usunięcia zasad DLP wymagane są następujące elementy: 

* Uprawnienia administratora środowiska lub administratora dzierżawy. Więcej informacji na temat uprawnień znajduje się w [temacie dotyczącym środowisk](environments-overview-admin.md).  
* [Licencja Flow P2](billing-questions.md).  

## <a name="create-a-dlp-policy"></a>Tworzenie zasad DLP
**Wymagania wstępne**  
Aby utworzyć zasady DLP, trzeba mieć uprawnienia do przynajmniej jednego środowiska.  

Wykonaj poniższe czynności, aby utworzyć zasady DLP, które uniemożliwią publikowanie danych przechowywanych w programie SharePoint firmy w serwisie Twitter:  

1. Na karcie Zasady danych wybierz link **Nowe zasady**:  
   ![Logowanie](./media/prevent-data-loss/create-policy-1.png)    
2. Wprowadź nazwę zasad DLP *Bezpieczny dostęp do danych dla Contoso* w etykiecie **Nazwa zasad danych** na górze strony, która zostanie otwarta:   
   ![Logowanie](./media/prevent-data-loss/create-policy-2.png)  
3. Wybierz [środowisko](environments-overview-admin.md) na karcie **Dotyczy**.  
   **Uwaga:** jako administrator środowiska możesz tworzyć zasady, które dotyczą tylko jednego środowiska. Jako administrator dzierżawy możesz tworzyć zasady dotyczące wszystkich środowisk, co najmniej jednego środowiska lub wszystkich środowisk z wyłączeniem wybranego zestawu:  
   ![Logowanie](./media/prevent-data-loss/create-policy-3.png)  
4. Wybierz kartę **Grupy danych**:  
   ![Logowanie](./media/prevent-data-loss/create-policy-4.png)  
5. Wybierz link **+ Dodaj** znajdujący się w polu grupy **Tylko dane biznesowe**:    
   ![Logowanie](./media/prevent-data-loss/create-policy-5.png)  
6. Wybierz usługi **SharePoint** i **Salesforce** ze strony **Dodaj usługi**:  
   ![Logowanie](./media/prevent-data-loss/create-policy-6.png)  
7. Wybierz przycisk **Dodaj usługi**, aby dodać usługi, które mogą udostępniać dane biznesowe:    
   ![Logowanie](./media/prevent-data-loss/create-policy-7.png)  
8. Wybierz przycisk **Zapisz zasady**:  
   ![Logowanie](./media/prevent-data-loss/create-policy-8.png)  
9. Po chwili nowe zasady DLP zostaną wyświetlone na liście zasad ochrony przed utratą danych:  
   ![Logowanie](./media/prevent-data-loss/create-policy-9.png)  
10. **Opcjonalnie** Wyślij wiadomość e-mail lub inny komunikat do zespołu zawierający alert z informacją o udostępnieniu nowych zasad DLP.

Gratulacje, utworzono zasady DLP, które umożliwiają aplikacji udostępnianie danych między programem SharePoint i Saleforce oraz blokują udostępnianie danych innym usługom.  

**Uwaga**: dodanie usługi do jednej grupy danych automatycznie powoduje jej usunięcie z drugiej grupy danych. Jeśli na przykład usługa Twitter znajduje się obecnie w grupie **tylko dane biznesowe**, a nie chcesz zezwalać, aby dane biznesowe można było udostępniać w usłudze Twitter, wystarczy dodać usługę Twitter do grupy danych **bez danych biznesowych**. Spowoduje to usunięcie usługi Twitter z grupy danych „tylko dane biznesowe”.  

## <a name="data-sharing-violations"></a>Naruszenia udostępniania danych
Jeśli zostały utworzone zasady DLP wymienione powyżej i jeśli użytkownik utworzy przepływ udostępniający dane między usługą Salesforce (która znajduje się w grupie danych **tylko dane biznesowe**) i usługą Twitter (która znajduje się w grupie danych **żadne dane biznesowe nie są dozwolone**), to zobaczy informację, że przepływ jest **zawieszony** z powodu konfliktu z utworzonymi zasadami zapobiegania utracie danych.  
![tworzenie przepływu](./media/prevent-data-loss/10.png)  

Jeśli użytkownicy skontaktują się z Tobą w sprawie zawieszonych przepływów, oto kwestie do rozważenia:  

1. Dla tego przykładu: jeśli istnieje uzasadnienie biznesowe dla udostępniania danych biznesowych między usługami SharePoint i Twitter, możesz poddać edycji zasady DLP.  
2. Poproś użytkownika o taką edycję przepływu, aby był zgodny z zasadami DLP.  
3. Poproś użytkownika o pozostawienie przepływu w stanie zawieszonym do czasu podjęcia decyzji dotyczącej udostępniania danych między tymi dwoma jednostkami.  

## <a name="find-a-dlp-policy"></a>Znajdowanie zasad DLP
### <a name="admins"></a>Administratorzy
Aby znaleźć określone zasady DLP, administratorzy mogą używać funkcji wyszukiwania w centrum administracyjnym.  

**UWAGA** Administratorzy powinni opublikować wszystkie zasady DLP, by użytkownicy w organizacji zapoznali się z nimi przed utworzeniem przepływów.

### <a name="makers"></a>Kreatorzy
Jeśli nie masz uprawnień administratora, a chcesz dowiedzieć się więcej na temat zasad DLP w Twojej organizacji, skontaktuj się z administratorem. Więcej informacji znajduje się również w [temacie dotyczącym środowisk kreatora](environments-overview-maker.md)  

**UWAGA** Tylko administratorzy mogą edytować lub usuwać zasady DLP.  

## <a name="edit-a-dlp-policy"></a>Edytowanie zasad DLP
1. Uruchom centrum administracyjne, przechodząc do witryny https://admin.flow.microsoft.com.  
2. W uruchomionym centrum administracyjnym wybierz link **Zasady danych** po lewej stronie.  
   ![Logowanie](./media/prevent-data-loss/2.png)  
3. Wyszukaj listę istniejących zasad DLP i wybierz przycisk Edytuj obok zasad, które zamierzasz edytować:  
   ![Logowanie](./media/prevent-data-loss/3.png)  
4. Wprowadź żądane zmiany. Możesz np. zmodyfikować środowisko lub usługi w grupach danych.  
5. Wybierz opcję **Zapisz zasady**, aby zapisać zmiany:  
   ![Logowanie](./media/prevent-data-loss/create-policy-8.png)  

Zasady zostały zaktualizowane. Możesz potwierdzić zmiany wprowadzone do zasad, znajdując je na liście zasad ochrony przed utratą danych i sprawdzając ich właściwości.   

**Uwaga** Zasady DLP utworzone przez administratorów dzierżawy mogą być wyświetlane przez administratorów środowiska, ale nie mogą być przez nich edytowane.  

## <a name="delete-a-dlp-policy"></a>Usuwanie zasad DLP
1. Uruchom centrum administracyjne, przechodząc do witryny https://admin.flow.microsoft.com.  
2. W uruchomionym centrum administracyjnym wybierz link **Zasady danych** po lewej stronie.  
   ![Logowanie](./media/prevent-data-loss/2.png)  
3. Przeszukaj listę istniejących zasad DLP i wybierz przycisk Usuń obok zasad, które zamierzasz usunąć:  
   ![Logowanie](./media/prevent-data-loss/3-delete.png)  
4. Potwierdź, że rzeczywiście chcesz usunąć zasady, wybierając przycisk **Usuń**:  
   ![Logowanie](./media/prevent-data-loss/4.png)  

Zasady zostały usunięte. Możesz sprawdzić, czy zasady nie są już wyświetlane na liście zasad ochrony przed utratą danych, wybierając link **Zasady danych** po lewej stronie i przeglądając listę zasad.   

## <a name="dlp-policy-permissions"></a>Uprawnienia do zasad DLP
Tylko administratorzy dzierżawy i środowiska mogą tworzyć i modyfikować zasady DLP. Więcej informacji na temat uprawnień znajduje się w temacie dotyczącym [środowisk](environments-overview-admin.md).  

## <a name="next-steps"></a>Następne kroki
* [Dowiedz się więcej o środowiskach](environments-overview-admin.md)  
* [Dowiedz się więcej o usłudze Microsoft Flow](getting-started.md)  
* [Dowiedz się więcej na temat centrum administracyjnego](introduction-to-the-admin-center.md)  

