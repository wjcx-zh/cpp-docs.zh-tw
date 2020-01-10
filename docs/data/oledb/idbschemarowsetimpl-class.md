---
title: IDBSchemaRowsetImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
ms.openlocfilehash: 3c34f84254fc57b6cd5f8b4763faac313a01636b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311783"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl 類別

提供結構描述資料列集的實作。

## <a name="syntax"></a>語法

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>參數

*SessionClass*<br/>
繼承自 `IDBSchemaRowsetImpl` 的類別。 一般而言，此類別會是使用者的工作階段類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CheckRestrictions](#checkrestrictions)|針對結構描述資料列集檢查限制的有效性。|
|[CreateSchemaRowset](#createschemarowset)|為範本參數所指定的物件實作 COM 物件建立者函式。|
|[SetRestrictions](#setrestrictions)|指定您在特定結構描述資料列集上支援的限制。|

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[GetRowset](#getrowset)|傳回結構描述資料列集。|
|[GetSchemas](#getschemas)|傳回 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)可存取的結構描述資料列集清單。|

## <a name="remarks"></a>備註

此類別實作 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 介面和範本化的建立者函式 [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)。

OLE DB 使用結構描述資料列集，傳回提供者內部資料的相關資料。 這類資料通常稱為「中繼資料」。 根據預設，提供者一律必須支援`DBSCHEMA_TABLES`、 `DBSCHEMA_COLUMNS` `DBSCHEMA_PROVIDER_TYPES`和，如 OLE DB 程式設計*人員參考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))中所述。 結構描述資料列集是在結構描述對應中指定。 如需結構描述對應項目的資訊，請參閱 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)。

[ATL 物件精靈] 中的 [OLE DB 提供者精靈] 會自動為您專案中的結構描述資料列集產生程式碼 (根據預設，此精靈支援上述的必要結構描述資料列集)。當您使用 [ATL 物件精靈] 建立消費者時，此精靈會使用結構描述資料列集，將正確的資料繫結至提供者。 如果您未實作結構描述資料列集以提供正確的中繼資料，此精靈將不會繫結正確的資料。

如需如何在提供者內支援結構描述資料列集的資訊，請參閱 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。

如需結構描述資料列集的詳細資訊，請參閱 *＜OLE DB 程式設計人員參考＞* 中的 [Schema Rowsets(結構描述資料列集)](/previous-versions/windows/desktop/ms712921(v=vs.85))。

## <a name="checkrestrictions"></a>IDBSchemaRowsetImpl：： CheckRestrictions

針對結構描述資料列集檢查限制的有效性。

### <a name="syntax"></a>語法

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>參數

*rguidSchema*<br/>
[in] 所要求之結構描述資料列集 GUID 的參考 (例如 `DBSCHEMA_TABLES`)。

*cRestrictions*<br/>
[in] 消費者針對結構描述資料列集傳入的限制數目。

*rgRestrictions*<br/>
[in] 要設定之限制值的長度 *cRestrictions* 陣列。 如需詳細資訊，請參閱[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)中*rgRestrictions*參數的描述。

### <a name="remarks"></a>備註

使用 `CheckRestrictions` 針對結構描述資料列集檢查限制的有效性。 它會檢查、 `DBSCHEMA_TABLES` `DBSCHEMA_COLUMNS`和`DBSCHEMA_PROVIDER_TYPES`架構資料列集的限制。 呼叫它來判斷取用者的呼叫`IDBSchemaRowset::GetRowset`是否正確。 如果您想要支援與以上所列不同的結構描述資料列集，您應該建立自己的函式來執行這項工作。

`CheckRestrictions`判斷取用者是否使用提供者支援的正確限制和正確限制類型（例如，字串的 VT_BSTR）來呼叫[GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) 。 它也會判斷是否支援正確的限制數目。 根據預設， `CheckRestrictions` 會透過 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 呼叫，來詢問提供者有關它在指定資料列集上支援的限制。 接著，它會將來自消費者的限制與提供者支援的限制進行比較，以判斷其為成功或失敗。

如需架構資料列集的詳細資訊，請參閱 Windows SDK 中 OLE DB 程式設計*人員參考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

## <a name="createschemarowset"></a>IDBSchemaRowsetImpl：： CreateSchemaRowset

為範本參數所指定的物件實作 COM 物件建立者函式。

### <a name="syntax"></a>語法

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>參數

*pUnkOuter*<br/>
在在匯總時為外部[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ，否則為 Null。

*cRestrictions*<br/>
[in] 套用至結構描述資料列集的限制計數。

*rgRestrictions*<br/>
[in] 要套用至資料列集的 `cRestrictions`**VARIANT**陣列。

*riid*<br/>
在要在輸出 `IUnknown`上進行 [QueryInterface](../../atl/queryinterface.md) 的介面。

*cPropertySets*<br/>
[in] 要設定的屬性集數目。

*rgPropertySets*<br/>
[in] 指定要設定之屬性的 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 結構陣列。

*ppRowset*<br/>
脫銷Riid 要求`IUnknown`的傳出。 這`IUnknown`是架構資料列集物件上的介面。

*pSchemaRowset*<br/>
[out] 結構描述資料列集類別執行個體的指標。 一般而言，您不會使用此參數；但如果您必須對結構描述資料列集執行更多工作，才能送出至 COM 物件，則可以使用此參數。 *PSchemaRowset*的存留期是由*ppRowset*所系結。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

此函式會對所有類型的結構描述資料列集實作一般建立者。 一般而言，使用者不會呼叫此函式， 而是由結構描述對應的實作進行呼叫。

## <a name="setrestrictions"></a>IDBSchemaRowsetImpl：： SetRestrictions

指定您在特定結構描述資料列集上支援的限制。

### <a name="syntax"></a>語法

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>參數

*cRestrictions*<br/>
在*RgRestrictions*陣列中的限制數目，以及*rguidSchema*陣列中的 guid 數目。

*rguidSchema*<br/>
[in] 要擷取限制之目標結構描述資料列集的 GUID 陣列。 每個陣列元素包含一個結構描述資料列集的 GUID (例如 `DBSCHEMA_TABLES`)。

*rgRestrictions*<br/>
[in] 要設定之限制值的長度 *cRestrictions* 陣列。 每個元素會對應至 GUID 所識別之結構描述資料列集上的限制。 如果提供者不支援結構描述資料列集，此元素會設定為零。 否則， **ULONG** 值會包含代表該結構描述資料列集支援之限制的位元遮罩。 如需有關哪些限制對應至特定架構資料列集的詳細資訊，請參閱 Windows SDK 中 OLE DB 程式設計*人員參考* [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))中的架構資料列集 guid 表。

### <a name="remarks"></a>備註

物件會呼叫`SetRestrictions`來決定您在特定架構資料列集上支援的限制（透過 upcasted 指標呼叫 [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)）。`IDBSchemaRowset` 限制允許消費者只擷取相符的資料列 (例如在資料表 "MyTable" 中尋找所有資料行)。 限制是選擇性的，在不支援任何限制的情況下 (預設)，一律會傳回所有資料。

這個方法的預設執行會將*rgRestrictions*陣列元素設定為0。 您可以覆寫工作階段類別中的預設，將限制設定為非預設。

如需實作結構描述資料列集支援的資訊，請參閱 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。

如需支援結構描述資料列集的提供者範例，請參閱 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 範例。

如需架構資料列集的詳細資訊，請參閱 Windows SDK 中 OLE DB 程式設計*人員參考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

## <a name="getrowset"></a>IDBSchemaRowsetImpl：： GetRowset

傳回結構描述資料列集。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>參數

*pUnkOuter*<br/>
在匯總時`IUnknown`為外部，否則為 Null。

*rguidSchema*<br/>
[in] 所要求之結構描述資料列集 GUID 的參考 (例如 `DBSCHEMA_TABLES`)。

*cRestrictions*<br/>
[in] 要套用至資料列集的限制計數。

*rgRestrictions*<br/>
[in] 代表限制的 `cRestrictions`**VARIANT**陣列。

*riid*<br/>
[in] 新建立之結構描述資料列集的要求 IID。

*cPropertySets*<br/>
[in] 要設定的屬性集數目。

*rgPropertySets*<br/>
[in/out] 要在新建立的結構描述資料列集上設定的 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 結構陣列。

*ppRowset*<br/>
[out] 新建立之結構描述資料列集上所要求的介面指標。

### <a name="remarks"></a>備註

此方法需要使用者具有工作階段類別中的結構描述對應。 如果 rguidSchema 參數等於其中一個`GetRowset`對應專案 guid，則使用架構對應資訊會建立給定的資料列集物件。 如需對應項目的說明，請參閱 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) 。

請參閱 Windows SDK 中的[IDBSchemaRowset：： GetRowset](/previous-versions/windows/desktop/ms722634(v=vs.85)) 。

## <a name="getschemas"></a>IDBSchemaRowsetImpl：： GetSchemas

傳回 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)可存取的結構描述資料列集清單。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>參數

*pcSchemas*<br/>
[out] 要填入結構描述數目的 **ULONG** 指標。

*prgSchemas*<br/>
[out] 要填入結構描述資料列集 GUID 陣列指標的 GUID 陣列指標。

*prgRest*<br/>
[out] 要填入限制陣列的 **ULONG**陣列指標。

### <a name="remarks"></a>備註

此方法會傳回提供者支援之所有結構描述資料列集的陣列。 請參閱 Windows SDK 中的[IDBSchemaRowset：： GetSchemas](/previous-versions/windows/desktop/ms719605(v=vs.85)) 。

此函式的實作需要使用者具有工作階段類別中的結構描述對應。 藉由使用此結構描述對應資訊，它就能接著以對應中結構描述的 GUID 陣列來回應。 這會是提供者支援的結構描述。

## <a name="see-also"></a>另請參閱

[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples)