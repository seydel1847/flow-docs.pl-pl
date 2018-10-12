---
title: Praca z przepływami procesów biznesowych przy użyciu kodu | MicrosoftDocs
description: Dowiedz się, jak programowo pracować z przepływami procesów biznesowych, aby tworzyć bardziej efektywne i usprawnione procesy biznesowe.
ms.custom: ''
ms.date: 07/09/2018
ms.reviewer: ''
ms.service: flow
ms.topic: article
ms.assetid: 67d8cf80-9f77-4804-97a1-cf9f61417e83
author: msftman
ms.author: deonhe
manager: kvivek
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: ae3633047bda556058c8e2ec94e6411e7f277e76
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691071"
---
# <a name="work-with-business-process-flows-using-code"></a>Praca z przepływami procesów biznesowych przy użyciu kodu

*Przepływ procesów biznesowych* umożliwia tworzenie bardziej efektywnych i usprawnionych procesów sprzedaży, usług i innych procesów biznesowych. Tworzy wizualizację procesu biznesowego, umieszczając specjalne kontrolki w górnej części formularzy jednostek. Użytkownicy są prowadzeni przez różne etapy procesów sprzedaży, marketingu i usług w kierunku ukończenia. Każdy proces obsługuje wiele etapów i kroków. Można dodawać lub usuwać kroki, zmieniać kolejność etapów lub dodawać nowe jednostki do przepływu procesów biznesowych.  
  
Różne wystąpienia przepływu procesów biznesowych mogą być uruchamiane jednocześnie dla tego samego rekordu jednostki. Użytkownicy mogą przełączać się między wystąpieniami współbieżnych procesów biznesowych i wznawiać swoją pracę na bieżącym etapie procesu. 

W tym temacie opisano sposób programowej pracy z przepływami procesów biznesowych.

> [!NOTE]
> Praca z przepływami procesów biznesowych nie wymaga pisania kodu. Aby uzyskać więcej informacji na temat tworzenia przepływów procesów biznesowych i zarządzania nimi przy użyciu interfejsu użytkownika, zobacz [Omówienie przepływów procesów biznesowych](../business-process-flows-overview.md)  

<a name="PrereqsBPF"></a>   
## <a name="prerequisites-for-business-process-flow"></a>Wymagania wstępne dotyczące przepływu procesów biznesowych 

Jednostki niestandardowe oraz jednostki mające zaktualizowane formularze interfejsu użytkownika mogą być częścią przepływu procesów biznesowych. Zaktualizowane jednostki interfejsu użytkownika mają właściwość <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAIRUpdated> o wartości `true`. 

Aby włączyć jednostkę do przepływu procesów biznesowych, dla właściwości <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsBusinessProcessEnabled> ustaw wartość `true`.

> [!IMPORTANT]
>  Włączenie jednostki do przepływu procesów biznesowych jest procesem jednokierunkowym. Nie można go cofnąć.

   
<a name="DefineBPF"></a>   
## <a name="define-business-process-flow"></a>Definiowanie przepływu procesów biznesowych
  
Użyj wizualnego kreatora procesów biznesowych, aby zdefiniować przepływ procesów biznesowych. Więcej informacji: [Tworzenie przepływu procesów biznesowych](../create-business-process-flow.md)

Domyślnie przepływ procesów biznesowych jest tworzony w stanie `Draft`.  

Definicja przepływu procesów biznesowych jest przechowywana w jednostce <xref:Microsoft.Dynamics.CRM.workflow>, a informacje o etapach przepływu procesów biznesowych są przechowywane w jednostce <xref:Microsoft.Dynamics.CRM.processstage>.
  
<a name="ActivateBPF"></a>   
## <a name="activate-business-process-flow"></a>Aktywowanie przepływu procesów biznesowych  
 Aby móc użyć przepływu procesów, należy go uaktywnić. Aby uaktywnić przepływ, musisz mieć uprawnienia `prvActivateBusinessProcessFlow` dla jednostki `Workflow`. Użyj komunikatu <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>, aby ustawić stan rekordu jednostki `Workflow` na `Activated`. Więcej informacji: [Wykonywanie wyspecjalizowanych operacji przy użyciu metody Update](/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update) 

 > [!NOTE]
 > Przepływ procesów biznesowych można również uaktywnić przy użyciu kreatora przepływu procesów biznesowych. 

<a name="BPFEntity"></a>   
## <a name="business-process-flow-entity"></a>Jednostka przepływu procesów biznesowych 
 Po uaktywnieniu definicji przepływu procesów biznesowych przez zmianę odpowiedniego rekordu jednostki `Workflow` lub przy użyciu kreatora przepływu procesów biznesowych automatycznie tworzona jest niestandardowa jednostka o następującej nazwie służąca do przechowywania uaktywnionych wystąpień przepływu procesów biznesowych: „*\<prefiks_aktywnego_rozwiazania>*_*\<unikatowa_nazwa>*”, gdzie wartość unikatowa_nazwa pochodzi od podanej przez Ciebie nazwy.  
  
 Jeśli na przykład określisz „Niestandardowy PPB” jako nazwę definicji przepływu procesów biznesowych i używasz domyślnego wydawcy (nowego) dla aktywnego rozwiązania, nazwa niestandardowej jednostki utworzonej w celu przetwarzania wystąpień procesów będzie mieć postać „nowy_niestandardowyppb”.  
  
 Jeśli wartość `uniquename` nie jest dostępna dla definicji przepływu procesów biznesowych, na przykład jeśli przepływ procesów biznesowych został zaimportowany jako część rozwiązania z wcześniejszej wersji, domyślną nazwą jednostki niestandardowej będzie „*\<prefiks_aktywnego_rozwiazania>*\_bpf\_*<identyfikator_GUID_definicji_PPB>*:  
  
> [!IMPORTANT]
>  W przykładowych rekordach przepływów procesów biznesowych jednostki systemowe są używane do przechowywania odpowiednich rekordów wystąpień przepływów procesów biznesowych.  
>   
>  Jednak we wszystkich nowo utworzonych definicjach przepływów procesów biznesowych jednostki niestandardowe będą używane do przechowywania rekordów wystąpień, jak wyjaśniono wcześniej. 

Nazwę jednostki przepływu procesów biznesowych można pobrać na jeden z następujących sposobów:

- **Za pomocą interfejsu użytkownika**: użyj interfejsu użytkownika dostosowywania, aby przeglądać jednostkę przepływu procesów biznesowych:

    ![](media/bpf-entity-name.png)
- **Za pomocą internetowego interfejsu API**: użyj następującego żądania:

    **Żądanie**

    ```
    GET [Organization URI]/api/data/v9.0/workflows?$filter=name eq 'My Custom BPF'&$select=uniquename HTTP/1.1
    ```

    **Odpowiedź**
    ```
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#workflows(uniquename)",
    "value":[  
         {  
             "@odata.etag":"W/\"1084677\"",
             "uniquename":"new_mycustombpf",
             "workflowid":"2669927e-8ad6-4f95-8a9a-f1008af6956f"
         }
      ]
    }

- **Using the Organization service**: Use the following code sample:

    ```c#
    QueryExpression query = new QueryExpression
    {
        EntityName = "workflow",
        ColumnSet = new ColumnSet("uniquename"),
        Criteria = new FilterExpression
        {
            Conditions =
            {
                new ConditionExpression
                {
                    AttributeName = "name",
                    Operator = ConditionOperator.Equal,
                    Values = { "My Custom BPF" }
                }
            }
        }
    };
    Workflow Bpf = (Workflow)_serviceProxy.RetrieveMultiple(query).Entities[0]; 

> [!NOTE]
> The <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsBPFEntity> property is `true` for business process flow entities. You can retrieve all the business process flow entities in your instance by running the following Web API request:
> ```http
> GET [Organization URI]/api/data/v9.0/EntityDefinitions?$select=SchemaName,LogicalName,DisplayName&$filter=IsBPFEntity eq true HTTP/1.1
> ```

<a name="BPFSecurity"></a>   
## Manage security for business process flows

The custom entity that is automatically created on activating a business process flow to store business process flow instances adheres to the standard security model as for any other custom entity in Customer Engagement. This implies that privileges granted on these entities define the runtime permissions for users for business process flows.

The custom business process flow entity has organization scope. The regular create, retrieve, update and delete privileges on this entity define the permission the user would have based on his/her assigned roles. By default, when the business process flow custom entity is created, only **System Administrator** and **System Customizer** security roles are granted access to it, and you must explicitly grant permissions to the new business process flow entity (for example, **My Custom BPF**) for other security roles as required.

