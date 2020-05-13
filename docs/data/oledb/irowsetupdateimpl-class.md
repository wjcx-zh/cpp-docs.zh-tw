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
ms.openlocfilehash: 6347a42b9065239f768c6b50c430946393358df1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370739"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 類別

[IRowset 更新](/previous-versions/windows/desktop/ms714401(v=vs.85))介面的 OLE 資料庫範本實現。

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
派生自`IRowsetUpdateImpl`的類。

*Storage*<br/>
用戶記錄。

*更新陣列*<br/>
包含用於更新列集的緩存數據的陣列。

*行類*<br/>
的`HROW`存儲單元。

*地圖類*<br/>
提供程式持有的所有行句柄的存儲單元。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods-used-with-irowsetchange"></a>介面方法(與 IRowsetChange 一起使用)

|||
|-|-|
|[設定資料](#setdata)|在一個或多個列中設置數據值。|

### <a name="interface-methods-used-with-irowsetupdate"></a>介面方法(與 IRowset 更新一起使用)

|||
|-|-|
|[取得原始資料](#getoriginaldata)|獲取最近傳輸到數據源或從數據源獲取的數據,而忽略掛起的更改。|
|[取得暫停的列](#getpendingrows)|返回具有掛起更改的行的清單。|
|[取得羅維狀態](#getrowstatus)|返回指定行的狀態。|
|[復原](#undo)|撤銷自上次提取或更新以來對行的任何更改。|
|[更新](#update)|傳輸自上次提取或更新以來對行所做的任何更改。|

### <a name="implementation-methods-callback"></a>實作方法(回撥)

|||
|-|-|
|[已更新允許](#isupdateallowed)|用於在允許更新之前檢查安全性、完整性等。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|包含延遲操作的原始數據。|

## <a name="remarks"></a>備註

您應該首先閱讀並理解[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))的文檔,因為此處描述的所有內容也適用於此處。 您還應閱讀 OLE DB 程式師關於設定資料的*參考的第*6 章。

`IRowsetUpdateImpl`實現 OLE `IRowsetUpdate` DB 介面,使使用者`IRowsetChange`能夠延遲對資料源所做的更改的傳輸,並在傳輸之前撤銷更改。

> [!IMPORTANT]
> 強烈建議您在嘗試實現提供程式之前閱讀以下文件:

- [建立可上可提供者](../../data/oledb/creating-an-updatable-provider.md)

- OLE DB*程式師參考*第 6 章

- 另請參閱在`RUpdateRowset`[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例中如何使用類別

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowset 更新::集資料

在一個或多個列中設置數據值。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>參數

請參閱[IRowset 更改:在](/previous-versions/windows/desktop/ms721232(v=vs.85)) *OLE DB 程式師參考*中設定數據。

### <a name="remarks"></a>備註

此方法重寫[IRowsetChangeImpl:setData](../../data/oledb/irowsetchangeimpl-setdata.md)方法,但包括原始數據的緩存,以允許立即或延遲處理操作。

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowset 更新::取得原始資料

獲取最近傳輸到數據源或從數據源獲取的數據,而忽略掛起的更改。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>參數

請參閱[IRowset 更新:在](/previous-versions/windows/desktop/ms709947(v=vs.85))OLE *DB 程式師的參考*中獲取原始數據。

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowset 更新::取得待定行

返回具有掛起更改的行的清單。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>參數

*h 保留*<br/>
[在]對應於 IRowset 更新中的*h 章節*參數[::獲取掛起的行。](/previous-versions/windows/desktop/ms719626(v=vs.85))

有關其他參數,請參閱[IRowset 更新::在](/previous-versions/windows/desktop/ms719626(v=vs.85))OLE *DB 程式師的參考*中獲取待定行。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[IRowset 更新:在](/previous-versions/windows/desktop/ms719626(v=vs.85))OLE DB*程式師的參考*中獲取待定行。

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowset 更新::取得行羅狀態

返回指定行的狀態。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>參數

*h 保留*<br/>
[在]對應於 IRowset 更新中的*h 章*[參數 :getRow 狀態](/previous-versions/windows/desktop/ms724377(v=vs.85))。

有關其他參數,請參閱[IRowset 更新:在](/previous-versions/windows/desktop/ms724377(v=vs.85)) *OLE DB 程式師的參考*中獲取羅維狀態。

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowset 更新::撤銷

撤銷自上次提取或更新以來對行的任何更改。

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

*h 保留*<br/>
[在]對應於[IRowsetUpdate](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*h 章*參數::復原 。

*pcRowsUndone*<br/>
[出]對應於[IRowsetUpdate](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*pcRows*參數::復原 。

*prgRowsUndone*<br/>
[在]對應於[IRowsetUpdate](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*prgRows*參數::撤銷 。

有關其他參數,請參閱[IRowsetUpdate::](/previous-versions/windows/desktop/ms719655(v=vs.85))在 OLE *DB 程式師的參考*中撤銷。

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowset 更新::更新

傳輸自上次提取或更新以來對行所做的任何更改。

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

*h 保留*<br/>
[在]對應於 IRowset 更新中的*h 章*[參數 ::更新](/previous-versions/windows/desktop/ms719709(v=vs.85))。

有關其他參數,請參閱[IRowsetUpdate::](/previous-versions/windows/desktop/ms719709(v=vs.85))*在 OLE DB 程式師參考*中更新。

### <a name="remarks"></a>備註

更改通過調用[IRowsetChangeImpl::flushData](../../data/oledb/irowsetchangeimpl-flushdata.md)傳輸。 使用者必須調用[CRowset::更新](../../data/oledb/crowset-update.md),以便更改生效。 將*prgRow 狀態*設定為適當的值,如*OLE DB 程式師參考*中的[行狀態](/previous-versions/windows/desktop/ms722752(v=vs.85))中所述。

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowset 更新::是否已更新允許

重寫此方法以在更新之前檢查安全性、完整性等。

### <a name="syntax"></a>語法

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>參數

*狀態*<br/>
[在]行上掛起操作的狀態。

*h羅更新*<br/>
[在]處理使用者要更新的行。

*p 羅狀態*<br/>
[出]狀態返回給使用者。

### <a name="remarks"></a>備註

如果確定應允許更新,請返回S_OK;否則返回E_FAIL。 如果允許更新,還需要`DBROWSTATUS`在[IRowsetUpdateImpl::更新](../../data/oledb/irowsetupdateimpl-update.md)到適當的[行狀態](/previous-versions/windows/desktop/ms722752(v=vs.85))。

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowset 更新::m_mapCachedData

包含延遲操作的原始數據的映射。

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
處理數據的行。

*pData*<br/>
指向要緩存的數據的指標。 數據的類型為*存儲*(使用者記錄類)。 請參閱[IRowsetUpdateImpl 類](../../data/oledb/irowsetupdateimpl-class.md)中的*儲存*範本參數。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程式樣本架構結構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[建立可上可提供者](../../data/oledb/creating-an-updatable-provider.md)
