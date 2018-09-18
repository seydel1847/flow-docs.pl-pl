---
title: Informacje dotyczące dodawania innych właścicieli do przepływu i tworzenia przepływów zespołu | Microsoft Docs
description: Usługa Microsoft Flow ułatwia automatyzację powtarzających się zadań. Użytkowników lub grupy możesz dodawać jako właścicieli oraz wspólnie projektować przepływy i zarządzać nimi.
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
ms.date: 04/21/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 238ef8eac80d3259981cb11cc21e3b05eb83e0ec
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689737"
---
# <a name="create-team-flows"></a>Tworzenie przepływów zespołu
Utwórz przepływ zespołu, dodając inne osoby w Twojej organizacji jako właścicieli. Wszyscy właściciele przepływu zespołu mogą wykonywać następujące akcje:

* Wyświetlanie historii przepływu (każdego przebiegu)
* Zarządzanie właściwościami przepływu (na przykład uruchamianie lub zatrzymywanie przepływu, dodawanie właścicieli lub aktualizowanie poświadczeń dla połączenia)
* Edytowanie definicji przepływu (na przykład dodawanie lub usuwanie akcji albo warunku)
* Dodawanie i usuwanie innych właścicieli (ale nie autora przepływu)
* Usuwanie przepływu

Jeśli jesteś twórcą lub właścicielem przepływu zespołu, znajdziesz go na karcie **Przepływy zespołu** w usłudze [Microsoft Flow](https://flow.microsoft.com).

![karta przepływów zespołu](./media/create-team-flows/addowner5.png)

> [!NOTE]
> Połączenia udostępnione mogą być używane **wyłącznie** w przepływie, w którym zostały utworzone.
> 
> 

Właściciele mogą używać usług w przepływie, ale nie mogą modyfikować poświadczeń połączenia utworzonego przez innego właściciela.

## <a name="prerequisites"></a>Wymagania wstępne
Do utworzenia przepływu zespołu musisz mieć [płatny plan usługi Microsoft Flow](https://flow.microsoft.com/pricing/). Dodatkowo musisz być twórcą lub właścicielem, aby dodawać/usuwać właścicieli z przepływu zespołu.

## <a name="create-a-team-flow"></a>Tworzenie przepływu zespołu
Poniżej przedstawiono procedurę tworzenia przepływu zespołu i dodawania kolejnych właścicieli do przepływu zespołu.

1. Zaloguj się do usługi [Microsoft Flow](https://flow.microsoft.com), a następnie wybierz pozycję **Moje przepływy**.
2. Wybierz ikonę osób dla przepływu, który chcesz zmodyfikować:
   
    ![ikona zespołu](./media/create-team-flows/addowner1.png)
3. Wprowadź nazwę, adres e-mail albo nazwę grupy dla osoby lub grupy, którą chcesz dodać jako właściciela:
   
    ![wyszukiwanie użytkownika](./media/create-team-flows/addowner2.png)
4. Z listy, która zostanie wyświetlona, wybierz użytkownika, którego chcesz ustawić jako właściciela:
   
    ![wybieranie użytkownika](./media/create-team-flows/addowner3.png)
   
     Wybrany użytkownik lub wybrana grupa stanie się właścicielem przepływu:
   
    ![nowy właściciel](./media/create-team-flows/addowner4.png)
   
     Gratulujemy &mdash; utworzono przepływ zespołu!

##<a name="add-a-list-as-a-co-owner"></a>Dodawanie listy jako współwłaściciela

Listy programu SharePoint można dodać do przepływu jako współwłaścicieli, aby każdy, kto ma dostęp do listy z możliwością edycji, automatycznie uzyskiwał dostęp do przepływu z możliwością edycji. Po udostępnieniu przepływu wystarczy rozpowszechnić link do niego.

## <a name="remove-an-owner"></a>Usuwanie właściciela
> [!IMPORTANT]
> W przypadku usunięcia właściciela, którego poświadczenia są używane do uzyskiwania dostępu do usług Microsoft Flow, należy zaktualizować poświadczenia dla tych połączeń, aby przepływ mógł nadal działać prawidłowo.
> 
> 

1. Wybierz ikonę osób dla przepływu, który chcesz zmodyfikować:
   
    ![wybieranie ikony osób](./media/create-team-flows/removeowner1.png)
2. Wybierz ikonę **Usuń** dla właściciela, którego chcesz usunąć:
   
    ![wybieranie usuwania](./media/create-team-flows/removeowner2.png)
3. W oknie dialogowym potwierdzenia wybierz pozycję **Usuń tego właściciela**:
   
    ![potwierdzanie usunięcia](./media/create-team-flows/removeowner3.png)
4. Gratulujemy &mdash; usunięty użytkownik lub usunięta grupa nie jest już właścicielem przepływu:
   
    ![użytkownik usunięty](./media/create-team-flows/removeowner4.png)

## <a name="embedded-and-other-connections"></a>Połączenia osadzone i inne połączenia
Połączenia używane w ramach przepływu dzielą się na dwie kategorie:

* **Osadzone** &mdash; te połączenia są używane w przepływie.
* **Inne** &mdash; te połączenia zostały zdefiniowane dla przepływu, ale nie są w nim używane.

Jeśli przestaniesz korzystać z połączenia w przepływie, połączenie to będzie wyświetlane na liście połączeń **Inne** do czasu ponownego dołączenia go przez właściciela do przepływu.

Lista połączeń jest wyświetlana poniżej listy właścicieli we właściwościach przepływu:

![osadzone połączenia](./media/create-team-flows/embeddedconnections.png)

