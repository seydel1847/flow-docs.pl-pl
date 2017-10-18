---
title: "Użycie usługi Azure Active Directory z łącznikiem niestandardowym | Microsoft Docs"
description: "Dowiedz się, jak utworzyć łącznik niestandardowy dla usługi Azure Resource Manager z uwierzytelnianiem za pomocą usługi Azure Active Directory."
services: 
suite: flow
documentationcenter: 
author: msftman
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/03/2016
ms.author: deonhe
ms.openlocfilehash: d98a3505ab7d667f5a64eed9a23041efec95b1d7
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2017
---
# <a name="use-azure-active-directory-with-a-custom-connector-in-microsoft-flow"></a>Użycie usługi Azure Active Directory z łącznikiem niestandardowym w usłudze Microsoft Flow
Usługa Azure Resource Manager (ARM) umożliwia zarządzanie składnikami rozwiązania na platformie Azure — takimi jak bazy danych, maszyny wirtualne i aplikacje sieci Web. Ten samouczek pokazuje, jak włączyć uwierzytelnianie w usłudze Azure Active Directory, zarejestrować jeden z interfejsów API usługi ARM jako łącznik niestandardowy, a następnie połączyć go z usługą Microsoft Flow. Może to być przydatne, jeśli chcesz zarządzać zasobami platformy Azure w ramach przepływu. Aby uzyskać więcej informacji na temat usługi ARM, zobacz [Omówienie usługi Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## <a name="prerequisites"></a>Wymagania wstępne
* [Subskrypcja Azure](https://azure.microsoft.com/free/).
* [Konto usługi Microsoft Flow](https://flow.microsoft.com).
* [Przykładowy plik OpenAPI](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json) używany w tym samouczku.

## <a name="enable-authentication-in-azure-active-directory"></a>Włączanie uwierzytelniania w usłudze Azure Active Directory
Po pierwsze musimy utworzyć aplikację usługi Azure Active Directory (AAD), która będzie przeprowadzać uwierzytelnianie podczas wywoływania punktu końcowego interfejsu API usługi ARM.

1. Zaloguj się do witryny [Azure Portal](https://portal.azure.com).  Jeśli masz więcej niż jedną dzierżawę usługi Azure Active Directory, upewnij się, że zalogowanie odbyło się w poprawnym katalogu. W tym celu sprawdź nazwę użytkownika w prawym górnym rogu.
   
    ![Nazwa użytkownika](./media/customapi-azure-resource-manager-tutorial/current-user.png)
2. W menu po lewej stronie kliknij pozycję **Więcej usług**.  W polu tekstowym **Filtr** wpisz **Azure Active Directory**, a następnie kliknij pozycję **Azure Active Directory**.
   
    ![Azure Active Directory](./media/customapi-azure-resource-manager-tutorial/azureaad.png)
   
    Zostanie otwarty blok Azure Active Directory.   
3. W menu w bloku Azure Active Directory kliknij pozycję **Rejestracje aplikacji**.
   
    ![Rejestracje aplikacji](./media/customapi-azure-resource-manager-tutorial/azureapplication.png)
4. Na liście zarejestrowanych aplikacji kliknij przycisk **Dodaj**.
   
    ![Przycisk Dodaj](./media/customapi-azure-resource-manager-tutorial/add-app-btn.png)   
5. Wpisz nazwę aplikacji, pozostaw wybraną opcję **Interfejs API/aplikacja sieci Web**, a następnie w polu **Adres URL logowania** wpisz `https://login.windows.net`.  Kliknij przycisk **Utwórz**.  
   
    ![Formularz nowej aplikacji](./media/customapi-azure-resource-manager-tutorial/newapplication.png)
6. Kliknij przycisk nową aplikację na liście.
   
    ![Nowa aplikacja na liście](./media/customapi-azure-resource-manager-tutorial/newapplication2.png)
   
    Zostanie otwarty blok Zarejestrowana aplikacja.  Zanotuj **identyfikator aplikacji**.  Będzie potrzebny później.
7. Powinien zostać również otwarty blok Ustawienia.  Jeśli nie, kliknij przycisk **Ustawienia**.
   
    ![Przycisk Ustawienia](./media/customapi-azure-resource-manager-tutorial/settings-btn.png)
8. W bloku Ustawienia kliknij pozycję **Adresy URL odpowiedzi**. Na liście adresów URL dodaj adres `https://msmanaged-na.consent.azure-apim.net/redirect` i kliknij przycisk **Zapisz**.
   
    ![Adresy URL odpowiedzi](./media/customapi-azure-resource-manager-tutorial/reply-urls.png)
9. Po powrocie do bloku Ustawienia kliknij pozycję **Wymagane uprawnienia**.  W bloku Wymagane uprawnienia kliknij przycisk **Dodaj**.
   
    ![Wymagane uprawnienia](./media/customapi-azure-resource-manager-tutorial/permissions.png)
   
    Zostanie otwarty blok Dodaj dostęp do interfejsu API.
10. Kliknij pozycję **Wybierz interfejs API**. W bloku, który się otworzy, kliknij opcję dotyczącą interfejsu API zarządzania usługami Azure, a następnie kliknij przycisk **Wybierz**.
    
    ![Wybór interfejsu API](./media/customapi-azure-resource-manager-tutorial/permissions2.png)
11. Kliknij przycisk **Wybierz uprawnienia**.  W obszarze *Delegowane uprawnienia* kliknij pozycję **Access Azure Service Management as organization users** (Dostęp do zarządzania usługami Azure jako użytkownicy organizacji), a następnie kliknij przycisk **Wybierz**.
    
    ![Delegowane uprawnienia](./media/customapi-azure-resource-manager-tutorial/permissions3.png)
12. W bloku Dodaj dostęp do interfejsu API kliknij przycisk **Gotowe**.
13. Po powrocie do bloku Ustawienia kliknij pozycję **Klucze**.  W bloku Klucze wpisz opis klucza, wybierz termin ważności, a następnie kliknij przycisk **Zapisz**.  Nowy klucz zostanie wyświetlony.  Zanotuj wartość klucza, która również będzie potrzebna później.  Możesz teraz zamknąć witrynę Azure Portal.
    
    ![Tworzenie klucza](./media/customapi-azure-resource-manager-tutorial/configurekeys.png)

## <a name="add-the-connection-in-microsoft-flow"></a>Dodawanie połączenia w usłudze Microsoft Flow
Teraz, gdy aplikacja usługi AAD jest skonfigurowana, dodamy łącznik niestandardowy.

1. W [aplikacji sieci Web usługi Microsoft Flow](https://flow.microsoft.com/) kliknij przycisk **Ustawienia** w prawym górnym rogu strony (wygląda jak koło zębate).  Następnie kliknij **łączniki niestandardowe**.
   
    ![Wyszukiwanie łączników niestandardowych](./media/customapi-azure-resource-manager-tutorial/finding-custom-apis.png)  
2. Kliknij pozycję **Utwórz łącznik niestandardowy**.  
   
    Zostanie wyświetlony monit o podanie właściwości interfejsu API.  
   
   | Właściwość | Opis |
   | --- | --- |
   | Nazwa |W górnej części strony kliknij opcję **Bez tytułu** i nazwij przepływ. |
   | Plik OpenAPI |Przejdź do [przykładowego pliku OpenAPI usługi ARM](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json). |
   | Przekaż ikonę interfejsu API |Kliknij przycisk **Przekaż ikonę**, aby wybrać plik obrazu ikony. Odpowiedni będzie dowolny obraz PNG lub JPG o rozmiarze mniejszym niż 1 MB. |
   | Opis |Wpisz opis łącznika niestandardowego (opcjonalnie). |
   
    ![Tworzenie łącznika niestandardowego](./media/customapi-azure-resource-manager-tutorial/create-custom-api.png)  
   
    Wybierz przycisk **Kontynuuj**.
3. Ponieważ plik OpenAPI używa naszej aplikacji usługi AAD do uwierzytelniania, na następnym ekranie musimy przekazać kilka informacji na temat naszej aplikacji do usługi Flow.  W obszarze **Identyfikator klienta** wpisz zanotowany wcześniej **identyfikator aplikacji** usługi AAD.  Podaj **klucz** jako wpis tajny klienta.  I wreszcie w polu **Adres URL zasobu** wpisz `https://management.core.windows.net/`.
   
   > [!IMPORTANT]
   > Koniecznie użyj adresu URL zasobu w takiej formie, jak podano powyżej, łącznie z ukośnikiem na końcu.
   > 
   > 
   
    ![Ustawienia OAuth](./media/customapi-azure-resource-manager-tutorial/oauth-settings.png)
   
    Po wprowadzeniu informacji o zabezpieczeniach kliknij znacznik wyboru (**&#x2713;**) obok nazwy przepływu w górnej części strony, aby utworzyć łącznik niestandardowy.
4. Łącznik niestandardowy zostanie wyświetlony w obszarze **Łączniki niestandardowe**.
   
    ![Dostępne interfejsy API](./media/customapi-azure-resource-manager-tutorial/list-custom-apis.png)  
5. Po zarejestrowaniu łącznika niestandardowego należy utworzyć połączenie z nim do użytku w aplikacjach i przepływach.  Kliknij przycisk **+** z prawej strony nazwy łącznika niestandardowego, a następnie wypełnij pola ekranu logowania.

> [!NOTE]
> Przykładowy plik OpenAPI nie definiuje pełnego zestawu operacji usługi ARM i obecnie zawiera tylko operację [wyświetlenia listy wszystkich subskrypcji](https://msdn.microsoft.com/library/azure/dn790531.aspx).  Możesz zmodyfikować ten plik OpenAPI lub utworzyć inny plik OpenAPI za pomocą [edytora online plików OpenAPI](http://editor.swagger.io/).
> 
> Proces ten może służyć do dostępu do dowolnego interfejsu API RESTful uwierzytelnianego przy użyciu usługi AAD.
> 
> 

## <a name="next-steps"></a>Następne kroki
Aby uzyskać szczegółowe informacje o sposobie tworzenia przepływu, zobacz artykuł [Rozpocznij tworzenie z usługą Microsoft Flow](get-started-logic-flow.md).

Aby zadawać pytania lub publikować komentarze dotyczące łączników niestandardowych, [dołącz do naszej społeczności](https://aka.ms/flow-community).

