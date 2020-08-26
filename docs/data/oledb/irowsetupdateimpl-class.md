---
title: IRowsetUpdateImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: 7a63062a02ebcc6c8a89fadceb36dc81bc9af88c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844921"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 類別

[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))介面的 OLE DB 範本執行。

## <a name="syntax"></a>語法

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IRowsetUpdateImpl` 。

*Storage*<br/>
使用者記錄。

*UpdateArray*<br/>
陣列，其中包含用來更新資料列集的快取資料。

*RowClass*<br/>
的儲存單位 `HROW` 。

*MapClass*<br/>
提供者所保留的所有資料列控制碼的儲存單位。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods-used-with-irowsetchange"></a>介面方法 (與 IRowsetChange) 搭配使用

| 名稱 | 描述 |
|-|-|
|[SetData](#setdata)|設定一或多個資料行中的資料值。|

### <a name="interface-methods-used-with-irowsetupdate"></a>介面方法 (與 IRowsetUpdate) 搭配使用

| 名稱 | 描述 |
|-|-|
|[GetOriginalData](#getoriginaldata)|取得最近傳送至或從資料來源取得的資料，並忽略暫止的變更。|
|[GetPendingRows](#getpendingrows)|傳回包含暫止變更的資料列清單。|
|[GetRowStatus](#getrowstatus)|傳回指定資料列的狀態。|
|[復原](#undo)|復原自上次提取或更新之後對資料列所做的任何變更。|
|[更新](#update)|傳輸自上次提取或更新之後對資料列所做的任何變更。|

### <a name="implementation-methods-callback"></a> (回呼的實方法) 

| 名稱 | 描述 |
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|在允許更新之前，用來檢查安全性、完整性等等。|

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|-|-|
|[m_mapCachedData](#mapcacheddata)|包含延遲作業的原始資料。|

## <a name="remarks"></a>備註

您應該先閱讀並瞭解 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))的檔，因為這裡所述的所有內容也適用于此處。 您也應該閱讀 OLE DB 程式設計 *人員參考* 資料的第6章。

`IRowsetUpdateImpl` 會執行 OLE DB `IRowsetUpdate` 介面，此介面可讓取用者延遲傳送 `IRowsetChange` 到資料來源的變更，並在傳輸之前復原變更。

> [!IMPORTANT]
> 強烈建議您先閱讀下列檔，然後再嘗試執行您的提供者：

- [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)

- OLE DB 程式設計*人員參考*的第6章

- 另請參閱 `RUpdateRowset` [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 範例中的類別使用方式

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a> IRowsetUpdateImpl：： SetData

設定一或多個資料行中的資料值。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetChange：： SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) 。

### <a name="remarks"></a>備註

這個方法會覆寫 [IRowsetChangeImpl：： SetData](../../data/oledb/irowsetchangeimpl-setdata.md) 方法，但會包含原始資料的快取，以允許立即或延遲的工作處理。

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a> IRowsetUpdateImpl：： GetOriginalData

取得最近傳送至或從資料來源取得的資料，並忽略暫止的變更。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetUpdate：： GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) 。

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a> IRowsetUpdateImpl：： GetPendingRows

傳回包含暫止變更的資料列清單。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>參數

*hReserved*<br/>
在對應至[IRowsetUpdate：： GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85))中的*hChapter*參數。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetUpdate：： GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) 。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetUpdate：： GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) 。

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a> IRowsetUpdateImpl：： GetRowStatus

傳回指定資料列的狀態。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>參數

*hReserved*<br/>
在對應至[IRowsetUpdate：： GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85))中的*hChapter*參數。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetUpdate：： GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) 。

## <a name="irowsetupdateimplundo"></a><a name="undo"></a> IRowsetUpdateImpl：： Undo

復原自上次提取或更新之後對資料列所做的任何變更。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>參數

*hReserved*<br/>
在對應至[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*hChapter*參數。

*pcRowsUndone*<br/>
擴展對應至[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*pcRows*參數。

*prgRowsUndone*<br/>
在對應至[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*prgRows*參數。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) 。

## <a name="irowsetupdateimplupdate"></a><a name="update"></a> IRowsetUpdateImpl：： Update

傳輸自上次提取或更新之後對資料列所做的任何變更。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>參數

*hReserved*<br/>
在對應至[IRowsetUpdate：： Update](/previous-versions/windows/desktop/ms719709(v=vs.85))中的*hChapter*參數。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetUpdate：： Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) 。

### <a name="remarks"></a>備註

藉由呼叫 [IRowsetChangeImpl：： FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)來傳送變更。 取用者必須呼叫 [CRowset：： Update](../../data/oledb/crowset-update.md) ，變更才會生效。 將*prgRowstatus*設定為適當的值，如《 OLE DB 程式設計*人員參考*》中的資料[列狀態](/previous-versions/windows/desktop/ms722752(v=vs.85))所述。

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a> IRowsetUpdateImpl：： IsUpdateAllowed

覆寫此方法以在更新之前檢查安全性、完整性等等。

### <a name="syntax"></a>語法

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>參數

*status*<br/>
在資料列上暫止作業的狀態。

*hRowUpdate*<br/>
在使用者想要更新之資料列的控制碼。

*pRowStatus*<br/>
擴展傳回給使用者的狀態。

### <a name="remarks"></a>備註

如果您判斷應該允許更新，則會傳回 S_OK;否則會傳回 E_FAIL。 如果您允許更新，您也必須將 `DBROWSTATUS` [IRowsetUpdateImpl：： update](../../data/oledb/irowsetupdateimpl-update.md) 中的設定為適當的資料 [列狀態](/previous-versions/windows/desktop/ms722752(v=vs.85))。

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a> IRowsetUpdateImpl：： m_mapCachedData

包含延遲作業之原始資料的對應。

### <a name="syntax"></a>語法

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>參數

*hRow*<br/>
資料的資料列控制碼。

*.Pdata*<br/>
要快取之資料的指標。 資料的類型為「 *儲存體* 」 (使用者記錄類別) 。 請參閱[IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)中的*儲存體*範本引數。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)
