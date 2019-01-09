# <a name="microsoft-flow-web-api"></a>Internetowy interfejs API usługi Microsoft Flow

Od tej pory wszystkie przepływy będą przechowywane w usłudze Common Data Service (CDS) for Apps i będą korzystać z [zaawansowanego internetowego interfejsu API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/perform-operations-web-api).

W tym temacie omówiono zarządzanie przepływami zawartymi na karcie **Rozwiązania** w usłudze Microsoft Flow. Obecnie przepływy w obszarze **Moje przepływy** nie są obsługiwane przez te interfejsy API.

## <a name="compose-http-requests"></a>Tworzenie żądań HTTP

Aby rozpocząć tworzenie żądań, należy najpierw skonstruować adres URL. Format podstawowego adresu URL internetowego interfejsu API usługi Microsoft Flow to: `https://{Organization ID}.{Regional Subdomain}.dynamics.com/api/data/v9.1/`. Dwa parametry to:

- **Organization ID** (Identyfikator organizacji) to unikatowa nazwa środowiska, które przechowuje Twoje przepływy. Identyfikator organizacji można zobaczyć w przełączniku środowiska w prawym górnym rogu usługi Microsoft Flow. Pamiętaj, że parametr **Organization ID** (Identyfikator organizacji) jest inny niż **Environment ID** (Identyfikator środowiska), który jest identyfikatorem GUID widocznym w adresie URL przepływu.

     ![Przełącznik środowiska](media/web-api/get-organization-id.png "Przełącznik środowiska")

- **Poddomena regionalna** zależy od lokalizacji środowiska. Po zalogowaniu się w usłudze Microsoft Flow można zobaczyć region środowiska w adresie URL strony internetowej. Użyj tej nazwy regionu do znalezienia odpowiedniej poddomeny w poniższej tabeli:

     ![Adres URL przepływu](media/web-api/get-region-name.png "Adres URL przepływu")

     | Region         | Poddomena   |
     | -------------- | ----------- |
     | Stany Zjednoczone  | crm         |
     | Ameryka Południowa  | crm2        |
     | Kanada         | crm3        |
     | Europa         | crm4        |
     | Azja i Pacyfik   | crm5        |
     | Australia      | crm6        |
     | Japonia          | crm7        |
     | Indie          | crm8        |
     | US Government  | crm9        |
     | Zjednoczone Królestwo | crm11       |

