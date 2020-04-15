---
title: IRowsetChangeImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: ae4ceea53ec91cc3f9593dd3789fcf61e0702274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376951"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 類別

OLE DB 範本在 OLE DB 規範中的[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))介面的實現。

## <a name="syntax"></a>語法

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>參數

*T*<br/>
派生自`IRowsetChangeImpl`的類。

*Storage*<br/>
用戶記錄。

*基本介面*<br/>
介面的基類,如`IRowsetChange`。

*行類*<br/>
行句柄的存儲單元。

*地圖類*<br/>
提供程式持有的所有行句柄的存儲單元。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods-used-with-irowsetchange"></a>介面方法(與 IRowsetChange 一起使用)

|||
|-|-|
|[刪除列](#deleterows)|從行集中刪除行。|
|[InsertRow](#insertrow)|將行插入行。|
|[設定資料](#setdata)|在一個或多個列中設置數據值。|

### <a name="implementation-method-callback"></a>實作方法(回撥)

|||
|-|-|
|[更新資料](#flushdata)|由提供程式重寫以將數據提交到其存儲。|

## <a name="remarks"></a>備註

此介面負責立即寫入數據存儲。 "立即"是指當最終使用者(使用消費者的人)進行任何更改時,這些更改將立即傳輸到數據存儲(並且無法撤銷)。

`IRowsetChangeImpl`實現 OLE `IRowsetChange` DB 介面,該介面支援更新現有列中的列值、刪除行和插入新行。

OLE 資料庫樣本支援所有基本方法 (`SetData``InsertRow`與`DeleteRows`。

> [!IMPORTANT]
> 強烈建議您在嘗試實現提供程式之前閱讀以下文件:

- [建立可上可提供者](../../data/oledb/creating-an-updatable-provider.md)

- OLE DB*程式師參考*第 6 章

- 另請參閱在`RUpdateRowset`[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例中如何使用該類。

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChange::DeleteRows

從行集中刪除行。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>參數

請參閱[IRowsetChange::D EleteRows](/previous-versions/windows/desktop/ms724362(v=vs.85))在*OLE DB 程式師的參考*中。

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowset 更改:插入行

在行集中創建和初始化新行。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>參數

請參閱[IRowset 更改:在](/previous-versions/windows/desktop/ms716921(v=vs.85)) *OLE DB 程式師參考*中插入行。

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChange::集資料

在一個或多個列中設置數據值。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>參數

請參閱[IRowset 更改:在](/previous-versions/windows/desktop/ms721232(v=vs.85)) *OLE DB 程式師參考*中設定數據。

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChange::FlushData

由提供程式重寫以將數據提交到其存儲。

### <a name="syntax"></a>語法

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>參數

*h羅托弗什*<br/>
[在]處理數據的行。 此行的類型是從`IRowsetImpl`類`CSimpleRow`的*RowClass*範本參數(預設情況下)確定的。

*h 存取器*<br/>
[在]句柄訪問器,其中包含綁定資訊和鍵入其`PROVIDER_MAP`中的資訊(請參閱[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md))。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程式樣本架構結構](../../data/oledb/ole-db-provider-template-architecture.md)
