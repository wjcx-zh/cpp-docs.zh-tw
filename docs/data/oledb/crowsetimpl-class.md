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
- GetColumnInfo
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
ms.openlocfilehash: 1fac3a74ca259fe3b680355fadc7f9bbd6e3cc13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368704"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl 類別

提供標準的 OLE DB 資料列集實作，而不需要的許多實作介面的多重繼承。

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
使用者的類別衍生自`CRowsetImpl`。

*儲存體*<br/>
使用者記錄類別。

*CreatorClass*<br/>
包含資料列集; 屬性的類別通常命令。

*ArrayType*<br/>
將做為資料列集的資料儲存體類別。 此參數預設為`CAtlArray`，但它可以是任何類別都支援必要的功能。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[NameFromDBID](#namefromdbid)|會從字串中擷取`DBID`並將它複製到*bstr*傳入。|
|[SetCommandText](#setcommandtext)|驗證並儲存`DBID`中的兩個字串 ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md))。|

### <a name="overridable-methods"></a>可覆寫方法

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|擷取特定的用戶端要求的資料行資訊。|
|[GetCommandFromID](#getcommandfromid)|檢查以查看或這兩個參數包含字串值時，如果是的話，會將字串值複製到的資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|
|[ValidateCommandID](#validatecommandid)|檢查是否有任一或兩者`DBID`s 包含字串值，而且如果是的話，將它們複製到其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_rgRowData](#rgrowdata)|根據預設，`CAtlArray`上的使用者記錄的範本引數，templatizes `CRowsetImpl`。 另一個陣列型別類別可供變更`ArrayType`樣板引數`CRowsetImpl`。|
|[m_strCommandText](#strcommandtext)|包含資料列集的初始命令。|
|[m_strIndexText](#strindextext)|包含資料列集的起始索引。|

## <a name="remarks"></a>備註

`CRowsetImpl` 提供靜態向上轉型成為表單中的覆寫。 方法會控制將在其中指定的資料列集將會驗證命令文字的方式。 您也可以建立自己`CRowsetImpl`-樣式藉由實作介面多重繼承的類別。 唯一的方法，您必須提供實作`Execute`。 根據您建立何種類型的資料列集，建立者方法就會預期收到不同的簽章的`Execute`。 例如，如果您使用`CRowsetImpl`-衍生類別來實作結構描述資料列`Execute`方法會具有下列簽章：

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

如果您要建立`CRowsetImpl`-衍生類別來實作命令或工作階段的資料列集，`Execute`方法會具有下列簽章：

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

若要實作的任何`CRowsetImpl`-衍生`Execute`方法，您必須填入您的內部資料緩衝區 ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md))。

## <a name="namefromdbid"></a> CRowsetImpl::NameFromDBID

會從字串中擷取`DBID`並將它複製到*bstr*傳入。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>參數

*pDBID*<br/>
[in]指標`DBID`要從中擷取字串。

*bstr*<br/>
[in]A [CComBSTR](../../atl/reference/ccombstr-class.md)放置一份參考`DBID`字串。

*bIndex*<br/>
[in]**真**如果索引`DBID`;**假**如果資料表`DBID`。

### <a name="return-value"></a>傳回值

標準的 HRESULT。 取決於是否`DBID`是資料表或索引 (以表示*bIndex*)，此方法會傳回 DB_E_NOINDEX 或 DB_E_NOTABLE。

### <a name="remarks"></a>備註

這個方法會呼叫`CRowsetImpl`的實作[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)並[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)。

## <a name="setcommandtext"></a> CRowsetImpl::SetCommandText

驗證並儲存`DBID`中的兩個字串 ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md))。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>參數

*pTableID*<br/>
[in]指標`DBID`代表資料表的識別碼。

*pIndexID*<br/>
[in]指標`DBID`代表索引識別碼。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

`SetCommentText`方法會呼叫`CreateRowset`，靜態樣板化的方法`IOpenRowsetImpl`。

這個方法會委派其工作，藉由呼叫[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)並[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)透過向上轉型的指標。

## <a name="getcolumninfo"></a> CRowsetImpl::GetColumnInfo

擷取特定的用戶端要求的資料行資訊。

### <a name="syntax"></a>語法

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>參數

*pv*<br/>
[in]使用者的指標`CRowsetImpl`衍生的類別。

*pcCols*<br/>
[in]指標 （輸出） 的數字傳回的資料行。

### <a name="return-value"></a>傳回值

設為靜態的指標`ATLCOLUMNINFO`結構。

### <a name="remarks"></a>備註

這個方法是進階的覆寫。

若要擷取特定的用戶端要求的資料行資訊的數個基底實作類別會呼叫這個方法。 通常，這個方法會由呼叫`IColumnsInfoImpl`。 如果您覆寫這個方法，就必須放在方法的版本您`CRowsetImpl`-衍生的類別。 由於方法可能會放在非樣板化類別中，您必須變更*pv*適當`CRowsetImpl`-衍生的類別。

下列範例示範`GetColumnInfo`使用量。 在此範例中，`CMyRowset`是`CRowsetImpl`-衍生的類別。 若要覆寫`GetColumnInfo`的這個類別的所有執行個體，將下列方法`CMyRowset`類別定義：

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="getcommandfromid"></a> CRowsetImpl::GetCommandFromID

檢查以查看或這兩個參數包含字串值時，如果是的話，會將字串值複製到的資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>參數

*pTableID*<br/>
[in]指標`DBID`代表資料表的識別碼。

*pIndexID*<br/>
[in]指標`DBID`代表索引的識別碼。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

透過靜態的向上轉型，藉由呼叫這個方法`CRowsetImpl`來填入資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 根據預設，這個方法會檢查以查看其中一個或兩個參數是否包含字串值。 如果它們包含字串值，這個方法會複製至資料成員的字串值。 將具有此簽章中的方法您`CRowsetImpl`-衍生的類別，會呼叫您的方法，而不是基底實作。

## <a name="validatecommandid"></a> CRowsetImpl::ValidateCommandID

檢查是否有任一或兩者`DBID`s 包含字串值，而且如果是的話，將它們複製到其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。

### <a name="syntax"></a>語法

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>參數

*pTableID*<br/>
[in]指標`DBID`代表資料表的識別碼。

*pIndexID*<br/>
[in]指標`DBID`代表索引識別碼。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

透過靜態的向上轉型，藉由呼叫這個方法`CRowsetImpl`填入其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)並[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 根據預設，這個方法會檢查是否有任一或兩者`DBID`s 包含字串值，而且如果是的話，將它們複製到其資料成員。 將具有此簽章中的方法您`CRowsetImpl`-衍生的類別，會呼叫您的方法，而不是基底實作。

## <a name="rgrowdata"></a> CRowsetImpl::m_rgRowData

根據預設，`CAtlArray`上的使用者記錄的範本引數，templatizes `CRowsetImpl`。

### <a name="syntax"></a>語法

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>備註

*ArrayType*為範本參數`CRowsetImpl`。

## <a name="strcommandtext"></a> CRowsetImpl::m_strCommandText

包含資料列集的初始命令。

### <a name="syntax"></a>語法

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="strindextext"></a> CRowsetImpl::m_strIndexText

包含資料列集的起始索引。

### <a name="syntax"></a>語法

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```