Można też programowo pobrać listę dostępnych wystąpień przy użyciu metody [Get Instances](https://docs.microsoft.com/rest/api/admin.services.crm.dynamics.com/instances/getinstances) (Pobierz wystąpienia) w interfejsie API zarządzania online.

Każde żądanie do internetowego interfejsu API musi mieć ustawione nagłówki `Accept` i `Content-type` na wartość `application/json`.

Na koniec wypełnij nagłówek `Authorization` tokenem elementu nośnego usługi Azure AD. Możesz [dowiedzieć się](https://docs.microsoft.com/dynamics365/customer-engagement/developer/authenticate-users), jak uzyskać token elementu nośnego usługi Azure AD dla usługi CDS for Apps. Na przykład to żądanie:

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows
Accept: application/json
Authorization: Bearer ey...
```

Odpowiedź zawiera listę przepływów w obrębie tego środowiska:

```http
{
    "@odata.context": "https://org00000000.crm0.dynamics.com/api/data/v9.1/$metadata#workflows",
    "value": [{
        "@odata.etag": "W/\"12116760\"",
        "category": 5,
        "statecode": 0,
        "workflowidunique": "00000000-0000-0000-0000-000000000001",
        "workflowid" : "00000000-0000-0000-0000-000000000002",
        "createdon": "2018-11-15T19:45:51Z",
        "_ownerid_value": "00000000-0000-0000-0000-000000000003",
        "modifiedon": "2018-11-15T19:45:51Z",
        "ismanaged": false,
        "name": "Sample flow",
        "_modifiedby_value": "00000000-0000-0000-0000-000000000003",
        "_createdby_value": "00000000-0000-0000-0000-000000000003",
        "type": 1,
        "description": "This flow updates some data in CDS for Apps.",
        "clientdata": "{\"properties\":{\"connectionReferences\":{\"shared_commondataservice\":{\"source\":\"NotSpecified\",\"id\":\"/providers/Microsoft.PowerApps/apis/shared_commondataservice\",\"tier\":\"NotSpecified\"}},\"definition\":{...}},\"schemaVersion\":\"1.0.0.0\"}"
    }]
}
```

## <a name="list-flows"></a>Pobieranie listy przepływów

Jak pokazano powyżej, możesz pobrać listę przepływów pracy, wywołując metodę `GET` w elemencie `workflows`. Każdy przepływ pracy ma wiele właściwości, ale najistotniejsze to:

| Nazwa właściwości     | Opis                                              |
| ----------------- | -------------------------------------------------------- |
| category          | Kategoria przepływu. Różne typy to: 0 — klasyczne przepływy pracy usługi CDS for Apps, 1 — klasyczne okna dialogowe usługi CDS for Apps, 2 — reguły biznesowe, 3 — klasyczne akcje usługi CDS for Apps, 4 — przepływy procesów biznesowych i 5 — zautomatyzowane, natychmiastowe lub zaplanowane przepływy. |
| statecode         | Stan przepływu. Możliwe stany to **0** — wyłączony lub **1** — włączony.|
| workflowuniqueid  | Unikatowy identyfikator dla tej instalacji przepływu. |
| workflowid        | Unikatowy identyfikator dla przepływu we wszystkich importach. |
| createdon         | Data utworzenia przepływu. |
| _ownerid_value    | Unikatowy identyfikator użytkownika lub zespołu będącego właścicielem przepływu. Jest to identyfikator z jednostki systemusers w usłudze CDS for Apps. |
| modifiedon        | Czas ostatniej aktualizacji przepływu. |
| ismanaged         | Wskazuje, czy przepływ został zainstalowany przy użyciu rozwiązania zarządzanego. |
| name              | Nazwa wyświetlana nadana przepływowi przez Ciebie. |
| _modifiedby_value | Ostatni użytkownik, który zaktualizował przepływ. Jest to identyfikator z jednostki systemusers w usłudze CDS for Apps. |
| _createdby_value  | Użytkownik, który utworzył przepływ. Jest to identyfikator z jednostki systemusers w usłudze CDS for Apps. |
| type              | Wskazuje, czy przepływ to uruchomiony przepływ, czy szablon, którego można użyć do tworzenia dodatkowych przepływów. 1 — przepływ, 2 — aktywacja lub 3 — szablon. |
| description       | Podany przez użytkownika opis przepływu. |
| clientdata        | Zakodowany w ciągu format JSON obiektu, który zawiera odwołania połączenia i definicję przepływu. |

Możesz również zażądać konkretnych właściwości, przefiltrować listę przepływów i nie tylko, jak opisano w [dokumentacji interfejsu API usługi CDS for Apps dotyczącej wykonywania zapytań na danych](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/query-data-web-api). Na przykład to zapytanie zwraca tylko zautomatyzowane, natychmiastowe lub zaplanowane przepływy, które są obecnie włączone:

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows?$filter=category eq 5 and statecode eq 1
Accept: application/json
Authorization: Bearer ey...
```

## <a name="create-a-flow"></a>Utwórz przepływ

Wywołaj metodę `POST` w kolekcji `workflows`, aby utworzyć przepływ. Wymagane właściwości zautomatyzowanych, natychmiastowych i zaplanowanych przepływów to: category (kategoria), name (nazwa), type (typ), primaryentity (encja podstawowa) i clientdata (dane klienta). Użyj wartości `none` dla właściwości primaryentity w przypadku tych typów przepływów.

Możesz również podać właściwości description (opis) i statecode (kod stanu).

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
        "category": 5,
        "statecode": 0,
        "name": "Sample flow name",
        "type": 1,
        "description": "This flow reads some data from CDS for Apps.",
        "primaryentity":"none",
        "clientdata": "{\"properties\":{\"connectionReferences\":{\"shared_commondataservice\":{\"connectionName\":\"shared-commondataser-00000000-0000-0000-0000-000000000004\",\"source\":\"Invoker\",\"id\":\"/providers/Microsoft.PowerApps/apis/shared_commondataservice\"}},\"definition\":{\"$schema\": \"https:\/\/schema.management.azure.com\/providers\/Microsoft.Logic\/schemas\/2016-06-01\/workflowdefinition.json#\",\"contentVersion\": \"1.0.0.0\",\"parameters\": {\"$connections\": {\"defaultValue\": {},\"type\": \"Object\"},\"$authentication\": {\"defaultValue\": {},\"type\": \"SecureObject\"}},\"triggers\": {\"Recurrence\": {\"recurrence\": {\"frequency\": \"Minute\",\"interval\": 1},\"type\": \"Recurrence\"}},\"actions\": {\"List_records\": {\"runAfter\": {},\"metadata\": {\"flowSystemMetadata\": {\"swaggerOperationId\": \"GetItems_V2\"}},\"type\": \"ApiConnection\",\"inputs\": {\"host\": {\"api\": {\"runtimeUrl\": \"https:\/\/firstrelease-001.azure-apim.net\/apim\/commondataservice\"},\"connection\": {\"name\": \"@parameters('$connections')['shared_commondataservice']['connectionId']\"}},\"method\": \"get\",\"path\": \"\/v2\/datasets\/@{encodeURIComponent(encodeURIComponent('default.cds'))}\/tables\/@{encodeURIComponent(encodeURIComponent('accounts'))}\/items\",\"queries\": {\"$top\": 1},\"authentication\": \"@parameters('$authentication')\"}}},\"outputs\": {}}},\"schemaVersion\":\"1.0.0.0\"}"
}
```

Najważniejsza sekcja to `clientdata`, która zawiera odwołania przepływu używane przez przepływ, oraz [definition](https://docs.microsoft.com/azure/logic-apps/logic-apps-workflow-definition-language) (definicja) przepływu. Odwołania przepływu to mapowania do każdego połączenia używanego w przepływie.

Dostępne są trzy właściwości:

| Nazwa właściwości  | Opis                                                 |
| -------------- | ----------------------------------------------------------- |
| connectionName | Określa połączenie. Właściwość connectionName można wyświetlić, przechodząc do strony **Połączenia**, a następnie kopiując ją z adresu URL połączenia. |
| source         | Wartość `Embedded` lub `Invoker`. Wartość `Invoker` obowiązuje tylko w przypadku przepływów natychmiastowych (tych, w których użytkownik wybiera przycisk, aby uruchomić przepływ) oraz wskazuje, że użytkownik końcowy udostępni połączenie. W tym przypadku właściwość connectionName jest używana tylko w czasie projektowania. Jeśli połączenie ma wartość `Embedded`, oznacza to, że jest zawsze używana określona przez Ciebie właściwość connectionName. |
| id             | Identyfikator łącznika. Identyfikator zawsze zaczyna się od ciągu `/providers/Microsoft.PowerApps/apis/`, a następnie zawiera nazwę łącznika, którą można skopiować z adresu URL połączenia lub wybierając łącznik ze strony **Łączniki**. |

Po wykonaniu żądania `POST` otrzymasz nagłówek `OData-EntityId`, który będzie zawierać właściwość `workflowid` dla nowego przepływu.

## <a name="update-a-flow"></a>Aktualizowanie przepływu

Możesz wywołać metodę `PATCH` w przepływie pracy, aby zaktualizować, włączyć lub wyłączyć przepływ. Użyj właściwości `workflowid` do nawiązywania tych wywołań. Na przykład możesz zaktualizować opis i właściciela przepływu przy użyciu następującego wywołania:

```http
PATCH https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows(00000000-0000-0000-0000-000000000002)
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "description" : "This flow will ensure consistency across systems.",
    "ownerid@odata.bind": "systemusers(00000000-0000-0000-0000-000000000005)",
}
```

> [!NOTE]
> W składni zmieniania właściciela jest używany format `odata.bind`. Oznacza to, że zamiast stosowania poprawek \_pola ownerid_value bezpośrednio, możesz dołączyć właściwość `@odata.bind` do nazwy właściwości, a następnie opakować identyfikator za pomocą funkcji `systemusers()`.

W kolejnym przykładzie można włączyć przepływ przy użyciu tego wywołania:

```http
PATCH https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows(00000000-0000-0000-0000-000000000002)
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "statecode" : 1
}
```

### <a name="delete-a-flow"></a>Usuwanie przepływu

Usuń przepływ przy użyciu prostego wywołania `DELETE`:

```http
DELETE https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows(00000000-0000-0000-0000-000000000002)
Accept: application/json
Authorization: Bearer ey...
```

> [!NOTE]
> Nie można usunąć przepływu, który jest włączony. Należy najpierw wyłączyć przepływ (zobacz **Aktualizowanie przepływu** wcześniej) lub w przeciwnym razie zostanie wyświetlony następujący błąd: `Cannot delete an active workflow definition.`

## <a name="get-all-users-with-whom-a-flow-is-shared"></a>Uzyskiwanie listy wszystkich użytkowników, którym udostępniono przepływ

Do pobierania listy użytkowników mających dostęp jest używana *funkcja* w usłudze CDS for Apps. Ta funkcja przyjmuje pojedynczy parametr `Target`:

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/RetrieveSharedPrincipalsAndAccess(Target=@tid)?@tid={'@odata.id':'workflows(00000000-0000-0000-0000-000000000002)'}
Accept: application/json
Authorization: Bearer ey...
```

