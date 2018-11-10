---
title: Omówienie przepływów obsługujących rozwiązania| Microsoft Docs
description: Informacje o zaletach usługi tworzenia przepływów w rozwiązaniach.
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: kvivek
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/05/2018
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 2515b64629436ccb96de497eaf928b83f281dc5f
ms.sourcegitcommit: b41b45f6fa29a22e9a9a4d3c726a2321b2ff3cbf
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025827"
---
# <a name="overview"></a>Omówienie

Gdy przepływy są hostowane w [rozwiązaniu](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview), stają się przenośne, dzięki czemu można łatwo przenieść je i wszystkie ich składniki z jednego środowiska do innego. Typowy przypadek użycia: niezależny dostawca oprogramowania (ISV) tworzy przepływy w środowisku piaskownicy, a następnie przenosi te przepływy do środowiska testowego. Po zakończeniu testowania niezależny dostawca oprogramowania może przenieść przepływy do środowiska produkcyjnego dla klientów, którzy zakupią te przepływy. Ten proces jest znacznie łatwiejszy, jeśli tworzy się przepływy w rozwiązaniach, a następnie przenosi się rozwiązania i ich zawartość.

Przepływy, które tworzy się wewnątrz rozwiązania, są znane jako przepływy *obsługujące rozwiązania*. Możesz dodać wiele przepływów w ramach jednego rozwiązania.

> [!NOTE] 
> Przepływów nieobsługujących rozwiązania (czyli nieutworzonych w ramach rozwiązania) nie można przenieść do rozwiązania.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz mieć następujące składniki do tworzenia rozwiązań i przepływów obsługujących rozwiązania:

- [Common Data Service for Apps 2.0](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)
- Środowisko w wersji 9.1.0.267 lub nowszej.

  Aby sprawdzić swoją wersję, przejdź do [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com), wybierz opcję **Środowiska**, wybierz środowisko, które Cię interesuje, a następnie wybierz kartę **Szczegóły**.

## <a name="create-a-solution"></a>Tworzenie rozwiązania

Wykonaj następujące kroki, aby utworzyć rozwiązanie:

1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com).
1. Wybierz pozycję **Rozwiązania** na pasku nawigacyjnym.

   ![](./media/overview-solution-flows/select-solutions-from-left-nav.png)

1. Wybierz pozycję **+ Nowe rozwiązanie**.

   ![](./media/overview-solution-flows/select-new-solution.png)

1. Podaj wszystkie wymagane informacje dotyczące nowego rozwiązania, wypełniając m.in. pola **Nazwa wyświetlana**, **Wydawca**, **Wersja** i **Nazwa**. Podanie opisu rozwiązania jest również dobrym pomysłem.

   ![](./media/overview-solution-flows/new-solution.png)

1. Wybierz opcję **Zapisz i zamknij** z menu widocznego u góry.

   ![](./media/overview-solution-flows/save-and-close-solution.png)

   Nowe rozwiązanie może pojawić się, jak na poniższej ilustracji:

   ![](./media/overview-solution-flows/new-solution-created.png)

   > [!TIP]
   > Wybierz pozycję **Rozwiązania**, aby odświeżyć listę rozwiązań, jeśli nowe rozwiązanie nie jest widoczne.

## <a name="learn-more"></a>Dowiedz się więcej

- [Tworzenie przepływu w rozwiązaniu](./create-flow-solution.md)
- [Eksportowanie rozwiązania](./export-flow-solution.md)
- [Importowanie rozwiązania](./import-flow-solution.md)
- [Edytowanie przepływu obsługującego rozwiązania](./edit-solution-aware-flow.md)
- [Usuwanie przepływu obsługującego rozwiązania](./remove-solution-aware-flow.md)
