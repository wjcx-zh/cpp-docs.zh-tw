---
title: OLE DB 提供者樣板的巨集
ms.date: 02/11/2019
f1_keywords:
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
ms.openlocfilehash: e72204102bfa47a9dd162499030a38c07bbfe46c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504008"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 提供者樣板的巨集

OLE DB 範本提供者宏提供下列類別的功能：

## <a name="property-set-map-macros"></a>屬性集對應宏

| 名稱 | 描述 |
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|標記屬性集的開頭。|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|標記屬性集的開頭。|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|標記屬性集的開頭，該屬性集可以隱藏或定義于提供者範圍之外。|
|[CHAIN_PROPERTY_SET](#chain_property_set)|將屬性群組連結在一起。|
|[END_PROPERTY_SET](#end_property_set)|標記屬性集的結尾。|
|[END_PROPSET_MAP](#end_propset_map)|標記屬性集對應的結尾。|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|將屬性（property）中的特定屬性（property）設定為預設值。|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|將屬性（property）中的特定屬性（property）設定為您所提供的值。 也可讓您設定旗標和選項。|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|將屬性（property）中的特定屬性（property）設定為您所提供的值。|

## <a name="column-map-macros"></a>資料行對應宏

| 名稱 | 描述 |
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|標記提供者資料行對應專案的開頭。|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|標記提供者資料行對應專案的結尾。|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|表示提供者所支援的特定資料行。|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|表示提供者所支援的特定資料行。 您可以指定資料行資料類型。|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|表示提供者所支援的特定資料行。 您可以指定資料行的大小、資料類型、精確度、小數位數和架構資料列集 GUID。|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|表示提供者所支援的特定資料行。 您可以指定資料行大小。|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|表示提供者所支援的特定資料行。 它會假設資料行類型是字串。|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|表示提供者所支援的特定資料行。 和 PROVIDER_COLUMN_ENTRY_LENGTH 一樣，還可讓您指定資料行的資料類型和大小。|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|表示提供者所支援的特定資料行。 它會假設資料行類型是 Unicode 字元字串。|

## <a name="schema-rowset-macros"></a>架構資料列集宏

| 名稱 | 描述 |
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|標記架構對應的開頭。|
|[END_SCHEMA_MAP](#end_schema_map)|標記架構對應的結尾。|
|[SCHEMA_ENTRY](#schema_entry)|將 GUID 與類別產生關聯。|

## <a name="requirements"></a>需求

**Header:** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a> BEGIN_PROPERTY_SET

標記屬性集對應中設定的屬性（property）開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>參數

*guid*<br/>
在屬性 GUID。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](#begin_propset_map)。

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

標記屬性集對應中設定的屬性（property）開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>參數

*guid*<br/>
在屬性 GUID。

*flags*<br/>
在UPROPSET_HIDDEN 任何您不想公開的屬性集，或針對提供者範圍外所定義之屬性的提供者 UPROPSET_PASSTHROUGH。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](#begin_propset_map)。

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

標記屬性集對應專案的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>參數

*類別*<br/>
在指定這個屬性集的類別。 您可以在下列 OLE DB 物件中指定屬性集：

- [資料來源物件](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Session 物件](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [命令](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>範例

以下是範例屬性集對應：

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a> CHAIN_PROPERTY_SET

此宏會將屬性群組連結在一起。

#### <a name="syntax"></a>語法

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>參數

*ChainClass*<br/>
在要鏈屬性的類別名稱。 這是 ATL 專案 Wizard 所產生的類別，此類別已包含對應 (例如會話、命令或資料來源物件類別) 。

#### <a name="remarks"></a>備註

您可以從另一個類別將屬性集鏈至您自己的類別，然後直接從您的類別存取屬性。

> [!CAUTION]
> 請謹慎使用此宏。 不當使用可能會導致取用者使 OLE DB 的一致性測試失敗。

### <a name="end_property_set"></a><a name="end_property_set"></a> END_PROPERTY_SET

標記屬性集的結尾。

#### <a name="syntax"></a>語法

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>參數

*guid*<br/>
在屬性 GUID。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](#begin_propset_map)。

### <a name="end_propset_map"></a><a name="end_propset_map"></a> END_PROPSET_MAP

標記屬性集對應專案的結尾。

#### <a name="syntax"></a>語法

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](#begin_propset_map)。

### <a name="property_info_entry"></a><a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

代表屬性集中的特定屬性。

#### <a name="syntax"></a>語法

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>參數

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，可搭配屬性集 GUID 以識別屬性。

#### <a name="remarks"></a>備註

此巨集會將 `DWORD` 類型的屬性值設定為 ATLDB 中定義的預設值。 若要將屬性設定為您選擇的值，請使用 [PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)。 若要 `VARTYPE` 同時設定屬性的和 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) ，請使用 [PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](#begin_propset_map)。

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

代表屬性集中的特定屬性。

#### <a name="syntax"></a>語法

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>參數

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，可搭配屬性集 GUID 以識別屬性。

*vt*<br/>
[in] 此屬性項目的 `VARTYPE`。  (定義于 wtypes.h .h) 

*dwFlags*<br/>
[in] 描述此屬性項目的 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 值。

*value*<br/>
[in] `DWORD`類型的屬性值。

*options*<br/>
DBPROPOPTIONS_REQUIRED 或 DBPROPOPTIONS_SETIFCHEAP。 一般而言，提供者不需要設定 *選項* ，因為它是由取用者設定。

#### <a name="remarks"></a>備註

透過這個巨集，您可以直接指定 `DWORD` 類型的屬性值，以及選項和旗標。 若只要將屬性設定為 ATLDB.H 中定義的預設值，請使用 [PROPERTY_INFO_ENTRY](#property_info_entry)。 若要將屬性設定為您選擇的值，請使用 [PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)，而不需要設定屬性的選項或旗標。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](#begin_propset_map)。

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

代表屬性集中的特定屬性。

#### <a name="syntax"></a>語法

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>參數

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，可搭配屬性集 GUID 以識別屬性。

*value*<br/>
[in] `DWORD`類型的屬性值。

#### <a name="remarks"></a>備註

使用這個宏，您可以直接指定類型的屬性值 `DWORD` 。 將屬性設定為 ATLDB.H 中定義的預設值。H，使用 [PROPERTY_INFO_ENTRY](#property_info_entry)。 若要設定屬性的值、旗標和選項，請使用 [PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](#begin_propset_map)。

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

標記提供者資料行對應專案的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>參數

*theClass*<br/>
在此對應所屬類別的名稱。

#### <a name="example"></a>範例

以下是範例提供者資料行對應：

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

標記提供者資料行對應專案的結尾。

#### <a name="syntax"></a>語法

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>範例

請參閱 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)。

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

表示提供者所支援的特定資料行。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>參數

*name*<br/>
在資料行名稱。

*序*<br/>
[in] 資料行編號。 除非資料行是書簽資料行，否則資料行編號不得為0。

*成員*<br/>
在對應至資料行的成員變數 `dataClass` 。

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

表示提供者所支援的特定資料行。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>參數

*name*<br/>
在資料行名稱。

*序*<br/>
[in] 資料行編號。 除非資料行是書簽資料行，否則資料行編號不得為0。

*dbtype*<br/>
在 [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))中的資料類型。

*成員*<br/>
在中儲存資料的成員變數 `dataClass` 。

#### <a name="remarks"></a>備註

可讓您指定資料行資料類型。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)。

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

表示提供者所支援的特定資料行。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>參數

*name*<br/>
在資料行名稱。

*序*<br/>
[in] 資料行編號。 除非資料行是書簽資料行，否則資料行編號不得為0。

*flags*<br/>
在指定傳回資料的方式。 請參閱 `dwFlags` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的描述。

*colSize*<br/>
在資料行大小。

*dbtype*<br/>
在指出值的資料類型。 請參閱 `wType` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的描述。

*有效位數*<br/>
在指出當 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL *dbType* 時，取得資料時所要使用的精確度。 請參閱 `bPrecision` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的描述。

*scale*<br/>
在指出當 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL dbType 時，取得資料時要使用的尺規。 請參閱 `bScale` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的描述。

*guid*<br/>
架構資料列集 GUID。 如需架構資料列集的清單及其 Guid，請參閱 OLE DB 程式設計*人員參考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

#### <a name="remarks"></a>備註

可讓您指定資料行的大小、資料類型、精確度、小數位數和架構資料列集 GUID。

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

表示提供者所支援的特定資料行。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>參數

*name*<br/>
在資料行名稱。

*序*<br/>
[in] 資料行編號。 除非資料行是書簽資料行，否則資料行編號不得為0。

*size*<br/>
在資料行大小（以位元組為單位）。

*成員*<br/>
在中 `dataClass` 儲存資料行資料的成員變數。

#### <a name="remarks"></a>備註

可讓您指定資料行大小。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)。

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

表示提供者所支援的特定資料行。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>參數

*name*<br/>
在資料行名稱。

*序*<br/>
[in] 資料行編號。 除非資料行是書簽資料行，否則資料行編號不得為0。

*成員*<br/>
在資料類別中儲存資料的成員變數。

#### <a name="remarks"></a>備註

當將資料行資料假設為 [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))時，請使用這個宏。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)。

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

表示提供者所支援的特定資料行。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>參數

*name*<br/>
在資料行名稱。

*序*<br/>
[in] 資料行編號。 除非資料行是書簽資料行，否則資料行編號不得為0。

*dbtype*<br/>
在 [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))中的資料類型。

*size*<br/>
在資料行大小（以位元組為單位）。

*成員*<br/>
在資料類別中儲存資料的成員變數。

#### <a name="remarks"></a>備註

類似于 [PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length) ，但也可讓您指定資料行的資料類型和大小。

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

表示提供者所支援的特定資料行。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>參數

*name*<br/>
在資料行名稱。

*序*<br/>
[in] 資料行編號。 除非資料行是書簽資料行，否則資料行編號不得為0。

*成員*<br/>
在資料類別中儲存資料的成員變數。

#### <a name="remarks"></a>備註

當資料行資料是以 null 結束的 Unicode 字元字串， [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85))時，請使用這個宏。

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

表示架構對應的開始。

#### <a name="syntax"></a>語法

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>參數

*SchemaClass*<br/>
包含對應的類別。 通常這會是會話類別。

#### <a name="remarks"></a>備註

如需架構資料列集的詳細資訊，請參閱 Windows SDK 中的 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

### <a name="end_schema_map"></a><a name="end_schema_map"></a> END_SCHEMA_MAP

表示架構對應的結尾。

#### <a name="syntax"></a>語法

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)。