Parametr `Target` to ciąg w formacie JSON z pojedynczą właściwością o nazwie `@odata.id`. Zastąp identyfikator przepływu pracy w powyższym przykładzie. Zostanie zwrócona następująca wartość:

```http
{
    "@odata.context": "https://org00000000.crm0.dynamics.com/api/data/v9.1/$metadata#Microsoft.Dynamics.CRM.RetrieveSharedPrincipalsAndAccessResponse",
    "PrincipalAccesses": [
        {
            "AccessMask": "ReadAccess",
            "Principal": {
                "@odata.type": "#Microsoft.Dynamics.CRM.systemuser",
                "ownerid": "00000000-0000-0000-0000-000000000005"
            }
        }
    ]
}
```

## <a name="share-or-unshare-a-flow"></a>Udostępnianie lub anulowanie udostępniania przepływu

Możesz udostępnić przepływ używając akcji `GrantAccess`.

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/GrantAccess
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "Target" : {
        "@odata.type": "Microsoft.Dynamics.CRM.workflow",
        "workflowid" : "00000000-0000-0000-0000-000000000002"
    },
    "PrincipalAccess": {
        "Principal": {
            "@odata.type" : "Microsoft.Dynamics.CRM.systemuser",
            "ownerid" : "00000000-0000-0000-0000-000000000005"
        },
        "AccessMask": "ReadAccess"
    }
}
```

Parametr `AccessMask` to pole z następującymi wartościami dla różnych poziomów uprawnień:

| Nazwa         | Opis                                          |
| ------------ | ---------------------------------------------------- |
| None         | Brak dostępu.                                           |
| ReadAccess   | Uprawnienie do odczytywania przepływu.                          |
| WriteAccess  | Uprawnienie do aktualizowania przepływu.                        |
| DeleteAccess | Uprawnienie do usuwania przepływu.                        |
| ShareAccess  | Uprawnienie do udostępniania przepływu.                         |
| AssignAccess | Uprawnienie do zmieniania właściciela przepływu.           |

Uprawnienia możesz połączyć przy użyciu przecinka, na przykład zapewniając możliwość odczytywania i aktualizowania przepływu, podając wartość `ReadAccess,WriteAccess`.

Możesz *anulować udostępnianie* przepływu przy użyciu akcji `RevokeAccess`. Oto przykład:

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/RevokeAccess
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "Target" : {
        "@odata.type": "Microsoft.Dynamics.CRM.workflow",
        "workflowid" : "00000000-0000-0000-0000-000000000002"
    },
    "Revokee": {
        "@odata.type" : "Microsoft.Dynamics.CRM.systemuser",
        "ownerid" : "00000000-0000-0000-0000-000000000005"
    }
}
```