![](media/bpf-privileges.png)

<a name="ManageBPF"></a>   
## Create, retrieve, update, and delete business process flow entity records (process instances)  
 The custom entity that is automatically created on activating a business process flow definition stores all the process instances for the business process flow definition. The custom entity supports the standard programmatic creation and management of records (process instances) using Web API and CRM 2011 endpoint.

> [!IMPORTANT]
> Switching to another process instance for an entity record is only supported through UI (client) or programmatically using information available in this section. You can no longer use the `SetProcess` message (<xref href="Microsoft.Dynamics.CRM.SetProcess?text=SetProcess Action" /> or <xref:Microsoft.Crm.Sdk.Messages.SetProcessRequest>) to programmatically switch processes (set another business process flow as the active process instance) for the target entity record. 

 Lets consider the following example where we have a cross-entity business process flow, "My Custom BPF," with 3 stages: S1:Account, S2:Account, and S3:Contact. 

 ![](media/sample-bpf.png)
 
### Retrieve all the records (instances) for a business process flow entity
 If the name of your business process flow entity is "new_mycustombpf", use the following query to retrieve all the records (process instances) for your business process flow entity:  
  
```http
GET [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
```

Na tym etapie można nie uzyskać żadnych wystąpień w odpowiedzi, ponieważ nie istnieją. Uruchom to żądanie po utworzeniu wystąpienia definicji przepływu procesów biznesowych w dalszej części tego tematu.

