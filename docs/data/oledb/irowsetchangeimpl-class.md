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
ms.openlocfilehash: b069cd08814855a0528806ac6d19ed8f5beb6f37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210453"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 類別

OLE DB 規格中[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))介面的 OLE DB 範本執行。

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
衍生自 `IRowsetChangeImpl`的類別。

*Storage*<br/>
使用者記錄。

*Typeinterface*<br/>
介面的基底類別，例如 `IRowsetChange`。

*RowClass*<br/>
資料列控制碼的儲存單位。

*MapClass*<br/>
提供者所持有之所有資料列控制碼的儲存單位。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods-used-with-irowsetchange"></a>介面方法（與 IRowsetChange 搭配使用）

|||
|-|-|
|[DeleteRows](#deleterows)|從資料列集刪除資料列。|
|[InsertRow](#insertrow)|將資料列插入資料列集。|
|[SetData](#setdata)|設定一或多個資料行中的資料值。|

### <a name="implementation-method-callback"></a>執行方法（回呼）

|||
|-|-|
|[FlushData](#flushdata)|由提供者覆寫，以將資料認可至其存放區。|

## <a name="remarks"></a>備註

此介面負責對資料存放區進行立即寫入作業。 「立即」表示當使用者（使用取用者的人）進行任何變更時，這些變更會立即傳送到資料存放區（而且無法復原）。

`IRowsetChangeImpl` 會執行 OLE DB `IRowsetChange` 介面，這可讓您更新現有資料列中的資料行值、刪除資料列，以及插入新的資料列。

OLE DB 範本的實作為支援所有基底方法（`SetData`、`InsertRow`和 `DeleteRows`）。

> [!IMPORTANT]
>  強烈建議您先閱讀下列檔，然後再嘗試執行提供者：

- [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)

- OLE DB 程式設計*人員參考*的第6章

- 另請參閱[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例中使用 `RUpdateRowset` 類別的方式。

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl：:D eleteRows

從資料列集刪除資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetChange：:D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) 。

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl：： InsertRow

建立並初始化資料列集中的新資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetChange：： InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) 。

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl：： SetData

設定一或多個資料行中的資料值。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetChange：： SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) 。

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl：： FlushData

由提供者覆寫，以將資料認可至其存放區。

### <a name="syntax"></a>語法

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>參數

*hRowToFlush*<br/>
在資料列的控制碼。 這個資料列的型別是從 `IRowsetImpl` 類別的*RowClass*樣板引數（預設為`CSimpleRow`）來決定。

*hAccessorToFlush*<br/>
在存取子的控制碼，其中包含其 `PROVIDER_MAP` 中的系結資訊和類型資訊（請參閱[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)）。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
