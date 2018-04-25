---
title: Tworzenie przepływu za pomocą szablonu | Microsoft Docs
description: Możesz utworzyć przepływ przy użyciu jednego z wielu wbudowanych szablonów.
services: ''
suite: flow
documentationcenter: na
author: aftowen
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/07/2017
ms.author: anneta
ms.openlocfilehash: b755d9abe70740a97ad85aaa60b8a3f4685a7b26
ms.sourcegitcommit: d00c10759d4afb54517a0b1032f8d0a509006d5b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-flow-from-a-template-in-microsoft-flow"></a>Tworzenie przepływu za pomocą szablonu w usłudze Microsoft Flow
Utwórz przepływ przy użyciu jednego z wielu wbudowanych szablonów, które umożliwiają na przykład wysłanie do Ciebie wiadomości w usłudze Slack, gdy kierownik wyśle do Ciebie wiadomość e-mail w usłudze Office 365.

**Uwaga:** [utwórz przepływ od podstaw](get-started-logic-flow.md), jeśli masz już na myśli proces, ale nie możesz znaleźć dla niego szablonu.

**Wymagania wstępne**

* Konto w witrynie [flow.microsoft.com](https://flow.microsoft.com)
* Konto usługi Slack
* Poświadczenia usługi Office 365

## <a name="choose-a-template"></a>Wybieranie szablonu
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZJK8cYdjAic?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

1. W witrynie [flow.microsoft.com](https://flow.microsoft.com) wybierz pozycję **Szablony** znajdującą się na górnym pasku nawigacyjnym.
2. Na pasku wyszukiwania wpisz **Slack**, a następnie wybierz ikonę wyszukiwania.
3. Zostaną wyświetlone tylko szablony powiązane z usługą Slack, więc możesz teraz wybrać pozycję **Wyślij wiadomość w usłudze Slack, gdy mój menedżer wyśle do mnie wiadomość e-mail**.
   
    ![Nowa opcja na lewym pasku nawigacji](./media/get-started-logic-template/select-template.png)
4. Potwierdź, że ten szablon będzie wykonywać wymagane zadania, a następnie wybierz pozycję **Użyj tego szablonu**.
5. Jeśli nie zalogowano się do usługi Office lub Slack, wybierz pozycję **Zaloguj**, a następnie postępuj zgodnie z poleceniami.
   
    ![Lista połączeń wymaganych przez szablon](./media/get-started-logic-template/confirm-connections.png)
6. Po potwierdzeniu połączeń wybierz pozycję **Kontynuuj**.
   
    Zostanie wyświetlony przepływ z akcjami z pomarańczowym paskiem tytułu.
   
    ![Domyślne zdarzenia i akcje szablonu](./media/get-started-logic-template/template-default.png)

## <a name="customize-your-flow"></a>Dostosowywanie przepływu
1. Zaznacz pasek tytułu, aby rozwinąć zdarzenie, a następnie dostosuj je (na przykład przez określenie filtru dla interesujących Cię wiadomości e-mail).
2. Akcje wymagające wprowadzania danych zostaną automatycznie rozwinięte.
   
    Na przykład akcja **Ogłoszenie** jest rozwinięta, ponieważ musisz podać kanał, taki jak *\@nazwa_użytkownika*. Możesz również dostosować zawartość wiadomości. Domyślnie wiadomość zawiera tylko temat, ale możesz dołączyć inne informacje.
   
    ![Określanie kanału dla usługi Slack](./media/get-started-logic-template/specify-keyword.png)
3. W górnej części ekranu podaj nazwę przepływu, a następnie wybierz pozycję **Utwórz przepływ**.
4. Jeśli przepływ spełnia Twoje oczekiwania, wybierz pozycję **Gotowe**.
   
    ![Przycisk Gotowe](./media/get-started-logic-template/done.png)

Gdy kierownik wyśle do Ciebie wiadomość e-mail, otrzymasz wiadomość w usłudze Slack z określonymi przez Ciebie informacjami.

## <a name="next-steps"></a>Następne kroki
* [Oglądanie przepływu w akcji](see-a-flow-run.md)
* [Publikowanie własnego szablonu](publish-a-template.md)
* [Korzystanie z szablonu w usłudze Common Data Service](common-data-model-intro.md)
* [Zacznij korzystać z przepływów zespołu](create-team-flows.md) i zaproś inne osoby do wspólnego projektowania przepływów.

