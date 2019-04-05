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
- SetData
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
ms.openlocfilehash: 8b2a92fdefd965d4b87e0a9ed411cc1b5c89b8f9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036795"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 類別

OLE DB 樣板實作[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) OLE DB 規格中的介面。

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
類別衍生自`IRowsetChangeImpl`。

*存放裝置*<br/>
使用者記錄中。

*BaseInterface*<br/>
基底類別的介面，例如`IRowsetChange`。

*RowClass*<br/>
資料列控制代碼儲存體單位。

*MapClass*<br/>
提供者所持有的所有資料列控制代碼儲存體單位。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods-used-with-irowsetchange"></a>（搭配 IRowsetChange） 的介面方法

|||
|-|-|
|[DeleteRows](#deleterows)|從資料列集刪除資料列。|
|[InsertRow](#insertrow)|資料列插入資料列集。|
|[SetData](#setdata)|設定一或多個資料行中的資料值。|

### <a name="implementation-method-callback"></a>實作方法 （回呼）

|||
|-|-|
|[FlushData](#flushdata)|將資料認可到其存放區提供者覆寫。|

## <a name="remarks"></a>備註

這個介面會負責立即寫入至資料存放區作業。 「 立即 」 表示，當使用者 （使用取用者的人員） 會進行任何變更，這些變更會立即傳輸至資料存放區 （且無法復原）。

`IRowsetChangeImpl` 實作 OLE DB`IRowsetChange`介面，讓更新的現有資料列，刪除資料列，並插入新資料列中的資料行的值。

OLE DB 樣板實作支援所有基底的方法 (`SetData`， `InsertRow`，和`DeleteRows`)。

> [!IMPORTANT]
>  強烈建議您先閱讀下列文件，然後再嘗試實作您的提供者：

- [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)

- 第 6 章*OLE DB 程式設計人員參考*

- 另請參閱如何`RUpdateRowset`類別用於[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例。

## <a name="deleterows"></a> IRowsetChangeImpl::DeleteRows

從資料列集刪除資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>參數

請參閱[irowsetchange:: Deleterows](/previous-versions/windows/desktop/ms724362(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="insertrow"></a> IRowsetChangeImpl::InsertRow

建立並初始化新的資料列中資料列集。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>參數

請參閱[irowsetchange:: Insertrow](/previous-versions/windows/desktop/ms716921(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="setdata"></a> IRowsetChangeImpl::SetData

設定一或多個資料行中的資料值。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>參數

請參閱[irowsetchange:: Setdata](/previous-versions/windows/desktop/ms721232(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="flushdata"></a> IRowsetChangeImpl::FlushData

將資料認可到其存放區提供者覆寫。

### <a name="syntax"></a>語法

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>參數

*hRowToFlush*<br/>
[in]資料的資料列的控制代碼。 此資料列的型別從決定*RowClass*樣板引數`IRowsetImpl`類別 (`CSimpleRow`預設情況下)。

*hAccessorToFlush*<br/>
[in]存取子，其中包含繫結資訊以及型別資訊中的控制代碼及其`PROVIDER_MAP`(請參閱 < [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md))。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)