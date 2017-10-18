---
title: "Używanie zasad ochrony przed utratą danych (DLP) | Microsoft Docs"
description: "Dowiedz się, jak przy użyciu zasad ochrony przed utratą danych kontrolować usługi, które mogą udostępniać dane podczas automatyzacji zadań w usłudze Microsoft Flow."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: vls4RPVP5xE
courseduration: 6m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: 2e69fd07103cb16e6c91476462f39586810b4a5d
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="use-data-loss-prevention-dlp-policies"></a>Używanie zasad ochrony przed utratą danych (DLP)
Wraz z powiększającą się listą [usług](https://flow.microsoft.com/services) dostępnych do tworzenia przepływów pracy w usłudze [Microsoft Flow](https://flow.microsoft.com) może zajść potrzeba ochrony danych poufnych lub o krytycznym znaczeniu dla firmy przechowywanych w ramach usług dla przedsiębiorstw, takich jak SharePoint lub Salesforce. Może się okazać, że Twoja organizacja musi utworzyć zasady, które zapewnią, że wrażliwe dane biznesowe nie będą publikowane w ramach usług dla konsumentów, takich jak Twitter i Facebook. Za pomocą usługi Microsoft Flow możesz łatwo tworzyć zasady **ochrony przed utratą danych** (DLP, data loss prevention), które ściśle określają, w jakich usługach dla konsumentów mogą być udostępniane Twoje dane biznesowe, gdy użytkownicy tworzą przepływy.  

## <a name="terms-you-should-get-familiar-with"></a>Terminy, które warto znać
| Termin | Opis |
| --- | --- |
| **DLP** |Skrótowe określenie dla ochrony przed utratą danych. Utworzysz zasady DLP do zarządzania udostępnianiem danych między **usługami**. |
| **Usługi** |[Usługi](https://flow.microsoft.com/services) to aplikacje, takie jak Salesforce, SharePoint oraz Twitter. Te oraz inne usługi są używane do tworzenia przepływów. |
| **Grupa danych** |Logiczna grupa usług. Usługi, które mogą udostępniać dane umieszcza się w tej samej grupie danych. Istnieją dwie grupy danych: grupa **tylko dane biznesowe** oraz grupa **bez danych biznesowych**. |
| **Środowisko** |Ochronę przed utratą danych stosuje się do [środowiska](../environments-overview-admin.md). Środowisko zawiera użytkowników. |
| **Użytkownicy** |Użytkownicy to członkowie organizacji, których mają dotyczyć zasady DLP na podstawie ich członkostwa w środowisku. |
| **Przepływ** |Przepływ to aplikacja przepływu pracy korzystająca z dowolnej kombinacji dostępnych usług. |

## <a name="all-about-how-dlp-policies-work"></a>Wszystko na temat działania zasad DLP
Zasady DLP to po prostu nazwana reguła, która umieszcza każdą usługę w jednej z dwóch wzajemnie wykluczających się grup danych. Reguła ta jest następnie stosowana w odniesieniu do środowiska. Środowisko to logiczna grupa użytkowników. Użytkownicy nie mogą tworzyć przepływów, które udostępniają dane między usługami umieszczonymi w innych grupach danych. Innymi słowy użytkownicy mogą tworzyć tylko takie przepływy, które udostępniają dane między usługami w ramach **jednej** grupy danych. Udostępnianie danych między grupami danych nie jest dozwolone.  

| **Nazwa grupy danych** | **Opis grupy danych** |
| --- | --- |
| **Tylko dane biznesowe** |Wszystkie usługi w tej grupie mogą udostępniać dane między sobą. Nie mogą one współdzielić danych z grupą **bez danych biznesowych**. |
| **Bez danych biznesowych** |Wszystkie usługi w tej grupie mogą udostępniać dane między sobą. Nie mogą one udostępniać danych grupie **tylko dane biznesowe**. |

**Uwaga**: dodanie usługi do jednej grupy danych automatycznie powoduje jej usunięcie z drugiej grupy danych. Jeśli na przykład usługa Twitter znajduje się obecnie w grupie **tylko dane biznesowe**, a nie chcesz zezwalać, aby dane biznesowe można było udostępniać w usłudze Twitter, wystarczy dodać usługę Twitter do grupy danych **bez danych biznesowych**. Spowoduje to usunięcie usługi Twitter z grupy danych **tylko dane biznesowe**.

## <a name="heres-what-you-need-to-create-a-dlp"></a>Do wprowadzenia ochrony przed utratą danych wymagane są następujące elementy
* Dostęp do [centrum administracyjnego](https://admin.flow.microsoft.com) usługi Microsoft Flow  
* Konto w roli administratora środowiska  
* Środowisko z przypisanymi użytkownikami  

## <a name="create-a-dlp-policy"></a>Tworzenie zasad DLP
Krótkie omówienie sposobu tworzenia zasad DLP:  

1. Nadaj nazwę zasadom
2. Wybierz środowisko, którego zasady mają dotyczyć
3. Dodaj usługi do jednej z dwóch grup danych. Pamiętaj, że tylko usługi znajdujące się w danej grupie mogą współdzielić dane, więc wszelkie przepływy utworzone w celu udostępniania danych między usługami znajdującymi się w różnych grupach danych zostaną automatycznie zablokowane po zapisaniu ich przez użytkownika.  

Dostępny jest również bardziej [szczegółowy przewodnik](../prevent-data-loss.md) dotyczący zasad DLP.  

## <a name="examples"></a>Przykłady
* Poniżej przedstawiono zasady ograniczające przepływy w zakresie udostępniania danych biznesowych tylko do usług SharePoint, Office 365 Outlook, OneDrive dla Firm, Dynamics 365, SQL Server i Salesforce oraz użytkowników usługi Office 365:  
  ![](./media/learning-data-loss-prevention/a-few-business-centric-services.png)  
* Poniższe zasady uniemożliwiają wszystkim członkom określonego środowiska tworzenie przepływów udostępniających dane usługi SharePoint. Zwróć uwagę, że SharePoint jest jedyną usługą w grupie danych **tylko dane biznesowe**:  
  ![tylko dane biznesowe](./media/learning-data-loss-prevention/sharepoint-only-no-sharing-guided-learning.png)

