---
title: Wprowadzenie do tokenów wyzwalacza przycisku | Microsoft Docs
description: Wprowadzenie do tokenów wyzwalacza przycisku dla przepływów przycisku firmy Microsoft.
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
ms.date: 12/12/2016
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: dc1b93553938221c3f1c995b63b984cfff913c06
ms.sourcegitcommit: ffed9f02092fbd19fc4108aee05dd40d1a2a3755
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711616"
---
# <a name="get-started-with-button-trigger-tokens"></a>Rozpoczynanie pracy z tokenami wyzwalacza przycisku
## <a name="what-are-button-trigger-tokens"></a>Co to są tokeny wyzwalacza przycisku?
Tokeny wyzwalacza przycisku to punkty danych znane i dostępne dla urządzenia, na którym jest uruchomiony [przepływ przycisku](introduction-to-button-flows.md). Te tokeny zmieniają się na podstawie czynników takich jak bieżący czas lub lokalizacja geograficzna urządzenia w danym momencie.  

Jeśli na przykład uruchomisz przepływ przycisku na smartfonie, prawdopodobnie **będzie on miał informacje o czasie** w bieżącej lokalizacji, a także o dacie i Twoim obecnym adresie. W tym kontekście godzina, data i adres lokalizacji telefonu są określane w czasie uruchamiania przepływu przycisku. Są one automatycznie dostępne do użycia we wszystkich przepływach przycisku wykonywanych na urządzeniu. Tokeny wyzwalacza umożliwiają tworzenie przydatnych przepływów minimalizujących konieczność wykonywania powtarzających się czynności, takich jak podawanie swojej lokalizacji innej osobie lub śledzenie ilości czasu spędzonego nad konkretnym zadaniem lub podczas rozmowy serwisowej.

### <a name="list-of-button-trigger-tokens"></a>Lista tokenów wyzwalacza przycisku
Oto lista tokenów wyzwalacza przycisku, które są dostępne do użycia podczas tworzenia przepływów przycisku.

| Parametr | Opis |
| --- | --- |
| Miasto |Miasto, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Kraj/region |Kraj/region, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Pełny adres |Pełny adres lokalizacji, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Szerokość geograficzna |Szerokość geograficzna lokalizacji, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Długość geograficzna |Długość geograficzna lokalizacji, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Kod pocztowy |Kod pocztowy lokalizacji, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Stan |Stan, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Ulica |Ulica, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Sygnatura czasowa |Czas w lokalizacji, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Data |Data w lokalizacji, gdzie znajduje się urządzenie, na którym działa przepływ. |
| Nazwa użytkownika |Nazwa użytkownika osoby zalogowanej na urządzeniu, na którym działa przepływ. |
| Adres e-mail użytkownika |Adres e-mail osoby zalogowanej na urządzeniu, na którym działa przepływ. |

## <a name="create-a-button-flow-that-uses-trigger-tokens"></a>Tworzenie przepływu przycisku korzystającego z tokenów wyzwalacza
Podczas tworzenia przycisku możesz użyć tokenów wyzwalacza, aby dodać zaawansowane funkcje do przycisku.

W tym przewodniku utworzymy przepływ przycisku na urządzeniu z systemem Android. Przepływ przycisku będzie używać tokenów wyzwalacza do wysyłania daty i pełnego adresu w wiadomości e-mail do szefa „**Praca z domu**”.

W tym przewodniku zobaczysz zrzuty ekranu urządzenia z systemem Android, jednak cały proces przebiega w podobny sposób na urządzeniach z systemem iOS i Windows Phone.

### <a name="prerequisites"></a>Wymagania wstępne
* Służbowy adres e-mail lub [konto Microsoft](https://account.microsoft.com/about?refd=www.microsoft.com) z dostępem do usługi Microsoft Flow.
* Aplikacja mobilna usługi Microsoft Flow dla systemu [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) lub [Windows Phone](https://aka.ms/flowmobilewindows).

Zaczynajmy:

1. Uruchom aplikację Flow i wybierz pozycję **Przeglądaj**   
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/1.png)  
2. Wybierz usługę **Wyślij wiadomość e-mail „Dzisiaj pracuję z domu” do menedżera** w kategorii **Przycisk**   
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/2.png)  
3. Wybierz przycisk **UŻYJ TEGO SZABLONU**  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/3.png)  
4. Wybierz pozycję **Edytuj** na karcie **Wyślij wiadomość e-mail**  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/3-5.png)  
5. Naciśnij pole tekstowe **Temat** i wpisz w nim ciąg: „**dzisiaj —**” po tekście „Praca z domu”. Zauważ, że po naciśnięciu pola tekstowego została również otworzona lista parametrów/tokenów. Użyjemy jednego z tych tokenów w następnym kroku do dodania daty do tematu wiadomości e-mail.  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/4.png)  
6. Pozostaw kursor w polu tekstowym tematu, przewiń do listy parametrów **ręczne** i naciśnij pozycję **Data**. Zauważ, że parametr daty znajduje się teraz w polu tekstowym **Temat**:  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/6.png)  
7. Przewiń do pola tekstowego **Treść** i naciśnij w miejscu po wiadomości domyślnej, aby umieścić w tym miejscu dodatkowe tokeny.  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/7.png)  
8. Naciśnij parametr **Pełny adres**, a następnie naciśnij pozycję **Utwórz**  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/8.png)  
9. Naciśnij pozycję **Gotowe**. Przepływ przycisku jest gotowy.  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/9.png)  

## <a name="run-the-button-flow"></a>Uruchamianie przepływu przycisku
**UWAGA**: ten przepływ przycisku wyśle Twoją bieżącą lokalizacji za pośrednictwem poczty e-mail.  

1. Naciśnij kategorię **Przyciski** w dolnej części ekranu. Zobaczysz listę przycisków, dla których masz uprawnienia do użycia. Naciśnij przycisk reprezentujący właśnie utworzony przepływ przycisku:  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/10.png)  
2. Naciśnij pozycję **ZEZWÓL**, aby zezwolić przepływowi przycisku na dostęp do informacji o lokalizacji urządzenia:  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/11.png)  
3. Wiadomość e-mail zostanie wysłana do szefa w ciągu kilku chwil:  
   ![token wyzwalacza przycisku](./media/introduction-to-button-trigger-tokens/12.png)  

Gratulacje, właśnie został utworzony przepływ przycisku, który używa tokenów wyzwalacza zarówno daty, jak i pełnego adresu. 

## <a name="next-steps"></a>Następne kroki
* [Udostępnianie przepływów przycisków](share-buttons.md)
* [Więcej informacji na temat przepływów przycisku](introduction-to-button-flows.md)
