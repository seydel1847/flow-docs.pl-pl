---
title: "Usługa Microsoft Flow dla deweloperów w przedsiębiorstwach, niezależnych dostawców oprogramowania i partnerów| Microsoft Docs"
description: "Wprowadzenie do projektowania rozwiązań dla usługi Microsoft Flow."
services: 
suite: flow
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/31/2018
ms.author: mblythe
ms.openlocfilehash: d8886f0828ca3b8ccf7ae1ce9c46f6e9b8fcc766
ms.sourcegitcommit: f3261717768177e03e825c0dd2e3ba736dc9b94d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2018
---
# <a name="microsoft-flow-for-enterprise-developers-isvs-and-partners"></a>Usługa Microsoft Flow dla deweloperów w przedsiębiorstwach, niezależnych dostawców oprogramowania i partnerów

Deweloperzy mogą rozszerzać usługę Microsoft Flow, umożliwiając korzystanie z jeszcze bardziej wydajnych rozwiązań dla organizacji i klientów.

## <a name="microsoft-flow-for-enterprise-developers"></a>Usługa Microsoft Flow dla deweloperów w firmach

Jako deweloper w przedsiębiorstwie możesz umożliwić Twojej organizacji tworzenie niezawodnych i dostosowanych rozwiązań w usłudze Microsoft Flow:

