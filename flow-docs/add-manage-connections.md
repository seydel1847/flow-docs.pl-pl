---
title: Dowiedz się, jak nawiązać połączenie z danymi za pomocą połączeń i lokalnych bram danych | Microsoft Docs
description: Dodawanie połączeń z produktami SharePoint, SQL Server, OneDrive dla Firm, Salesforce, Office 365, OneDrive, Dropbox, Twitter, Dysk Google itp. lub zarządzanie nimi
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/15/2017
ms.author: stepsic
ms.openlocfilehash: c0e115732e26bdeb0d7e4c3c60e1aa6c63e0ffc1
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "23439780"
---
# <a name="manage-connections-in-microsoft-flow"></a>Zarządzanie połączeniami w usłudze Microsoft Flow
Utworzenie połączenia w usłudze Microsoft Flow zapewnia łatwy dostęp do danych podczas tworzenia przepływu. Usługa Microsoft Flow zawiera często używane połączenia, w tym połączenia z produktami SharePoint, SQL Server, Office 365, OneDrive dla Firm, Salesforce, Excel, Dropbox, Twitter itp. Połączenia są współdzielone z usługą PowerApps, więc po utworzeniu połączenia w jednym produkcie pojawia się ono w drugim i na odwrót.

Za pomocą połączenia możesz na przykład wykonywać następujące zadania:

* Zaktualizowanie listy programu SharePoint.
* Pobranie danych z pliku programu Excel na koncie usługi OneDrive dla Firm lub Dropbox.
* Wysłanie wiadomości e-mail w usłudze Office 365.
* Wysłanie tweetu.

Połączenie możesz utworzyć w wielu scenariuszach, takich jak:

* Tworzenie [przepływu z szablonu](get-started-logic-template.md)
* Tworzenie [przepływu od podstaw](get-started-logic-flow.md) lub aktualizowanie istniejącego przepływu
* Tworzenie połączenia bezpośrednio w [witrynie internetowej usługi Microsoft Flow][1]

W tym temacie opisano sposób zarządzania połączeniami w [witrynie internetowej usługi Microsoft Flow][1].

## <a name="add-a-connection"></a>Dodawanie połączenia
1. Zaloguj się w [witrynie internetowej usługi Microsoft Flow][1] przy użyciu konta służbowego lub konta organizacji.
2. Wybierz ikonę koła zębatego w prawym górnym rogu, a następnie wybierz pozycję **Połączenia**.
   
    ![Wybieranie pozycji Połączenia](./media/add-manage-connections/connections-menu.png)
3. Wybierz pozycję **Utwórz połączenie**.
4. Z listy **Dostępne połączenia** wybierz połączenie, które chcesz skonfigurować, np. SharePoint.
5. Wybierz przycisk **Utwórz połączenie**, a następnie wprowadź swoje poświadczenia, aby skonfigurować połączenie.

Po skonfigurowaniu połączenia jest ono wyświetlane w obszarze **Moje połączenia**.

## <a name="connect-to-your-data-through-an-on-premises-data-gateway"></a>Łączenie z danymi za pomocą lokalnej bramy danych
W trakcie tworzenia tej dokumentacji programy SQL Server i SharePoint Server obsługują lokalną bramę danych. Aby utworzyć połączenie korzystające z bramy:

1. Wykonaj kroki podane wcześniej w tym temacie, aby dodać połączenie.
2. Na liście **Dostępne połączenia** wybierz pozycję **SQL Server**, a następnie zaznacz pole wyboru **Połącz za pośrednictwem lokalnej bramy danych**.
   
    ![Wybieranie bramy](./media/add-manage-connections/select-gateway.png)
   
   > [!IMPORTANT]
   > Bramy danych programu Microsoft SharePoint obsługują ruch HTTP, ale nie obsługują ruchu HTTPS.
   > 
   > 
3. Podaj poświadczenia połączenia, a następnie wybierz bramę, której chcesz używać.
   
    Aby uzyskać więcej informacji, zobacz [Zarządzanie bramami](gateway-manage.md) i [Opis bram](gateway-reference.md).
   
    Po skonfigurowaniu połączenia jest ono wyświetlane w obszarze **Moje połączenia**.

## <a name="delete-a-connection"></a>Usuwanie połączenia
1. Przejdź do strony **Moje połączenia**, a następnie wybierz ikonę kosza przy połączeniu, które chcesz usunąć.
   
    ![Usuwanie połączenia](./media/add-manage-connections/delete-connection.png)
2. Wybierz przycisk **OK**, aby potwierdzić usunięcie połączenia.
   
    ![Potwierdzanie usunięcia](./media/add-manage-connections/delete-confirmation.png)

Usunięcie połączenia spowoduje jego usunięcie zarówno z usługi PowerApps, jak i Microsoft Flow.

## <a name="update-a-connection"></a>Aktualizacja połączenia
Możesz zaktualizować połączenie, które nie działa z powodu zmiany szczegółów konta lub hasła.

1. Na stronie **Moje połączenia** wybierz link **Weryfikuj hasło** przy połączeniu, które chcesz zaktualizować.
   
    ![Weryfikuj hasło](./media/add-manage-connections/verify-password.png)
2. Po wyświetleniu monitu zaktualizuj połączenie za pomocą nowych poświadczeń.

Po zaktualizowaniu połączenia jest ono aktualizowane zarówno w usłudze PowerApps, jak i Microsoft Flow.

## <a name="troubleshoot-a-connection"></a>Rozwiązywanie problemów z połączeniem
W zależności od zasad organizacji może być konieczne używanie tego samego konta do logowania się w usłudze Microsoft Flow i tworzenia połączenia do produktów SharePoint, Office 365 i OneDrive dla Firm.

Na przykład zalogowanie się w usłudze Microsoft Flow przy użyciu konta *yourname@outlook.com* jest możliwe, ale próba połączenia z programem SharePoint przy użyciu konta *yourname@contoso.com* jest blokowana. Możesz zamiast tego zalogować się w usłudze Microsoft Flow przy użyciu konta *yourname@contoso.com*, co umożliwi połączenie z programem SharePoint.

<!--Reference links in article-->
[1]: https://flow.microsoft.com
