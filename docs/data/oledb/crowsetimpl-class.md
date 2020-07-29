---
title: CRowsetImpl 類別
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 35a80503597b7e59ec10618b9c8e18e0e69f018e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221506"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl 類別

提供標準的 OLE DB 資料列集執行，而不需要多個實作為介面的繼承。

## <a name="syntax"></a>語法

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl :
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的使用者類別 `CRowsetImpl` 。

*Storage*<br/>
使用者記錄類別。

*CreatorClass*<br/>
包含資料列集屬性的類別;通常是命令。

*ArrayType*<br/>
將做為資料列集資料之儲存的類別。 這個參數預設為 `CAtlArray` ，但它可以是任何支援所需功能的類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[NameFromDBID](#namefromdbid)|從解壓縮字串 `DBID` ，並將它複製到傳入的*bstr* 。|
|[SetCommandText](#setcommandtext)|驗證並將 `DBID` s 儲存在兩個字串（[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)）中。|

### <a name="overridable-methods"></a>可覆寫的方法

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|抓取特定用戶端要求的資料行資訊。|
|[GetCommandFromID](#getcommandfromid)|檢查其中一個或兩個參數是否包含字串值，如果是，會將字串值複製到[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)的資料成員，並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|
|[ValidateCommandID](#validatecommandid)|檢查其中一個或兩個是否 `DBID` 包含字串值，如果是，則會將它們複製到其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_rgRowData](#rgrowdata)|根據預設， `CAtlArray` 會 templatizes 在使用者記錄範本引數上的 `CRowsetImpl` 。 另一個陣列型別類別可以藉由將樣板 `ArrayType` 引數變更為來使用 `CRowsetImpl` 。|
|[m_strCommandText](#strcommandtext)|包含資料列集的初始命令。|
|[m_strIndexText](#strindextext)|包含資料列集的初始索引。|

## <a name="remarks"></a>備註

`CRowsetImpl`以靜態 upcasts 的形式提供覆寫。 方法會控制給定資料列集將驗證命令文字的方式。 您可以建立您自己的 `CRowsetImpl` 樣式類別，方法是讓您的實作為介面成為多重繼承。 唯一必須提供實作為的方法是 `Execute` 。 根據您所建立的資料列集類型而定，建立者方法會預期不同的簽章 `Execute` 。 例如，如果您使用 `CRowsetImpl` 衍生類別來執行架構資料列集，則此 `Execute` 方法會具有下列簽章：

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

如果您要建立 `CRowsetImpl` 衍生類別來執行命令或會話的資料列集，此 `Execute` 方法將具有下列簽章：

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

若要執行任何 `CRowsetImpl` 衍生的 `Execute` 方法，您必須填入內部資料緩衝區（[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)）。

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a>CRowsetImpl：： NameFromDBID

從解壓縮字串 `DBID` ，並將它複製到傳入的*bstr* 。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>參數

*pDBID*<br/>
在要從中 `DBID` 解壓縮字串之的指標。

*bstr*<br/>
在要放置字串複本的[CComBSTR](../../atl/reference/ccombstr-class.md)參考 `DBID` 。

*bIndex*<br/>
[in] **`true`** 如果是索引 `DBID` ，則為; **`false`** 如果是資料表，則為 `DBID` 。

### <a name="return-value"></a>傳回值

標準 HRESULT。 視 `DBID` 是資料表或索引（以*bIndex*表示）而定，此方法會傳回 DB_E_NOINDEX 或 DB_E_NOTABLE。

### <a name="remarks"></a>備註

這個方法是由 `CRowsetImpl` [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)的實作為呼叫。

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl：： SetCommandText

驗證並將 `DBID` s 儲存在兩個字串（[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)）中。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>參數

*pTableID*<br/>
在的指標， `DBID` 表示資料表識別碼。

*pIndexID*<br/>
在的指標， `DBID` 表示索引識別碼。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

`SetCommentText`方法是由（的 `CreateRowset` 靜態範本化方法）所呼叫 `IOpenRowsetImpl` 。

這個方法會透過 upcasted 指標呼叫[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)來委派其工作。

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a>CRowsetImpl：： GetColumnInfo

抓取特定用戶端要求的資料行資訊。

### <a name="syntax"></a>語法

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>參數

*pv*<br/>
在使用者的衍生類別的指標 `CRowsetImpl` 。

*pcCols*<br/>
在傳回之資料行數目的指標（輸出）。

### <a name="return-value"></a>傳回值

靜態結構的指標 `ATLCOLUMNINFO` 。

### <a name="remarks"></a>備註

這個方法是一個先進的覆寫。

這個方法是由數個基底執行類別所呼叫，以取得特定用戶端要求的資料行資訊。 通常，會呼叫這個方法 `IColumnsInfoImpl` 。 如果您覆寫這個方法，您必須將方法的版本放在 `CRowsetImpl` 衍生類別中。 因為方法可能會放在非範本化類別中，所以您必須將*pv*變更為適當的 `CRowsetImpl` 衍生類別。

下列範例示範 `GetColumnInfo` 使用方式。 在此範例中， `CMyRowset` 是 `CRowsetImpl` 衍生類別。 若要覆寫 `GetColumnInfo` 這個類別的所有實例，請將下列方法放在 `CMyRowset` 類別定義中：

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a>CRowsetImpl：： GetCommandFromID

檢查其中一個或兩個參數是否包含字串值，如果是，會將字串值複製到[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)的資料成員，並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>參數

*pTableID*<br/>
在的指標， `DBID` 表示資料表識別碼。

*pIndexID*<br/>
在的指標， `DBID` 表示索引識別碼。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法是透過靜態向上轉換來呼叫， `CRowsetImpl` 以填入[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)的資料成員。 根據預設，這個方法會檢查其中一個或兩個參數是否包含字串值。 如果它們包含字串值，這個方法會將字串值複製到資料成員。 藉由將具有此簽章的方法放在 `CRowsetImpl` 衍生類別中，將會呼叫您的方法，而不是基底實作為。

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>CRowsetImpl：： ValidateCommandID

檢查其中一個或兩個是否 `DBID` 包含字串值，如果是，則會將它們複製到其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>參數

*pTableID*<br/>
在的指標， `DBID` 表示資料表識別碼。

*pIndexID*<br/>
在的指標， `DBID` 表示索引識別碼。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法是透過靜態向上轉換來呼叫， `CRowsetImpl` 以填入其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 根據預設，這個方法會檢查其中一個或兩個是否 `DBID` 包含字串值，如果是，則會將它們複製到其資料成員。 藉由將具有此簽章的方法放在 `CRowsetImpl` 衍生類別中，將會呼叫您的方法，而不是基底實作為。

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>CRowsetImpl：： m_rgRowData

根據預設， `CAtlArray` 會 templatizes 在使用者記錄範本引數上的 `CRowsetImpl` 。

### <a name="syntax"></a>語法

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>備註

*ArrayType*是的範本參數 `CRowsetImpl` 。

## <a name="crowsetimplm_strcommandtext"></a><a name="strcommandtext"></a>CRowsetImpl：： m_strCommandText

包含資料列集的初始命令。

### <a name="syntax"></a>語法

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="crowsetimplm_strindextext"></a><a name="strindextext"></a>CRowsetImpl：： m_strIndexText

包含資料列集的初始索引。

### <a name="syntax"></a>語法

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```