- **Tworzenie łączników niestandardowych**: tworzenie łączników niestandardowych w celu łączenia z należącymi do Twojej organizacji danymi i usługami sieci Web za pośrednictwem usługi Microsoft Flow. [Dowiedz się więcej](https://docs.microsoft.com/connectors/custom-connectors/)

- **Tworzenie funkcji usługi Azure Functions**: opracowywanie funkcji usługi Azure Functions w celu rozszerzenia aplikacji za pomocą niestandardowej logiki po stronie serwera. [Dowiedz się więcej](https://docs.microsoft.com/azure/azure-functions/functions-flow-scenario)

- **Osadzanie usługi Microsoft Flow**: osadzanie usługi Microsoft Flow bezpośrednio we własnych środowiskach witryn internetowych w celu tworzenia zintegrowanych rozwiązań, dzięki czemu są ujawniane przepływy pracy lub procesy, w ramach których osoby w organizacji już wykonują swoją pracę. [Dowiedz się więcej](embed-flow-dev.md)

## <a name="microsoft-flow-for-isvs-and-microsoft-partners"></a>Usługa Microsoft Flow dla niezależnych dostawców oprogramowania i partnerów firmy Microsoft

Jako partner firmy Microsoft lub niezależny dostawca oprogramowania (ISV, Independent Software Vendor) szybciej przyciągniesz klientów, rozszerzając produkty pod kątem integracji z danymi i procesami biznesowymi klientów, a ponad to dodasz i dostosujesz przepływy pracy w celu zautomatyzowania procesów biznesowych w ramach aplikacji. Po wykonaniu poniższych siedmiu kroków aplikacja będzie mogła wykorzystać niezawodny aparat przepływu pracy skalowalny w chmurze, który umożliwia łączenie się z ponad 200 różnymi usługami.

| Faza | Krok | Kiedy jest to potrzebne? |
| --- | --- | --- |
| Programowanie | 1. Tworzenie niestandardowego łącznika danych | Jeśli chcesz uwidocznić własne dane niezależnego dostawcy oprogramowania dla usługi PowerApps lub Microsoft Flow |
| Programowanie | 2. Dodawanie obsługi aplikacji w celu uwierzytelniania użytkowników w usłudze Azure Active Directory (Azure AD) | Jeśli chcesz osadzić interfejs użytkownika usługi Microsoft Flow lub udostępnić rozwiązanie w usłudze Microsoft AppSource | 
| Programowanie | 3. Osadzanie interfejsu użytkownika usługi Microsoft Flow w aplikacji przy użyciu elementu iframe opartego na sieci Web | Jeśli chcesz uwzględnić tworzenie przepływu lub zarządzanie nim w aplikacji | 
| Programowanie | 4. Tworzenie i publikowanie szablonów przepływów | Jeśli chcesz wstępnie skompilować przepływy dla klientów | 
| Programowanie | 5. Dodawanie logiki aplikacji w celu programistycznego wdrożenia przepływów | Jeśli chcesz automatycznie wdrożyć wstępnie skompilowane przepływy dla klientów | 
| Dystrybucja | 6. Udzielanie klientom licencji na usługę Microsoft Flow za pomocą programu Microsoft Cloud Solution Provider | Jeśli klienci nie mają licencji usługi Office 365 ani Dynamics 365 |
| Dystrybucja | 7. Udostępnianie rozwiązania w usłudze Microsoft AppSource | Zalecane w celu zwiększenia widoczności rozwiązania niezależnego dostawcy oprogramowania |

### <a name="1-connecting-to-your-apis-or-enabling-customers-to-connect-to-your-apis"></a>1. Łączenie się z interfejsami API ALBO umożliwianie klientom łączenia się z interfejsami API

Niezależni dostawcy oprogramowania często mają zastrzeżone dane, do których klienci powinni uzyskiwać dostęp za pośrednictwem przepływów dostawcy. Możesz uwidocznić dostęp do dowolnych swoich danych za pośrednictwem łącznika niestandardowego. [Dowiedz się więcej](https://docs.microsoft.com/connectors/custom-connectors/)

Po utworzeniu łącznika można udostępnić go klientom na dwa sposoby:
- Łącznik można wdrożyć w dzierżawie klienta za pośrednictwem interfejsów API REST lub programu PowerShell.
- Aby publicznie udostępnić łącznik niestandardowy dla wszystkich użytkowników, można przesłać go do certyfikacji. [Dowiedz się więcej](https://docs.microsoft.com/connectors/custom-connectors/submit-certification)

### <a name="2-authentication"></a>2. Uwierzytelnianie 

Aby można było wywołać interfejsy API REST i osadzić uwierzytelniony interfejs użytkownika, aplikacja musi uwierzytelniać użytkowników końcowych i klientów za pomocą federacyjnego logowania jednokrotnego usługi Azure AD. [W tym miejscu](https://identity.microsoft.com/) można znaleźć informacje o sposobie włączania federacyjnego logowania jednokrotnego usługi AAD. Nie jest obsługiwany dostęp nieuwierzytelniony ani dostęp przy użyciu dostawców tożsamości innych niż usługa Azure AD. 

### <a name="3-embedding-ui-components"></a>3. Osadzanie składników interfejsu użytkownika

Osadzenie usługi Microsoft Flow w aplikacji umożliwia głęboką, kontekstową integrację aplikacji i wszystkich innych usług obsługiwanych przez usługę Microsoft Flow. [Dowiedz się więcej](embed-flow-dev.md)

### <a name="4-create-and-publish-flow-templates"></a>4. Tworzenie i publikowanie szablonów przepływów

Gdy masz już łącznik, należy opublikować szablony demonstrujące sposób użycia usługi. Te szablony będą służyć jako przykłady, za pomocą których użytkownicy mogą uczyć się i które następnie mogą rozszerzać na potrzeby własnych unikatowych przepływów pracy. [Dowiedz się więcej](publish-a-template.md)

### <a name="5-deployment"></a>5. Wdrażanie

Aby udostępnić użytkownikom końcowym przepływy, których mogą używać automatycznie, wdróż je w dzierżawach usługi Azure AD tych użytkowników. Użyj pakietu wdrożeniowego wdrażanego przy użyciu interfejsów API REST lub programu PowerShell. [Dowiedz się więcej](https://docs.microsoft.com/powerapps/export-import-packages)

### <a name="6-licensing"></a>6. Licencjonowanie

Jeśli klienci mają już usługę Office 365 lub Dynamics 365, a te licencje są skojarzone z tożsamościami, za pomocą których użytkownicy logują się w usłudze Azure AD, nie ma żadnych dodatkowych wymagań dotyczących licencjonowania. Jednak jeśli klienci nie korzystają z usługi Office 365 ani Dynamics 365, należy uzyskać w ich imieniu prawa do używania usługi Microsoft Flow, aby mieli licencje na korzystanie z tych składników osadzonych w aplikacji.

Udostępniamy program [Microsoft Cloud Solution Provider](https://partner.microsoft.com/cloud-solution-provider) na potrzeby uzyskiwania licencji w imieniu klientów. Istnieją dwa różne [plany cenowe](https://flow.microsoft.com/pricing/) dostępne dla usługi Microsoft Flow — sprawdź szczegóły planów i funkcji.

### <a name="7-list-on-appsource"></a>7. Udostępnianie w usłudze AppSource

Po zintegrowaniu usługi Microsoft Flow w aplikacji można udostępnić ją w usłudze AppSource. Usługa AppSource umożliwia znalezienie nowych potencjalnych klientów przez utworzenie aplikacji i opublikowanie jej w usłudze AppSource, dzięki czemu nowi klienci będą mogli ją testować. [Dowiedz się więcej](dev-appsource-test-drive.md)
