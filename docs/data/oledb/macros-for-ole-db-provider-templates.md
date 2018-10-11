---
title: OLE DB 提供者樣板的巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e26210bd5c856be43e281c57eaafc9c6e16b6d69
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083485"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 提供者樣板的巨集

OLE DB 範本提供巨集提供以下類別的功能：  
  
## <a name="property-set-map-macros"></a>屬性會設定對應巨集  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](#begin_property_set)|將標記屬性集的開頭。|  
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|將標記屬性集的開頭。|  
|[BEGIN_PROPSET_MAP](#begin_propset_map)|標記屬性的開頭設定，可以隱藏或定義範圍以外的提供者。|  
|[CHAIN_PROPERTY_SET](#chain_property_set)|鏈結在一起，屬性群組。|  
|[END_PROPERTY_SET](#end_property_set)|將標記屬性集的結尾。|  
|[END_PROPSET_MAP](#end_propset_map)|結束標記的屬性集對應。|  
|[PROPERTY_INFO_ENTRY](#property_info_entry)|您可以設定特定的屬性中將屬性設定為預設值。|  
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|將屬性設定為您所提供的值中設定特定的屬性。 也可讓您設定旗標和選項。|  
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|將屬性設定為您所提供的值中設定特定的屬性。|  
  
## <a name="column-map-macros"></a>資料行對應巨集  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|標記提供者的資料行對應項目的開頭。|  
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|標記提供者的資料行對應項目的結尾。|  
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|表示提供者支援的特定資料行。|  
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|表示提供者支援的特定資料行。 您可以指定資料行資料類型。|  
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|表示提供者支援的特定資料行。 您可以指定資料行的大小、 資料類型、 有效位數、 小數位數和結構描述資料列集的 GUID。|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|表示提供者支援的特定資料行。 您可以指定資料行大小。|  
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|表示提供者支援的特定資料行。 它會假設資料行類型是字串。|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|表示提供者支援的特定資料行。 PROVIDER_COLUMN_ENTRY_LENGTH，但也可讓您指定資料行的資料類型，以及大小。|  
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|表示提供者支援的特定資料行。 它會假設資料行類型是 Unicode 字元字串。|  
  
## <a name="schema-rowset-macros"></a>結構描述資料列集巨集  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|標記結構描述對應的開頭。|  
|[END_SCHEMA_MAP](#end_schema_map)|結束標記的結構描述對應。|  
|[SCHEMA_ENTRY](#schema_entry)|關聯類別的 GUID。|  

## <a name="requirements"></a>需求  

**Header:** atldb.h  

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET

標記屬性的開頭設定的屬性中設定對應。  
  
#### <a name="syntax"></a>語法  
  
```cpp
BEGIN_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>參數  

*guid*<br/>
[in]屬性的 GUID。  
  
#### <a name="example"></a>範例  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

標記屬性的開頭設定的屬性中設定對應。  
  
#### <a name="syntax"></a>語法  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)  
```  
  
#### <a name="parameters"></a>參數  

*guid*<br/>
[in]屬性的 GUID。  
  
*flags*<br/>
[in]任何屬性集，您不想公開 （expose），或提供者公開的屬性定義的提供者的範圍外的 UPROPSET_PASSTHROUGH UPROPSET_HIDDEN。  
  
#### <a name="example"></a>範例  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

標記屬性的開頭設定的對應項目。  
  
#### <a name="syntax"></a>語法  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
```  
  
#### <a name="parameters"></a>參數  

*類別*<br/>
[in]指定設定這個屬性的類別。 屬性集，請指定下列的 OLE DB 物件：  
  
- [資料來源物件](/previous-versions/windows/desktop/ms721278)  
  
- [工作階段物件](/previous-versions/windows/desktop/ms711572)  
  
- [命令](/previous-versions/windows/desktop/ms724608)  
  
#### <a name="example"></a>範例  

以下是範例屬性集對應：  
  
[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET

這個巨集鏈結在一起，屬性群組。  
  
#### <a name="syntax"></a>語法  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
```  
  
#### <a name="parameters"></a>參數  

*ChainClass*<br/>
[in]要鏈結屬性之類別的名稱。 這是已經包含對應 （例如工作階段、 命令或資料來源物件類別） [ATL 專案精靈] 產生的類別。  
  
#### <a name="remarks"></a>備註  

您可以鏈結至您自己的類別，從另一個類別屬性集，然後直接從您的類別存取的屬性。  
  
> [!CAUTION]
>  謹慎使用這個巨集。 不當使用，可能會導致失敗的 OLE DB 一致性測試的取用者。  

### <a name="end_property_set"></a> END_PROPERTY_SET

將標記屬性集的結尾。  
  
#### <a name="syntax"></a>語法  
  
```cpp
END_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>參數  

*guid*<br/>
[in]屬性的 GUID。  
  
#### <a name="example"></a>範例  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="end_propset_map"></a> END_PROPSET_MAP

標記屬性的結尾會設定對應項目。  
  
#### <a name="syntax"></a>語法  
  
```cpp
END_PROPSET_MAP()  
```  
  
#### <a name="example"></a>範例  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

代表屬性集中的特定屬性。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
```  
  
#### <a name="parameters"></a>參數  

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882) 值，可搭配屬性集 GUID 以識別屬性。  
  
#### <a name="remarks"></a>備註  

此巨集會將 `DWORD` 類型的屬性值設定為 ATLDB 中定義的預設值。 若要將屬性設定為您選擇的值，請使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。 若要設定`VARTYPE`並[DBPROPFLAGS](/previous-versions/windows/desktop/ms724342)同時屬性，使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。  
  
#### <a name="example"></a>範例  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

代表屬性集中的特定屬性。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)  
```  
  
#### <a name="parameters"></a>參數  

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882) 值，可搭配屬性集 GUID 以識別屬性。  
  
*vt*<br/>
[in] 此屬性項目的 `VARTYPE`。 （wtypes.h 中所定義）  
  
*dwFlags*<br/>
[in] 描述此屬性項目的 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342) 值。  
  
*值*<br/>
[in] `DWORD`類型的屬性值。  
  
*options*<br/>
Dbpropoptions_required 時或 DBPROPOPTIONS_SETIFCHEAP 中。 一般而言，提供者不需要設定*選項*因為它由取用者設定。  
  
#### <a name="remarks"></a>備註  

透過這個巨集，您可以直接指定 `DWORD` 類型的屬性值，以及選項和旗標。 若只要將屬性設定為 ATLDB.H 中定義的預設值，請使用 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要將屬性設定為您選擇的值，請使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)，而不需要設定屬性的選項或旗標。  
  
#### <a name="example"></a>範例  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

代表屬性集中的特定屬性。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)  
```  
  
#### <a name="parameters"></a>參數  

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882) 值，可搭配屬性集 GUID 以識別屬性。  
  
*值*<br/>
[in] `DWORD`類型的屬性值。  
  
#### <a name="remarks"></a>備註  

使用這個巨集，您可以直接指定類型的屬性值`DWORD`。 若要將屬性設定為 ATLDB 中定義的預設值。H、 使用[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要設定的值、 旗標和屬性的選項，使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。  
  
#### <a name="example"></a>範例  

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

標記提供者的資料行對應項目的開頭。  
  
#### <a name="syntax"></a>語法  
  
```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)  
```  
  
#### <a name="parameters"></a>參數  

*theClass*<br/>
[in]此對應所屬的類別名稱。  
  
#### <a name="example"></a>範例  

以下是範例提供者的資料行對應：  
  
[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]  

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

標記提供者的資料行對應項目的結尾。  
  
#### <a name="syntax"></a>語法  
  
```cpp
END_PROVIDER_COLUMN_MAP()  
```  
  
#### <a name="example"></a>範例  

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。  

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

表示提供者支援的特定資料行。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)  
```  
  
#### <a name="parameters"></a>參數  

*name*<br/>
[in]資料行名稱。  
  
*序數*<br/>
[in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
*成員*<br/>
[in]中的成員變數`dataClass` 資料行對應。  

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

表示提供者支援的特定資料行。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)  
```  
  
#### <a name="parameters"></a>參數  

*name*<br/>
[in]資料行名稱。  
  
*序數*<br/>
[in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
*dbtype*<br/>
[in]中的資料類型[DBTYPE](/previous-versions/windows/desktop/ms711251)。  
  
*成員*<br/>
[in]中的成員變數`dataClass`，儲存資料。  
  
#### <a name="remarks"></a>備註  

可讓您指定資料行資料類型。  
  
#### <a name="example"></a>範例  

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。  

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

表示提供者支援的特定資料行。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)  
```  
  
#### <a name="parameters"></a>參數  

*name*<br/>
[in]資料行名稱。  
  
*序數*<br/>
[in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
*flags*<br/>
[in]指定傳回資料的方式。 請參閱`dwFlags`中的說明[DBBINDING 結構](/previous-versions/windows/desktop/ms716845)。  
  
*colSize*<br/>
[in]資料行大小。  
  
*dbtype*<br/>
[in]表示值的資料類型。 請參閱`wType`中的說明[DBBINDING 結構](/previous-versions/windows/desktop/ms716845)。  
  
*precision*<br/>
[in]指出如果取得資料時所要使用的有效位數*dbType* DBTYPE_NUMERIC 或 DBTYPE_DECIMAL。 請參閱`bPrecision`中的說明[DBBINDING 結構](/previous-versions/windows/desktop/ms716845)。  
  
*小數位數*<br/>
[in]表示如果 dbType DBTYPE_NUMERIC 或 DBTYPE_DECIMAL 取得資料時所要使用的比例。 請參閱`bScale`中的說明[DBBINDING 結構](/previous-versions/windows/desktop/ms716845)。  
  
*guid*<br/>
結構描述資料列集的 GUID。 請參閱[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程式設計人員參考*取得一份結構描述資料列集和其 Guid。  
  
#### <a name="remarks"></a>備註  

可讓您指定資料行的大小、 資料類型、 有效位數、 小數位數和結構描述資料列集的 GUID。  

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

表示提供者支援的特定資料行。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)  
```  
  
#### <a name="parameters"></a>參數  

*name*<br/>
[in]資料行名稱。  
  
*序數*<br/>
[in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
*size*<br/>
[in]資料行大小 （位元組）。  
  
*成員*<br/>
[in]中的成員變數`dataClass`儲存資料行的資料。  
  
#### <a name="remarks"></a>備註  

可讓您指定資料行大小。  
  
#### <a name="example"></a>範例  

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。 

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

表示提供者支援的特定資料行。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>參數  

*name*<br/>
[in]資料行名稱。  
  
*序數*<br/>
[in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
*成員*<br/>
[in]將資料儲存的資料類別中成員變數。  
  
#### <a name="remarks"></a>備註  

當資料行的資料皆必須使用這個巨集[DBTYPE_STR](/previous-versions/windows/desktop/ms711251)。  
  
#### <a name="example"></a>範例  

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。   

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

表示提供者支援的特定資料行。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)  
```  
  
#### <a name="parameters"></a>參數  

*name*<br/>
[in]資料行名稱。  
  
*序數*<br/>
[in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
*dbtype*<br/>
[in]中的資料類型[DBTYPE](/previous-versions/windows/desktop/ms711251)。  
  
*size*<br/>
[in]資料行大小 （位元組）。  
  
*成員*<br/>
[in]將資料儲存的資料類別中成員變數。  
  
#### <a name="remarks"></a>備註  

類似於[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)也可讓您指定資料行的資料類型，以及大小。  

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

表示提供者支援的特定資料行。  
  
#### <a name="syntax"></a>語法  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>參數  

*name*<br/>
[in]資料行名稱。  
  
*序數*<br/>
[in] 資料行編號。 除非資料行是書籤資料行，資料行數目必須為 0。  
  
*成員*<br/>
[in]將資料儲存的資料類別中成員變數。  
  
#### <a name="remarks"></a>備註  

使用這個巨集，資料行的資料是以 null 結束的 Unicode 字元字串，當[DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251)。  

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

表示結構描述對應的開頭。  
  
#### <a name="syntax"></a>語法  
  
```cpp
BEGIN_SCHEMA_MAP(SchemaClass);  
```  
  
#### <a name="parameters"></a>參數  

*SchemaClass*<br/>
包含對應的類別。 通常這會是工作階段類別。  
  
#### <a name="remarks"></a>備註  

請參閱[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)結構描述資料列集的詳細資訊的 Windows SDK 中。  

### <a name="end_schema_map"></a> END_SCHEMA_MAP

表示結構描述對應的結尾。  
  
#### <a name="syntax"></a>語法  
  
```cpp
END_SCHEMA_MAP()  
```  
  
#### <a name="see-also"></a>另請參閱  

[IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)

### <a name="schema_entry"></a> SCHEMA_ENTRY

關聯類別的 GUID。  
  
#### <a name="syntax"></a>語法  
  
```cpp
SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>參數  

*guid*<br/>
結構描述資料列集的 GUID。 請參閱[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程式設計人員參考*取得一份結構描述資料列集和其 Guid。  
  
*rowsetClass*<br/>
將建立來代表結構描述資料列集類別。  
  
#### <a name="remarks"></a>備註  

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)可以接著查詢取得 Guid，一份地圖，或如果它有一個 GUID，它可以建立一個資料列集。 結構描述資料列`IDBSchemaRowsetImpl`會建立類似於標準`CRowsetImpl`-衍生類別，但它必須提供`Execute`具有下列簽章的方法：  
  
```cpp  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
這`Execute`函式會將資料列集的資料填入。 [ATL 專案精靈] 建立，如中所述[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程式設計人員參考*，三個初始的三個必要的 OLE DB 結構描述的每個專案中的結構描述資料列：  
  
- DBSCHEMA_TABLES  
  
- DBSCHEMA_COLUMNS  
  
- DBSCHEMA_PROVIDER_TYPES  
  
精靈也會將三個對應的項目中的結構描述對應。 請參閱[建立 OLE DB 範本提供者](../../data/oledb/creating-an-ole-db-provider.md)如需使用精靈來建立提供者的詳細資訊。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 提供者範本參考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 提供者範本的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   