> [!NOTE]
> Informacje na temat sposobu pobierania nazwy jednostki przepływu procesów biznesowych można znaleźć w poprzedniej sekcji [Jednostka przepływu procesów biznesowych](#business-process-flow-entity).
  
### <a name="create-a-business-process-flow-entity-record-process-instance"></a>Tworzenie rekordu jednostki przepływu procesów biznesowych (wystąpienie procesu) 

Utwórz rekord jednostki przepływu procesów biznesowych (wystąpienie procesu) programowo, jeśli chcesz przełączyć się na inny przepływ procesów biznesowych dla rekordu jednostki bez użycia interfejsu użytkownika. 

Aby utworzyć rekord jednostki przepływu procesów biznesowych, należy określić następujące wartości: 
- Powiąż rekord jednostki przepływu procesów biznesowych z głównym rekordem jednostki, ustawiając jednowartościową właściwość nawigacji przy użyciu adnotacji `@odata.bind`. Aby sprawdzić nazwę właściwości nawigacji, która wskazuje główny rekord jednostki dla definicji przepływu procesów biznesowych, użyj [dokumentu $metadata CSDL](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations.md#csdl-metadata-document). 
- Powiąż rekord jednostki przepływu procesów biznesowych z prawidłowym etapem określonym w definicji przepływu procesów biznesowych, ustawiając jednowartościową właściwość nawigacji przy użyciu adnotacji `@odata.bind`. Aby sprawdzić nazwę właściwości nawigacji (zwykle `activestageid`), która wskazuje rekord etapu dla definicji przepływu procesów biznesowych, użyj [dokumentu $metadata CSDL](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations.md#csdl-metadata-document).

    Ponadto możesz pobrać informacje o wszystkich etapach dla definicji przepływu procesów biznesowych przy użyciu następującego żądania internetowego interfejsu API, przy założeniu, że identyfikator definicji przepływu procesów biznesowych to 2669927e-8ad6-4f95-8a9a-f1008af6956f:

    **Żądanie**

    ```http
    GET [Organization URI]/api/data/v9.0/processstages?$select=stagename&$filter=processid/workflowid eq 2669927e-8ad6-4f95-8a9a-f1008af6956f HTTP/1.1
    ```

    **Odpowiedź**

    ```http
    {
        "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#processstages(stagename)",
        "value": [
            {
                "@odata.etag": "W/\"858240\"",
                "stagename": "S1",
                "processstageid": "9a9185f5-b75b-4bbb-9c2b-a6626683b99b"
            },
            {
                "@odata.etag": "W/\"858239\"",
                "stagename": "S3",
                "processstageid": "a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a"
            },
            {
                "@odata.etag": "W/\"858238\"",
                "stagename": "S2",
                "processstageid": "19a11fc0-3398-4214-8522-cb2a97f66e4b"
            }
        ]
    }
    ```

Następnie użyj następującego żądania, aby utworzyć wystąpienie definicji przepływu procesów biznesowych dla rekordu konta (ID=a176be9e-9a68-e711-80e7-00155d41e206) oraz aktywnego etapu ustawionego jako pierwszy etap wystąpienia procesu, S1 (ID=9a9185f5-b75b-4bbb-9c2b-a6626683b99b):

**Żądanie**

```http
POST [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
Content-Type: application/json; charset=utf-8 
OData-MaxVersion: 4.0 
OData-Version: 4.0 
Accept: application/json 

{
    "bpf_accountid@odata.bind": "/accounts(a176be9e-9a68-e711-80e7-00155d41e206)",
    "activestageid@odata.bind": "/processstages(9a9185f5-b75b-4bbb-9c2b-a6626683b99b)"    
}
```

**Odpowiedź**

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/new_mycustombpfs(cc3f721b-026e-e811-80ff-00155d513100)
```

Należy pamiętać, że aby utworzyć wystąpienie definicji przepływu procesów biznesowych, dla którego jako aktywny etap ustawiono etap ***inny*** niż pierwszy etap, należy również podać parametr `traversedpath` w żądaniu. Pokonana ścieżka jest oddzielanym przecinkami ciągiem identyfikatorów etapów procesu, które reprezentują odwiedzone etapy wystąpienia przepływu procesów biznesowych. Następujące żądanie tworzy wystąpienie dla rekordu konta (ID=679b2464-71b5-e711-80f5-00155d513100) oraz aktywnego etapu ustawionego jako drugi etap, S2 (ID=19a11fc0-3398-4214-8522-cb2a97f66e4b).

```http
POST [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
Content-Type: application/json; charset=utf-8 
OData-MaxVersion: 4.0 
OData-Version: 4.0 
Accept: application/json 

{
    "bpf_accountid@odata.bind": "/accounts(679b2464-71b5-e711-80f5-00155d513100)",
    "activestageid@odata.bind": "/processstages(19a11fc0-3398-4214-8522-cb2a97f66e4b)",
    "traversedpath":"9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b"   
}
```

### <a name="update-a-business-process-flow-entity-record-process-instance"></a>Aktualizowanie rekordu jednostki przepływu procesów biznesowych (wystąpienie procesu)

Można zaktualizować wystąpienie procesu, aby przejść do następnego lub poprzedniego etapu, porzucić wystąpienie procesu, ponownie uaktywnić wystąpienie procesu lub zakończyć wystąpienie procesu. 

#### <a name="stage-navigation"></a>Przechodzenie między etapami

Aby przejść do innego etapu, należy zaktualizować rekord wystąpienia procesu w celu zmiany jego identyfikatora aktywnego etapu i odpowiedniego zaktualizowania pokonanej ścieżki. Należy przechodzić tylko do następnego lub poprzedniego etapu podczas aktualizowania wystąpienia przepływu procesów biznesowych.

Aby przechodzić między etapami, należy znać identyfikator wystąpienia przepływu procesów biznesowych, który chcesz zaktualizować. Aby pobrać wszystkie wystąpienia przepływu procesów biznesowych, zobacz [Pobieranie wszystkich rekordów (wystąpień) jednostki przepływu procesów biznesowych](#retrieve-all-the-records-instances-for-a-business-process-flow-entity) we wcześniejszej części.

Przy założeniu, że identyfikator wystąpienia procesu, które chcesz zaktualizować, to dc2ab599-306d-e811-80ff-00155d513100, użyj następującego żądania, aby zaktualizować aktywny etap z S1 do S2:

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1
Content-Type: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0

{
    "activestageid@odata.bind": "/processstages(19a11fc0-3398-4214-8522-cb2a97f66e4b)",
    "traversedpath": "9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b"
}
```

#### <a name="change-the-state-of-a-process-instance-abort-reactivate-or-finish"></a>Zmienianie stanu wystąpienia procesu: przerywanie, ponowne uaktywnianie lub kończenie 

Wystąpienie procesu może mieć następujące stany: **Aktywne**, **Zakończone** lub **Przerwane**. Stan jest określany na podstawie następujących atrybutów w rekordzie wystąpienia procesu:

- **statecode**: wyświetla stan wystąpienia procesu.

    |Wartość|Etykieta|
    |-----|-----|
    |0    |Aktywne|
    |1    |Nieaktywne|

- **statuscode**: wyświetla informacje o stanie wystąpienia procesu.

    |Wartość|Etykieta|
    |-----|-----|
    |1    |Aktywne|
    |2    |Zakończone|
    |3    |Przerwane|

W celu **przerwania** wystąpienia procesu, użyj następującego żądania, aby ustawić odpowiednie wartości `statecode` i `statuscode`:

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1   
Content-Type: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0 
  
{ 
    "statecode" : "1", 
    "statuscode": "3" 
}
```
 
> [!NOTE]
> Wystąpienie procesu można przerwać na dowolnym etapie.

Podobnie, aby ponownie uaktywnić wystąpienie procesu, zastąp wartości `statecode` i `statuscode` w powyższym kodzie wartościami odpowiednio **0** i **1**.

Aby ustawić stan wystąpienia procesu **Zakończone**, co jest możliwe tylko na ostatnim etapie wystąpienia procesu, zastąp wartości `statecode` i `statuscode` w powyższym kodzie wartościami odpowiednio **0** i **2**.

#### <a name="cross-entity-navigation"></a>Przechodzenie między jednostkami

Aby przechodzić między jednostkami w tym przykładzie, należy ustawić aktywny etap wystąpienia procesu na ostatni etap, S3 (ID=a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a), odpowiednio zaktualizować przebytą ścieżkę i ustawić rekord kontaktu jako główny rekord jednostki, zgodnie z definicją przepływu procesów biznesowych.

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1   
Content-Type: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0 
  
{
    "activestageid@odata.bind": "/processstages(a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a)",
    "traversedpath":"9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b,a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a",
    "bpf_contactid@odata.bind": "/contacts(0e3f10b0-da33-e811-80fc-00155d513100)"
}
``` 

### <a name="delete-a-business-process-flow-entity-record-process-instance"></a>Usuwanie rekordu jednostki przepływu procesów biznesowych (wystąpienie procesu)

Użyj następującego żądania internetowego interfejsu API:

**Żądanie**

```http
DELETE [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1
```  

**Odpowiedź**

Jeśli rekord istnieje, otrzymasz normalną odpowiedź ze stanem 204, która oznacza, że usuwanie powiodło się. Jeśli jednostka nie zostanie znaleziona, otrzymasz odpowiedź ze stanem 404.

## <a name="use-retrieveprocessinstances-and-retrieveactivepath-messages"></a>Użycie komunikatów RetrieveProcessInstances i RetrieveActivePath

Użyj komunikatu `RetrieveProcessInstances` (<xref href="Microsoft.Dynamics.CRM.RetrieveProcessInstances?text=RetrieveActivePath Function" /> lub <xref:Microsoft.Crm.Sdk.Messages.RetrieveProcessInstancesRequest>), aby pobrać wszystkie wystąpienia przepływu procesów biznesowych dla rekordu jednostki we wszystkich definicjach procesów biznesowych. Zwracane wystąpienia przepływu procesów biznesowych są uporządkowane na podstawie atrybutu `modifiedon` dla danego wystąpienia. Na przykład ostatnio zmodyfikowane wystąpienie przepływu procesów biznesowych będzie *pierwszym* rekordem w zwróconej kolekcji. Ostatnio zmodyfikowane wystąpienie przepływu procesów biznesowych jest tym, które jest aktywne w interfejsie użytkownika dla rekordu jednostki.  
  
Każdy rekord wystąpienia przepływu procesów biznesowych zwrócony dla rekordu jednostki w wyniku użycia komunikatu `RetrieveProcessInstances` przechowuje identyfikator aktywnego etapu w atrybucie `processstageid`, za pomocą którego można sprawdzić aktywny etap, a następnie przejść do poprzedniego lub następnego etapu. W tym celu należy najpierw sprawdzić aktywną ścieżkę wystąpienia przepływu procesów biznesowych oraz etapy dostępne w wystąpieniu przepływu procesów, używając komunikatu `RetrieveActivePath` (<xref href="Microsoft.Dynamics.CRM.RetrieveActivePath?text=RetrieveActivePath Function" /> lub <xref:Microsoft.Crm.Sdk.Messages.RetrieveActivePathRequest>).   
  
 Po uzyskaniu informacji o aktywnym etapie i aktywnej ścieżce dla wystąpienia przepływu procesów biznesowych można użyć tych informacji, aby przejść do poprzedniego lub następnego etapu w aktywnej ścieżce. Przechodzenie do następnych etapów powinno odbywać się w kolejności, co oznacza, że należy przechodzić tylko do następnego etapu w aktywnej ścieżce.   
  
 Aby zapoznać się z pełnym przykładem kodu, w którym pokazano użycie tych dwóch metod oraz przechodzenie między etapami przy użyciu [usługi organizacji](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata), zobacz [Przykład: Praca z przepływami procesów biznesowych](sample-work-business-process-flows.md). 

<a name="ApplyBPF"></a>   
## <a name="apply-business-process-flow-while-creating-an-entity-record"></a>Stosowanie przepływu procesów biznesowych podczas tworzenia rekordu jednostki

Ta sekcja zawiera informacje na temat domyślnego zachowania w przypadku automatycznego stosowania przepływów procesów biznesowych do nowych rekordów jednostek tworzonych w rozwiązaniu Customer Engagement oraz sposobu jego zastępowania w celu stosowania wybranego przepływu procesów biznesowych do nowych rekordów jednostek.

Domyślnie w przypadku nowej jednostki, dla której zdefiniowano wiele przepływów procesów biznesowych, system stosuje przepływ procesów biznesowych do rekordu nowej jednostki przy użyciu następującej wieloetapowej logiki:
1. Zidentyfikuj wszystkie przepływy procesów biznesowych dotyczące nowego rekordu jednostki na podstawie atrybutu **Workflow.PrimaryEntity** rekordów definicji przepływów procesów biznesowych.
2. Określ definicje przepływów procesów biznesowych, do których ma dostęp bieżący użytkownik. Aby uzyskać informacje na temat sposobu określania dostępu do przepływu procesów biznesowych i zarządzania nim, zobacz [Zarządzanie zabezpieczeniami przepływów procesów biznesowych](#BPFSecurity) we wcześniejszej części tego tematu.<br/>  
3. Wszystkie definicje przepływów procesów biznesowych w systemie podlegają globalnej kolejności na jednostkę. Kolejność przepływu procesów biznesowych jest przechowywana w atrybucie **Workflow.ProcessOrder**. Definicje przepływów procesów biznesowych dla jednostki są sortowane według tej kolejności i wybierana jest definicja o najmniejszej wartości kolejności.
4. Jeśli rekord jednostki jest tworzony przy użyciu aplikacji biznesowej (moduł aplikacji), stosowany jest dodatkowy poziom filtrowania w celu wybrania przepływu procesów biznesowych, który ma być automatycznie stosowany do nowych rekordów jednostek. Podczas pracy w aplikacji użytkownicy mogą uzyskiwać dostęp tylko do odpowiednich jednostek, widoków i formularzy, do których mają dostęp na podstawie ról zabezpieczeń przypisanych do aplikacji biznesowej. 
    - Jeśli aplikacja biznesowa nie zawiera żadnych przepływów procesów biznesowych, przepływ procesów biznesowych jest stosowany zgodnie z objaśnieniem do kroku 3.
    - Jeśli aplikacja biznesowa zawiera co najmniej jeden przepływ procesów biznesowych, będą mieć zastosowanie tylko przepływy procesów biznesowych istniejące w aplikacji. W takim przypadku, gdy użytkownik pracuje w kontekście aplikacji biznesowej, lista przepływów procesów biznesowych z kroku 3 jest dodatkowo filtrowana do przepływów stanowiących część aplikacji biznesowej i obecnych w module aplikacji oraz sortowana na podstawie kolejności przetwarzania. 
    - W przypadku braku dostępnych przepływów procesów biznesowych w aplikacji biznesowej dla jednostki lub braku przepływów dostępnych dla użytkownika do nowego rekordu jednostki nie jest stosowany żaden przepływ procesów biznesowych.

Można zastąpić domyślną logikę automatycznego stosowania przepływów procesów biznesowych do nowych rekordów jednostek. W tym celu dla atrybutu **ProcessId** jednostki ustaw jedną z następujących wartości podczas tworzenia nowego rekordu jednostki:
- Ustaw wartość **Guid.Empty**, aby pominąć ustawianie przepływu procesów biznesowych dla nowych rekordów jednostek. Można to zrobić w przypadku zbiorczego tworzenia rekordów jednostek, do których nie ma być stosowany przepływ procesów biznesowych.
- Ustaw konkretną jednostkę przepływu procesów biznesowych (jako odwołanie do jednostki). W tym przypadku system zastosuje określony przepływ procesów biznesowych zamiast domyślnej logiki.

Jeśli wartość atrybutu **ProcessId** nie zostanie ustawiona podczas tworzenia nowego rekordu jednostki, system zastosuje domyślną logikę, jak wyjaśniono wcześniej.

> [!NOTE]
> Obsługiwane jest tylko programowe zastępowanie domyślnej logiki automatycznego stosowania przepływów procesów biznesowych do nowych rekordów jednostek. Nie można tego zrobić przy użyciu interfejsu użytkownika.

## <a name="legacy-process-related-attributes-in-entities"></a>Starsze atrybuty dotyczące procesu w jednostkach

Starsze atrybuty dotyczące procesu (takie jak **ProcessId**, **StageId** i **TraversedPath**) w jednostkach z włączoną obsługą przepływów procesów biznesowych są już przestarzałe. Modyfikowanie tych starszych atrybutów dotyczących procesu dla docelowych rekordów jednostek nie gwarantuje spójności stanu przepływu procesów biznesowych i ***nie*** jest obsługiwanym scenariuszem. Zalecane jest użycie atrybutów jednostki przepływu procesów biznesowych, jak wyjaśniono wcześniej w sekcji [Tworzenie, pobieranie, aktualizowanie i usuwanie rekordów jednostek przepływów procesów biznesowych (wystąpień procesów)](#create-retrieve-update-and-delete-business-process-flow-entity-records-process-instances)

Jedynym wyjątkiem jest programowe modyfikowanie atrybutu **ProcessId** podczas tworzenia rekordu jednostki w celu zastąpienia domyślnego stosowania przepływu procesów biznesowych do nowego rekordu, jak wyjaśniono w poprzedniej sekcji: [Stosowanie przepływu procesów biznesowych podczas tworzenia rekordu jednostki](#ApplyBPF).

<a name="BKMK_clientSideScript"></a>   
## <a name="client-side-programmability-support-for-business-process-flows"></a>Obsługa programowania po stronie klienta dla przepływów procesów biznesowych  
 Istnieje obiekt po stronie klienta, który służy do interakcji z przepływami procesów biznesowych w skryptach formularzy. Przepływy procesów biznesowych wyzwalają zdarzenia po stronie klienta za każdym razem, gdy proces jest stosowany do rekordu, etap ulega zmianie lub stan zostaje zmieniony na `Active`, `Finished` lub `Aborted`. Więcej informacji: [formContext.data.process (dokumentacja interfejsu API klienta)](/dynamics365/customer-engagement/developer/clientapi/reference/formcontext-data-process.md)  
  
<a name="BKMK_MaxSettings"></a>   
## <a name="maximum-number-of-processes-stages-and-steps"></a>Maksymalna liczba procesów, etapów i kroków  
 Domyślna wartość maksymalnej liczby uaktywnionych przepływów procesów biznesowych na jednostkę wynosi 10. Można określić inną wartość za pomocą atrybutu `Organization.MaximumActiveBusinessProcessFlowsAllowedPerEntity`. Jednak w przypadku wartości większej niż 10 może być zauważalny spadek wydajności systemu podczas przełączania procesów lub otwierania rekordu zawierającego przypisany przepływ procesów biznesowych. Może to być szczególnie zauważalne, jeśli procesy obejmują wiele jednostek.  
  
 Nie można dostosowywać następujących ustawień:  
  
-   Maksymalna liczba etapów na jednostkę w procesie wynosi 30.  
  
-   Maksymalna liczba kroków na każdym etapie wynosi 30.  
  
-   Maksymalna liczba jednostek, które mogą być częścią przepływu procesów, wynosi 5.  

