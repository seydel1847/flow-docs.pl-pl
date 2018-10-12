---
title: 'Przykład: praca z przepływami procesów biznesowych (Przewodnik dla deweloperów dotyczący usługi Dynamics 365 Customer Engagement) | MicrosoftDocs'
description: W tym przykładzie pokazano, jak pracować programowo z przepływami procesów biznesowych, na przykład pobierać wystąpienia przepływu procesów biznesowych dla rekordu jednostki, pobierać aktywną ścieżkę dla wystąpienia przepływu procesów biznesowych i jego etapów procesów oraz zmieniać aktywny etap.
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.service: flow
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 7d378504-b4b2-4a09-838c-69ee094072ef
caps.latest.revision: 15
author: msftman
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: 6fe2b6d600d86dfd807dbb1ef794a1f428f26fbf
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690059"
---
# <a name="sample-work-with-business-process-flows"></a>Przykład: praca z przepływami procesów biznesowych

W tym przykładzie pokazano, jak pracować programowo z przepływami procesów biznesowych, na przykład pobierać wystąpienia przepływu procesów biznesowych dla rekordu jednostki, pobierać aktywną ścieżkę dla wystąpienia przepływu procesów biznesowych i jego etapów procesów oraz zmieniać aktywny etap. Aby uzyskać więcej informacji na temat tych pojęć, zobacz temat [Praca z przepływami procesów biznesowych przy użyciu kodu](business-process-flows-code.md)  

 Ten przykład jest dostępny do pobrania na stronie [Przykład: praca z przepływami procesów biznesowych](https://go.microsoft.com/fwlink/p/?LinkId=846108).  

<a name="BKMK_Prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby móc uruchomić przykład, należy spełnić następujące wymagania:  

1. dostęp do środowiska Common Data Service for Apps;  

2. odpowiednie uprawnienia do jednostek Potencjalny klient, Szansa sprzedaży i Przepływ pracy oraz rekordów jednostki definicji przepływu procesów biznesowych użytej w tym przykładzie;  

3. oprogramowanie Visual Studio 2015 lub nowszy do uruchomienia przykładu;  

4. połączenie internetowe, aby pobrać przykładowy projekt i przywrócić pakiety NuGet używane w przykładowym projekcie.  

<a name="BKMK_WhatThisSampleDoes"></a>   
## <a name="what-this-sample-does"></a>Działanie tego przykładu  

1.  Tworzy przykładowy rekord potencjalnego klienta. Automatycznie tworzy wystąpienie przepływu procesów biznesowych „Proces sprzedaży — od potencjalnego klienta do szansy sprzedaży” dla rekordu potencjalnego klienta.  

2.  Konwertuje rekord potencjalnego klienta na rekord szansy sprzedaży.  


4.  Pobiera wystąpienia przepływu procesów biznesowych powiązane z rekordem „Potencjalny klient” przy użyciu komunikatu `RetrieveProcessInstances`. Pierwszy rekord w zwracanej kolekcji jest aktywnym wystąpieniem przepływu procesów biznesowych dla rekordu szansy sprzedaży, w tym przypadku jest to „Proces sprzedaży — od potencjalnego klienta do szansy sprzedaży”.  

5.  Pobiera aktywną ścieżkę i etapy procesu dla wystąpienia „Proces sprzedaży — od potencjalnego klienta do szansy sprzedaży” przy użyciu komunikatu `RetrieveActivePath`.  

6.  Pobiera bieżący aktywny etap dla wystąpienia „Proces sprzedaży — od potencjalnego klienta do szansy sprzedaży” i monituje użytkownika, czy przejść do następnego etapu. Po potwierdzeniu przejścia ustawia następny etap w aktywnej ścieżce jako aktywny etap wystąpienia „Proces sprzedaży — od potencjalnego klienta do szansy sprzedaży”.  

7.  Następnie pyta użytkownika, czy usunąć rekordy utworzone podczas uruchomienia przykładu.  

     Oto dane wyjściowe przykładu:  

    ![Dane wyjściowe przykładu](media/work-with-bpf-sample-output.png "Dane wyjściowe przykładu")  

<a name="BKMK_runSample"></a>   
## <a name="run-the-sample"></a>Uruchamianie przykładu  

1. [Pobierz](https://go.microsoft.com/fwlink/p/?LinkId=846108) przykładowy projekt WorkWithBPF programu Visual Studio i wyodrębnij go do folderu na komputerze.  

2. Znajdź plik `WorkWithBPF.sln` w wyodrębnionym folderze i otwórz go w programie Visual Studio.  

3. Przykładowy projekt korzysta z pakietów NuGet, które należy przywrócić przed uruchomieniem przykładu. Należy upewnić się, że automatyczne przywracanie pakietów NuGet jest włączone w programie Visual Studio. Więcej informacji: [Enabling and disabling NuGet package restore (Włączanie i wyłączanie przywracania pakietów NuGet)](https://go.microsoft.com/fwlink/?linkid=846106)  

    Można również wybrać pozycję **Projekt** > **Zarządzaj pakietami NuGet**, a następnie wybrać polecenie **Przywróć**, aby ręcznie przywrócić pakiety używane w przykładzie.  

4. Naciśnij klawisz F5 lub wybierz pozycję **Debuguj** > **Rozpocznij debugowanie**.  

5. Jeśli wcześniej nie uruchamiano jednego z przykładów, należy wprowadzić informacje, aby uruchomić kod. W przeciwnym razie należy wprowadzić liczbę wystąpień, które zostały wcześniej skonfigurowane.  


   |                                 Monit                                  |                                                                                             Opis                                                                                             |
   |-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      Wprowadź nazwę i port serwera usługi Dynamics 365 [crm.dynamics.com]       | Wpisz nazwę serwera usługi Dynamics 365. Wartość domyślna to Dynamics 365 (online) (crm.dynamics.com) w Ameryce Północnej.<br /><br /> Przykład: <br />crm5.dynamics.com |
   | Czy ta organizacja jest aprowizowana w usługach online firmy Microsoft (t/n) [n] |                                                 Wpisz **t**, jeśli ta organizacja jest aprowizowana w usługach online firmy Microsoft. W przeciwnym razie wpisz **n**.                                                  |
   |                          Wprowadź domenę\nazwę użytkownika                          |                                                                                    Wpisz konto Microsoft.                                                                                     |
   |                             Wprowadź hasło                              |                      Wpisz hasło. Znaki będą wyświetlane jako symbole „\*” w oknie. Hasło zostanie bezpiecznie zapisane w Menedżerze poświadczeń firmy Microsoft do użytku w przyszłości.                       |
   |                Określ numer organizacji (1-n) [1]                 |                      Wpisz odpowiedni numer organizacji z listy organizacji, do których należysz. Wartość domyślna to 1, co oznacza pierwszą organizację na liście.                       |


6. Przykładowa aplikacja wykona operacje opisane w części [Działanie tego przykładu](#what-this-sample-does) i może zostać wyświetlony monit z dodatkowymi opcjami.  

7. Po zakończeniu przykładu naciśnij klawisz ENTER, aby zamknąć okno konsoli.  

