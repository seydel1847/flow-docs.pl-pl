## <a name="what-is-an-environment"></a>Czym jest środowisko:
Środowisko to wirtualne miejsce do przechowywania i udostępniania aplikacji, przepływów i danych biznesowych oraz zarządzania nimi w ramach usługi Common Data Service. Środowiska mają określoną lokalizację geograficzną, tak samo jak wszystkie aplikacje i dane przechowywane w bazach danych środowisk.  

## <a name="terms-you-should-get-familiar-with"></a>Terminy, które warto znać

| **Termin** | **Opis** |
| --- | --- |
| **Centrum administracyjne** |Centrum administracyjne to [portal sieci Web](https://admin.flow.microsoft.com), który umożliwia zarządzanie wszystkimi środowiskami i zasadami ochrony przed utratą danych. |
| **Common Data Service** |Usługa Common Data Service umożliwia dodawanie funkcji modelowania i magazynu danych do aplikacji. |
| **Role środowiska** |Dwie istniejące role środowiska to Administrator środowiska i Twórca środowiska. |
| **Role użytkowników** |Dwie domyślne role użytkowników to Użytkownik organizacji i Właściciel bazy danych. Możesz dodawać role i przypisywać do tych ról uprawnienia. |

## <a name="purposes-for-an-environment"></a>Przeznaczenie środowiska
Środowisk można używać w następujących celach:  

* Oddzielenie aplikacji, przepływów i danych biznesowych na podstawie różnych ról, wymagań dotyczących zabezpieczeń lub użytkowników.  
* Oddzielenie aplikacji, przepływów i danych biznesowych na podstawie lokalizacji działów lub zespołów.
* Zarządzanie środowiskami testowymi i produkcyjnymi.  

## <a name="how-to-use-environments"></a>Jak używać środowisk
Środowiska mogą służyć do różnych celów, odpowiadających potrzebom danej organizacji. Oto kilka przykładów:  

* Można tworzyć wszystkie aplikacje i przepływy w ramach jednego środowiska. 
* Można utworzyć środowiska dla różnych typów aplikacji i przepływów. Na przykład w jednym środowisku można przechowywać aplikacje testowe, a w innym aplikacje produkcyjne.  
* Dodatkowo można tworzyć środowiska na podstawie struktury organizacji, a nawet oparte na lokalizacji geograficznej działów lub zespołów. Jeśli na przykład poszczególne zespoły pracują w Australii, Meksyku i Europie, można utworzyć środowiska dla każdej z tych lokalizacji i niezależnie zarządzać nimi.  

**Uwaga**: Środowiska nie są widoczne dla użytkowników, którzy nie muszą wiedzieć, w którym środowisku się znajdują. Środowiska pozwalają administratorom kategoryzować oraz udostępniać aplikacje i przepływy używane w organizacji oraz zarządzać nimi.  

## <a name="what-are-roles"></a>Co to są role?
Osoba mająca dostęp do środowiska musi mieć przypisaną rolę **Administrator środowiska** lub **Twórca środowiska**. Administratorzy mogą wykonywać wszystkie zadania administracyjne w środowisku. Twórca może tworzyć zasoby w istniejącym środowisku. Jedna osoba może mieć przypisane obie role.  

**Uwaga**: Przyznanie wszystkim użytkownikom dostępu do usługi Microsoft Flow skutkuje przyznaniem im dostępu do środowiska domyślnego. Użytkownicy mogą mieć dostęp do wielu środowisk.  

## <a name="create-an-environment"></a>Tworzenie środowiska
Środowiska można tworzyć z poziomu [Centrum administracyjnego usługi Microsoft Flow](https://admin.flow.microsoft.com), wykonując następujące kroki:  

1. Nazwij środowisko.
2. Wybierz region, w którym będzie ono hostowane.
3. Opcjonalnie możesz utworzyć bazę danych dla danego środowiska. W razie potrzeby można utworzyć bazę danych po utworzeniu środowiska.
4. Opcjonalnie określ, kto będzie mieć dostęp do tej bazy danych. Możesz ograniczyć dostęp lub przyznać dostęp wszystkim użytkownikom. 

## <a name="add-users-to-an-environment"></a>Dodawanie użytkowników do środowiska
Po utworzeniu środowiska można dodać użytkowników z rolą Administrator środowiska lub Twórca środowiska. Można to zrobić w centrum administracyjnym, podobnie jak w przypadku wszystkich innych zadań administracyjnych.  

Po utworzeniu środowiska i dodaniu użytkowników warto również utworzyć zasady ochrony przed utratą danych (DLP) w celu ułatwienia zarządzania wykorzystaniem danych biznesowych. Omówimy to w ramach następnego tematu. 