### <a name="schema_entry"></a><a name="schema_entry"></a> SCHEMA_ENTRY

將 GUID 與類別產生關聯。

#### <a name="syntax"></a>語法

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>參數

*guid*<br/>
架構資料列集 GUID。 如需架構資料列集的清單及其 Guid，請參閱 OLE DB 程式設計*人員參考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

*rowsetClass*<br/>
將建立以代表架構資料列集的類別。

#### <a name="remarks"></a>備註

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 接著可以查詢對應以取得 guid 清單，或者如果有 guid，則可以建立資料列集。 架構資料列集 `IDBSchemaRowsetImpl` 建立類似于標準 `CRowsetImpl` 衍生類別，但它必須提供具有下列簽章的 `Execute` 方法：

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

此 `Execute` 函數會填入資料列集的資料。 ATL 專案 Wizard 會依照 OLE DB 程式設計*人員參考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))所述，建立三個強制 OLE DB 架構的專案中的三個初始架構資料列集：

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

Wizard 也會在架構對應中新增三個對應的專案。 如需使用 wizard 建立提供者的詳細資訊，請參閱 [建立 OLE DB 範本提供者](../../data/oledb/creating-an-ole-db-provider.md) 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 提供者範本參考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 提供者範本的宏](../../data/oledb/macros-for-ole-db-provider-templates.md)
