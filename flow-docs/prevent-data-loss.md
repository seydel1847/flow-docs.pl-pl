---
title: Wprowadzenie do zasad ochrony przed utratą danych (DLP). | Microsoft Docs
description: Wprowadzenie do zasad ochrony przed utratą danych dla usługi Microsoft Flow.
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
ms.date: 02/28/2018
ms.author: deonhe
ms.openlocfilehash: 7dbf6296383551d82d22682121210f1cd339b65e
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "29563090"
---
# <a name="data-loss-prevention-dlp-policies"></a>Zasady ochrony przed utratą danych (DLP)

Ten dokument stanowi wprowadzenie do zasad ochrony przed utratą danych, które pomagają chronić dane organizacji przed udostępnianiem za pomocą zdefiniowanej listy łączników.

## <a name="whats-a-data-loss-prevention-policy"></a>Czym są zasady ochrony przed utratą danych?

Dane organizacji mają bardzo istotne znaczenie dla jej sukcesu. Dane muszą być łatwo dostępne na potrzeby podejmowania decyzji, ale należy je chronić, aby nie zostały udostępnione osobom, które nie powinny mieć do nich dostępu. W celu ochrony danych usługa Microsoft Flow zapewnia możliwość tworzenia i egzekwowania zasad określających, które łączniki mogą mieć dostęp do danych biznesowych i udostępniać je. Zasady określające sposób udostępniania danych nazywamy zasadami ochrony przed utratą danych (DLP).

## <a name="why-create-a-dlp-policy"></a>Dlaczego należy utworzyć zasady DLP?

Zasady DLP tworzy się w celu wyraźnego zdefiniowania, które łączniki konsumenta mogą uzyskać dostęp do danych biznesowych i udostępniać je. Na przykład organizacja korzystająca z usługi Microsoft Flow może nie chcieć, aby dane firmy przechowywane w programie SharePoint były automatycznie publikowane w serwisie Twitter. Aby temu zapobiec, należy utworzyć zasady DLP, które zablokują korzystanie z danych programu SharePoint jako źródła tweetów.

## <a name="benefits-of-a-dlp-policy"></a>Zalety zasad DLP

* Gwarantują, że dane są zarządzane w jednolity sposób w całej organizacji.
* Uniemożliwiają przypadkowe publikowanie ważnych danych firmy do łączników takich jak witryny mediów społecznościowych.

## <a name="managing-dlp-policies"></a>Zarządzanie zasadami DLP

### <a name="prerequisites-for-managing-dlp-policies"></a>Wymagania wstępne dla zarządzania zasadami DLP

* Uprawnienia administratora środowiska lub administratora dzierżawy.

    Więcej informacji na temat uprawnień znajduje się w [artykule dotyczącym środowisk](environments-overview-admin.md).
* [Licencja P2 usługi Microsoft Flow](billing-questions.md).

## <a name="create-a-dlp-policy"></a>Tworzenie zasad DLP

### <a name="prerequisites-for-creating-dlp-policies"></a>Wymagania wstępne dla tworzenia zasad DLP

Do utworzenia zasad DLP są wymagane uprawnienia do co najmniej jednego środowiska.

Wykonaj poniższe kroki, aby utworzyć zasady DLP, które uniemożliwią publikowanie danych w witrynie programu SharePoint firmy do serwisu Twitter:

1. Zaloguj się do [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com) (Centrum administracyjnego).

1. Wybierz kartę Zasady danych, a następnie link **Nowe zasady**:

    ![Logowanie](./media/prevent-data-loss/create-policy-1.png)
1. Wybierz kartę **Grupy danych**.

1. Wprowadź nazwę zasad DLP *Bezpieczny dostęp do danych dla Contoso* w ramach etykiety **Nazwa zasad danych** na górze strony:

    ![Logowanie](./media/prevent-data-loss/create-policy-2.png)

1. Wybierz [środowisko](environments-overview-admin.md) na karcie **Środowiska**.

    > [!NOTE]
    > Jako administrator środowiska możesz tworzyć zasady, które dotyczą tylko jednego środowiska. Jako administrator dzierżawy możesz tworzyć zasady, które dotyczą dowolnej kombinacji środowisk:
    >
    >

    ![Wybieranie środowiska](./media/prevent-data-loss/create-policy-3.png)

1. Wybierz kartę **Grupy danych**:

    ![Wybieranie grup danych](./media/prevent-data-loss/create-policy-4.png)

1. Wybierz link **Dodaj** znajdujący się w polu grupy **Tylko dane biznesowe**:

    ![Wybieranie opcji dodawania](./media/prevent-data-loss/create-policy-5.png)

1. Wybierz łączniki **SharePoint** i **Salesforce** ze strony **Dodaj łączniki**:

   ![Wybieranie łączników](./media/prevent-data-loss/create-policy-6.png)

1. Wybierz przycisk **Dodaj łączniki**, aby dodać łączniki, które mogą udostępniać dane biznesowe.

1. Wybierz polecenie **Zapisz zasady** w prawym górnym rogu ekranu.

1. Po chwili nowe zasady DLP zostaną wyświetlone na liście zasad ochrony przed utratą danych:

    ![Lista zasad DLP](./media/prevent-data-loss/create-policy-9.png)

