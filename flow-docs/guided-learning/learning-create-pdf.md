---
title: "Konwertowanie i przechowywanie dokumentów | Microsoft Docs"
description: "Dowiedz się, jak utworzyć przepływ konwersji dokumentów."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: ukRhuJGC9A0
courseduration: 14m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: 1c134f70cc065932a38784d672499f178c4d5702
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="convert-and-store-documents"></a>Konwertowanie i przechowywanie dokumentów
W tym temacie zobaczysz, w jaki sposób firma Contoso Flooring korzysta z usługi Microsoft Flow, aby automatycznie konwertować dokumenty do standardowego formatu, a następnie zapisywać je w usłudze SharePoint Online w celu ich bezpiecznego przechowywania w chmurze. Utworzysz przepływ, który wykryje dodanie nowego pliku do folderu usługi OneDrive dla Firm, a następnie przekonwertuje ten plik do formatu PDF i zapisze go w folderze usługi SharePoint Online. 

## <a name="prerequisites"></a>Wymagania wstępne
Na potrzeby tego scenariusza wymagane jest konto **Muhimbi**, usługi konwersji plików do formatu PDF. Jeśli nie masz jeszcze konta Muhimbi, możesz zarejestrować się w celu skorzystania z [bezpłatnej 30-dniowej wersji próbnej](http://www.muhimbi.com/Products/PDF-Converter-for-SharePoint/Products-PDF-Converter-for-SharePoint-Free-Trial.aspx). Postępuj zgodnie z instrukcjami na tej stronie, aby wdrożyć aplikację za pośrednictwem swojej witryny usługi SharePoint Online. 

## <a name="create-the-source-and-target-folders"></a>Tworzenie folderu źródłowego i docelowego
Najpierw musisz utworzyć folder źródłowy i folder docelowy w usługach OneDrive dla Firm i SharePoint Online. 

1. W usłudze OneDrive dla Firm w obszarze **Pliki** utwórz folder o nazwie **Gotowe dokumenty**. 
   
    ![](./media/learning-create-pdf/onedrive-folder.png)
2. W usłudze SharePoint Online w obszarze **Dokumenty udostępnione** utwórz folder o nazwie **PDF — gotowe pliki**. 
   
    ![](./media/learning-create-pdf/sharepoint-folder.png)

## <a name="create-the-flow"></a>Tworzenie przepływu
1. W usłudze Microsoft Flow wybierz pozycję **Moje przepływy**, a następnie pozycję **Utwórz z pustego**. 
   
    ![](./media/learning-create-pdf/create-blank-flow.png)
2. Wybierz pozycję **Przeszukaj setki łączników i wyzwalaczy**.
3. Wyszukaj ciąg **OneDrive**, wybierz usługę **OneDrive dla Firm**, a następnie wybierz wyzwalacz **OneDrive dla Firm — Po utworzeniu pliku**. W obszarze **Folder** wybierz ikonę folderu i wybierz folder **Gotowe dokumenty** utworzony w poprzednim kroku. 
   
    ![](./media/learning-create-pdf/onedrive-trigger.png)
4. Wybierz pozycję **Nowy krok**, a następnie wybierz pozycję **Dodaj akcję**. 
   
    ![](./media/learning-create-pdf/new-action.png)
5. Wyszukaj ciąg **Muhimbi**, wybierz łącznik **Muhimbi PDF** i wybierz akcję **Muhimbi PDF — Konwertuj dokument**.
   
    ![](./media/learning-create-pdf/muhimbi-action.png)
6. W tym momencie usługa Microsoft Flow może wyświetlić monit o uwierzytelnienie w usłudze Muhimbi. Aby umożliwić usłudze Microsoft Flow korzystanie z usługi Muhimbi, należy zarejestrować usługę Muhimbi z użyciem swojego **identyfikatora dzierżawy programu SharePoint**. 
   
   1. Aby znaleźć swój identyfikator dzierżawy, wybierz ikonę koła zębatego **Ustawienia** w usłudze SharePoint Online, a następnie wybierz pozycję **Ustawienia witryny**.
   2. W obszarze **Administracja zbiorem witryn** wybierz pozycję **Uprawnienia aplikacji zbioru witryn**. Twoim identyfikatorem dzierżawy jest identyfikator umieszczony po symbolu „**@**” na dowolnej z list aplikacji. 
      
       ![](./media/learning-create-pdf/tenant-id.png)
7. W akcji **Konwertuj dokument** ustaw następujące wartości:
   
   * **Nazwa pliku źródłowego**: wybierz pozycję **Nazwa pliku** z listy zawartości dynamicznej.
   * **Zawartość pliku źródłowego**: wybierz pozycję **Zawartość pliku** z listy zawartości dynamicznej.
   * **Format danych wyjściowych**: wybierz pozycję **PDF** z listy rozwijanej.
     
     ![](./media/learning-create-pdf/muhimbi-configuration.png)

Do tej pory skonfigurowano następujące kroki w ramach przepływu: 

1. Przepływ jest wyzwalany za każdym razem, gdy nowy plik zostanie dodany do określonego folderu usługi OneDrive dla Firm 
2. Usługa Muhimbi konwertuje ten plik do formatu PDF. 

W ostatnim kroku dodasz akcję, która przeniesie dokument PDF do folderu usługi SharePoint Online, gdzie będzie dostępny dla zespołu.  

1. Wybierz pozycję **Nowy krok**, a następnie wybierz pozycję **Dodaj akcję**.  Wyszukaj ciąg **SharePoint** i wybierz akcję **SharePoint — Utwórz plik**. 
   
    ![](./media/learning-create-pdf/sharepoint-create-file.png)
2. W akcji **Utwórz plik** ustaw następujące wartości:
   
   * **Adres witryny**: adres URL witryny programu SharePoint.  
   * **Ścieżka folderu**: wybierz ikonę folderu i przejdź do folderu **PDF — gotowe pliki**.
   * **Nazwa pliku**: na liście zawartości dynamicznej dla pozycji **Konwertuj dokument** wybierz opcję **Nazwa pliku podstawowego**, a następnie dodaj ciąg „**.pdf**”, aby zapisać plik w programie SharePoint wraz z tym rozszerzeniem. 
   * **Zawartość pliku**: na liście zawartości dynamicznej dla pozycji **Konwertuj dokument** wybierz opcję **Przetworzona zawartość pliku**.
3. Wybierz pozycję **Utwórz przepływ** w górnej części strony, aby zapisać swoją pracę.
   
    ![](./media/learning-create-pdf/sharepoint-configure-file.png)

## <a name="test-the-flow"></a>Testowanie przepływu
1. Aby przetestować przepływ, dodaj nowy plik do folderu **Gotowe dokumenty** w usłudze OneDrive dla Firm. 
2. W usłudze Flow wybierz pozycję **Moje przepływy**, a następnie wybierz nowy przepływ, aby wyświetlić historię uruchamiania. Domyślnie przepływ jest skonfigurowany do uruchamiania co pięć minut. 
3. Po wykonaniu przebiegu przepływu sprawdź, czy plik został przekonwertowany do formatu PDF i zapisany w folderze **PDF — gotowe pliki** programu SharePoint. 
   
    ![](./media/learning-create-pdf/test-the-flow.png)