Akcja `RevokeAccess` usuwa wszystkie uprawnienia udzielone w akcji `AccessMask`.

## <a name="export-flows"></a>Eksportowanie przepływów

Użyj akcji `ExportSolution`, aby wyeksportować przepływy do pliku zip. Najpierw dodaj odpowiednie przepływy do [rozwiązania](https://flow.microsoft.com/blog/solutions-in-microsoft-flow/).

Gdy przepływ będzie w rozwiązaniu, wywołaj następującą akcję:

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/ExportSolution
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "SolutionName" : "Awesome solution 1",
    "Managed": false
}
```

Akcja `ExportSolution` zwraca ciąg zakodowany algorytmem base-64 we właściwości `ExportSoutionFile`.

```http
{
    "@odata.context": "https://org00000000.crm0.dynamics.com/api/data/v9.1/$metadata#Microsoft.Dynamics.CRM.ExportSolutionResponse",
    "ExportSolutionFile": "UEsDBBQAAgAI..."
}
```

Następnie możesz zapisać ten plik w kontroli kodu źródłowego i/lub używać dowolnego systemu dystrybucji lub zarządzania wersjami.

## <a name="import-flows"></a>Importowanie przepływów

Wywołaj akcję `ImportSolution`, aby zaimportować rozwiązanie.

| Nazwa właściwości                    | Opis                               |
| -------------------------------- | ----------------------------------------- |
| OverwriteUnmanagedCustomizations | Jeśli istnieją wystąpienia tych przepływów w usłudze CDS for Apps, tę flagę należy ustawić na wartość `true`, aby je zaimportować. W przeciwnym razie nie zostaną one zastąpione. |
| PublishWorkflows                 | Wskazuje, czy klasyczne przepływy pracy usługi CDS for Apps zostaną aktywowane przy importowaniu. To ustawienie nie ma zastosowania do innych typów przepływów. |
| ImportJobId                      | Oferuje nowy, unikatowy identyfikator GUID do śledzenia zadania importu. |
| CustomizationFile                | Plik zip zakodowany algorytmem base-64, który zawiera rozwiązanie. |

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/ImportSolution
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "OverwriteUnmanagedCustomizations": false,
    "PublishWorkflows" : true,
    "ImportJobId" : "00000000-0000-0000-0000-000000000006",
    "CustomizationFile" : "UEsDBBQAAgAI..."
}
```

Ponieważ importowanie to długotrwała operacja, odpowiedzią na akcję ImportSolution będzie wartość `204 No content`. Aby śledzić postęp, wywołaj metodę `GET` na obiekcie `importjobs` pod warunkiem, że wartość `ImportJobId` została uwzględniona w oryginalnej akcji `ImportSolution`.

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/importjobs(00000000-0000-0000-0000-000000000006)
Accept: application/json
Authorization: Bearer ey...
```

To wywołanie zwróci stan operacji importowania, w tym `progress` (procent ukończenia), `startedon` i `completedon` (jeśli importowanie zostało zakończone).

Po pomyślnym zakończeniu importowania musisz skonfigurować połączenia dla przepływu, ponieważ wartość `connectionNames` będzie prawdopodobnie inna w środowisku docelowym (jeśli w ogóle istnieją połączenia). Jeśli konfigurujesz nowe połączenia w środowisku docelowym, właściciel przepływów musi utworzyć je w projektancie usługi Microsoft Flow. Jeśli połączenia są już skonfigurowane w nowym środowisku, możesz wywołać metodę `PATCH` dla właściwości `clientData` przepływu, używając nazw połączeń.
