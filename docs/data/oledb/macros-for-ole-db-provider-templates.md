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
ms.openlocfilehash: 5d29b2548102b056a21ebfccb037af3a766788ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369811"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 提供者樣板的巨集

OLE 資料庫樣本提供者集提供以下類別的功能:

## <a name="property-set-map-macros"></a>屬性集對應巨集

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|標記屬性集的開頭。|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|標記屬性集的開頭。|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|標記可在提供程式範圍之外隱藏或定義的屬性集的開頭。|
|[CHAIN_PROPERTY_SET](#chain_property_set)|將屬性組合並在一起。|
|[END_PROPERTY_SET](#end_property_set)|標記屬性集的末尾。|
|[END_PROPSET_MAP](#end_propset_map)|標記屬性集映射的末尾。|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|將屬性集中的特定屬性設置為預設值。|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|將屬性集中的特定屬性設置為您提供的值。 還使您能夠設置標誌和選項。|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|將屬性集中的特定屬性設置為您提供的值。|

## <a name="column-map-macros"></a>列對應巨集

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|標記提供程式列映射條目的開頭。|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|標記提供程式列映射條目的末尾。|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|表示提供程式支援的特定列。|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|表示提供程式支援的特定列。 您可以指定欄資料類型。|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|表示提供程式支援的特定列。 您可以指定欄的大小、資料類型、精度、比例和架構排組 GUID。|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|表示提供程式支援的特定列。 您可以指定欄位大小。|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|表示提供程式支援的特定列。 它假定列類型是字串。|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|表示提供程式支援的特定列。 PROVIDER_COLUMN_ENTRY_LENGTH,但也允許您指定列的數據類型和大小。|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|表示提供程式支援的特定列。 它假定列類型是 Unicode 字串。|

## <a name="schema-rowset-macros"></a>架構列集巨集

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|標記架構映射的開頭。|
|[END_SCHEMA_MAP](#end_schema_map)|標記架構映射的末尾。|
|[SCHEMA_ENTRY](#schema_entry)|將 GUID 與類關聯。|

## <a name="requirements"></a>需求

**Header:** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

在屬性集映射中標記屬性集的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>參數

*Guid*<br/>
[在]屬性 GUID。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

在屬性集映射中標記屬性集的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>參數

*Guid*<br/>
[在]屬性 GUID。

*標誌*<br/>
[在]UPROPSET_HIDDEN,對於不希望公開的任何屬性集,或UPROPSET_PASSTHROUGH提供程式公開在提供程式範圍之外定義的屬性。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

標記屬性集地圖條目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>參數

*類別*<br/>
[在]指定此屬性集的類。 可以在以下 OLE DB 物件中指定屬性集:

- [資料來源物件](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [工作階段物件](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [命令](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>範例

下面是一個範例屬性集映射:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

此宏將屬性分組在一起。

#### <a name="syntax"></a>語法

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>參數

*鏈類*<br/>
[在]要連結屬性的類的名稱。 這是由 ATL 專案嚮導生成的類,該嚮導已包含映射(如會話、命令或數據源物件類)。

#### <a name="remarks"></a>備註

可以將屬性集從另一個類連結到您自己的類,然後直接從類訪問屬性。

> [!CAUTION]
> 請謹慎使用此宏。 使用不當可能導致消費者未通過 OLE DB 符合性測試。

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

標記屬性集的末尾。

#### <a name="syntax"></a>語法

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>參數

*Guid*<br/>
[在]屬性 GUID。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="end_propset_map"></a><a name="end_propset_map"></a>END_PROPSET_MAP

標記屬性集映射條目的末尾。

#### <a name="syntax"></a>語法

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="property_info_entry"></a><a name="property_info_entry"></a>PROPERTY_INFO_ENTRY

代表屬性集中的特定屬性。

#### <a name="syntax"></a>語法

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>參數

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，可搭配屬性集 GUID 以識別屬性。

#### <a name="remarks"></a>備註

此巨集會將 `DWORD` 類型的屬性值設定為 ATLDB 中定義的預設值。 若要將屬性設定為您選擇的值，請使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。 要設定`VARTYPE`屬性與[DBPROPFLAGS,](/previous-versions/windows/desktop/ms724342(v=vs.85))請使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

代表屬性集中的特定屬性。

#### <a name="syntax"></a>語法

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>參數

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，可搭配屬性集 GUID 以識別屬性。

*vt*<br/>
[in] 此屬性項目的 `VARTYPE`。 ( wtype.h 中定義 )

*dwFlags*<br/>
[in] 描述此屬性項目的 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 值。

*值*<br/>
[in] `DWORD`類型的屬性值。

*選項*<br/>
DBPROPOPTIONS_REQUIRED 或 DBPROPOPTIONS_SETIFCHEAP。 通常,提供程式不需要設置*選項*,因為它由使用者設置。

#### <a name="remarks"></a>備註

透過這個巨集，您可以直接指定 `DWORD` 類型的屬性值，以及選項和旗標。 若只要將屬性設定為 ATLDB.H 中定義的預設值，請使用 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要將屬性設定為您選擇的值，請使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)，而不需要設定屬性的選項或旗標。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

代表屬性集中的特定屬性。

#### <a name="syntax"></a>語法

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>參數

*dwPropID*<br/>
[in] [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，可搭配屬性集 GUID 以識別屬性。

*值*<br/>
[in] `DWORD`類型的屬性值。

#### <a name="remarks"></a>備註

使用此宏,可以直接指定`DWORD`type 的屬性值。 將屬性設置為 ATLDB 中定義的預設值。H,使用[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 要設定屬性的值、標誌和選項,請使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。

#### <a name="example"></a>範例

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

標記提供程式列映射條目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>參數

*類別*<br/>
[在]此映射所屬的類的名稱。

#### <a name="example"></a>範例

下面是一個範例提供程式列映射:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

標記提供程式列映射條目的末尾。

#### <a name="syntax"></a>語法

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>範例

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

表示提供程式支援的特定列。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>參數

*名稱*<br/>
[在]列名稱。

*序*<br/>
[in] 資料行編號。 除非列是書籤列,否則列號不得為 0。

*成員*<br/>
[在]對應於`dataClass`列的成員變數。

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

表示提供程式支援的特定列。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>參數

*名稱*<br/>
[在]列名稱。

*序*<br/>
[in] 資料行編號。 除非列是書籤列,否則列號不得為 0。

*dbtype*<br/>
[在][DBTYPE 中的](/previous-versions/windows/desktop/ms711251(v=vs.85))資料類型。

*成員*<br/>
[在]存儲數據的成員`dataClass`變數。

#### <a name="remarks"></a>備註

允許您指定欄資料類型。

#### <a name="example"></a>範例

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

表示提供程式支援的特定列。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>參數

*名稱*<br/>
[在]列名稱。

*序*<br/>
[in] 資料行編號。 除非列是書籤列,否則列號不得為 0。

*標誌*<br/>
[在]指定如何返回數據。 請參閱`dwFlags`[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的說明。

*colSize*<br/>
[在]列大小。

*dbtype*<br/>
[在]指示值的數據類型。 請參閱`wType`[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的說明。

*有效位數*<br/>
[在]指示如果*dbType* DBTYPE_NUMERIC或DBTYPE_DECIMAL,則指示獲取數據時使用的精度。 請參閱`bPrecision`[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的說明。

*規模*<br/>
[在]指示獲取數據時要使用的比例,如果 dbType 是DBTYPE_NUMERIC還是DBTYPE_DECIMAL。 請參閱`bScale`[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))中的說明。

*Guid*<br/>
架構排件 GUID。 有關架構列集及其 GUID 的清單,請參閱*OLE DB 程式師參考中的* [IDBSchemaRowset。](/previous-versions/windows/desktop/ms713686(v=vs.85))

#### <a name="remarks"></a>備註

允許您指定列的大小、資料類型、精度、比例和架構排組 GUID。

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

表示提供程式支援的特定列。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>參數

*名稱*<br/>
[在]列名稱。

*序*<br/>
[in] 資料行編號。 除非列是書籤列,否則列號不得為 0。

*大小*<br/>
[在]列大小(以位元組為單位)。

*成員*<br/>
[在]其中的成員變數`dataClass`存儲列數據。

#### <a name="remarks"></a>備註

允許您指定列大小。

#### <a name="example"></a>範例

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

表示提供程式支援的特定列。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>參數

*名稱*<br/>
[在]列名稱。

*序*<br/>
[in] 資料行編號。 除非列是書籤列,否則列號不得為 0。

*成員*<br/>
[在]存儲數據的數據類中的成員變數。

#### <a name="remarks"></a>備註

當假定列數據[為 DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))時,使用此宏。

#### <a name="example"></a>範例

請參閱[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

表示提供程式支援的特定列。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>參數

*名稱*<br/>
[在]列名稱。

*序*<br/>
[in] 資料行編號。 除非列是書籤列,否則列號不得為 0。

*dbtype*<br/>
[在][DBTYPE 中的](/previous-versions/windows/desktop/ms711251(v=vs.85))資料類型。

*大小*<br/>
[在]列大小(以位元組為單位)。

*成員*<br/>
[在]存儲數據的數據類中的成員變數。

#### <a name="remarks"></a>備註

與[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)類似,但也允許您指定列的數據類型和大小。

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

表示提供程式支援的特定列。

#### <a name="syntax"></a>語法

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>參數

*名稱*<br/>
[在]列名稱。

*序*<br/>
[in] 資料行編號。 除非列是書籤列,否則列號不得為 0。

*成員*<br/>
[在]存儲數據的數據類中的成員變數。

#### <a name="remarks"></a>備註

當列資料為空終止的 Unicode 字串時[,DBTYPE_WSTR,](/previous-versions/windows/desktop/ms711251(v=vs.85))請使用此巨集。

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

表示架構映射的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>參數

*架構類*<br/>
包含 MAP 的類。 通常,這將是會話類。

#### <a name="remarks"></a>備註

有關架構列集的詳細資訊,請參閱 Windows SDK 中的[IDBSchemaRowset。](/previous-versions/windows/desktop/ms713686(v=vs.85))

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

表示架構映射的末尾。

#### <a name="syntax"></a>語法

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>備註

有關詳細資訊,請參閱[IDBSchemaRowsetimpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)。

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

將 GUID 與類關聯。

#### <a name="syntax"></a>語法

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>參數

*Guid*<br/>
架構排件 GUID。 有關架構列集及其 GUID 的清單,請參閱*OLE DB 程式師參考中的* [IDBSchemaRowset。](/previous-versions/windows/desktop/ms713686(v=vs.85))

*排設置類*<br/>
將創建以表示架構行集的類。

#### <a name="remarks"></a>備註

[然後,IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)可以查詢地圖以尋找 GUID 的清單,或者如果為 GUID 提供了一個行集,則可以創建一個行集。 架構列集`IDBSchemaRowsetImpl`建立的類似於`CRowsetImpl`標準 派生類,只不過它必須`Execute`提供具有 以下簽名的方法:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

此`Execute`函數填充行集的數據。 ATL 專案精靈建立,如*在 OLE DB 程式師參考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))中所述,在專案中為三個必需的 OLE DB 架構中的每個模式建立三個初始架構列集:

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

嚮導還在架構映射中添加三個相應的條目。 有關使用精靈建立提供者的詳細資訊,請參閱[建立 OLE DB 樣本提供者](../../data/oledb/creating-an-ole-db-provider.md)。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程式樣本架構結構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[建立 OLE 資料庫提供者](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 提供程式樣本參考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 提供程式樣本的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)