1. **Opcjonalnie** Wyślij wiadomość e-mail lub inny komunikat do zespołu zawierający alert z informacją o udostępnieniu nowych zasad DLP.

Gratulacje, utworzono zasady DLP, które umożliwiają aplikacji udostępnianie danych między programem SharePoint i usługą Salesforce oraz blokują udostępnianie danych innym usługom.

> [!NOTE]
> Dodanie usługi do jednej grupy danych automatycznie powoduje jej usunięcie z drugiej grupy danych. Jeśli na przykład usługa Twitter znajduje się obecnie w grupie **tylko dane biznesowe**, a nie chcesz zezwalać, aby dane biznesowe można było udostępniać w usłudze Twitter, wystarczy dodać usługę Twitter do grupy danych **bez danych biznesowych**. Spowoduje to usunięcie usługi Twitter z grupy danych „tylko dane biznesowe”.
>
>

## <a name="data-sharing-violations"></a>Naruszenia udostępniania danych

Jeśli po utworzeniu zasad DLP wymienionych powyżej użytkownik utworzy przepływ udostępniający dane między usługą Salesforce (która znajduje się w grupie danych **Tylko dane biznesowe**) i usługą Twitter (która znajduje się w grupie danych **Żadne dane biznesowe nie są dozwolone**), to zobaczy informację, że przepływ jest **zawieszony** z powodu konfliktu z utworzonymi zasadami zapobiegania utracie danych.

![Tworzenie przepływu](./media/prevent-data-loss/10.png)

Jeśli użytkownicy skontaktują się z Tobą w sprawie zawieszonych przepływów, oto kwestie do rozważenia:

1. Jeśli w przypadku tego przykładu istnieje uzasadnienie biznesowe dla udostępniania danych biznesowych między usługami SharePoint i Twitter, możesz zmodyfikować zasady DLP.

1. Poproś użytkownika o taką edycję przepływu, aby był zgodny z zasadami DLP.

1. Poproś użytkownika o pozostawienie przepływu w stanie zawieszonym do czasu podjęcia decyzji dotyczącej udostępniania danych między tymi dwoma jednostkami.

## <a name="find-a-dlp-policy"></a>Znajdowanie zasad DLP

### <a name="admins"></a>Administratorzy

Aby znaleźć określone zasady DLP, administratorzy mogą używać funkcji wyszukiwania w centrum administracyjnym.

> [!NOTE]
> Administratorzy powinni opublikować wszystkie zasady DLP, aby użytkownicy w organizacji zapoznali się z nimi przed tworzeniem przepływów.
>
>

### <a name="makers"></a>Kreatorzy

Jeśli nie masz uprawnień administratora, a chcesz dowiedzieć się więcej na temat zasad DLP w Twojej organizacji, skontaktuj się z administratorem. Więcej informacji znajduje się również w [artykule dotyczącym środowisk kreatora](environments-overview-maker.md)

> [!NOTE]
> Tylko administratorzy mogą edytować lub usuwać zasady DLP.
>
>

## <a name="edit-a-dlp-policy"></a>Edytowanie zasad DLP

1. Uruchom [Centrum administracyjne](https://admin.flow.microsoft.com).

1. W uruchomionym centrum administracyjnym wybierz link **Zasady danych** po lewej stronie.

    ![Wybieranie zasad danych](./media/prevent-data-loss/2.png)

1. Przeszukaj listę istniejących zasad DLP i wybierz przycisk edycji obok zasad, które zamierzasz edytować.

1. Wprowadź wymagane zmiany zasad. Możesz np. zmodyfikować środowisko lub usługi w grupach danych.

1. Wybierz pozycję **Zapisz zasady**, aby zapisać zmiany.

> [!NOTE]
> Zasady DLP utworzone przez administratorów dzierżawy mogą być wyświetlane przez administratorów środowiska, ale nie mogą być przez nich edytowane.
>
>

## <a name="delete-a-dlp-policy"></a>Usuwanie zasad DLP

1. Uruchom [Centrum administracyjne](https://admin.flow.microsoft.com).

1. Wybierz kartę **Zasady danych** po lewej stronie.

    ![Wybieranie karty Zasady danych](./media/prevent-data-loss/2.png)

1. Przeszukaj listę istniejących zasad DLP i wybierz przycisk usuwania obok zasad, które zamierzasz usunąć:

    ![Wybieranie przycisku usuwania](./media/prevent-data-loss/3-delete.png)

1. Potwierdź, że rzeczywiście chcesz usunąć zasady, wybierając przycisk **Usuń**:

    ![Potwierdzanie usuwania zasad](./media/prevent-data-loss/4.png)

## <a name="dlp-policy-permissions"></a>Uprawnienia do zasad DLP

Tylko administratorzy dzierżawy i środowiska mogą tworzyć i modyfikować zasady DLP. Więcej informacji na temat uprawnień znajduje się w artykule dotyczącym [środowisk](environments-overview-admin.md).

## <a name="next-steps"></a>Następne kroki

* [Dowiedz się więcej o środowiskach](environments-overview-admin.md)
* [Dowiedz się więcej o usłudze Microsoft Flow](getting-started.md)
* [Dowiedz się więcej na temat centrum administracyjnego](admin-center-introduction.md)
* [Dowiedz się więcej o integracji danych](https://docs.microsoft.com/common-data-service/entity-reference/dynamics-365-integration)
