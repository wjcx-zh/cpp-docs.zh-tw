---
title: IRowsetImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: 2fbe461bfc812c5ac9b9a09aa3ed31c0a2a638e1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447355"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl 類別

提供 `IRowset` 介面的實作。

## <a name="syntax"></a>語法

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IRowsetImpl`的類別。

*RowsetInterface*<br/>
衍生自 `IRowsetImpl`的類別。

*RowClass*<br/>
`HROW`的儲存單位。

*MapClass*<br/>
提供者所持有之所有資料列控制碼的儲存單位。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddRefRows](#addrefrows)|將參考次數 (Reference Count) 加入至現有的資料列控制代碼。|
|[CreateRow](#createrow)|由[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)呼叫以配置新的 `HROW`。 不是由使用者直接呼叫。|
|[GetData](#getdata)|從資料列集的資料列複本擷取資料。|
|[GetDBStatus](#getdbstatus)|傳回指定欄位的狀態。|
|[GetNextRows](#getnextrows)|循序擷取資料列，並且會記住上一個位置。|
|[IRowsetImpl](#irowsetimpl)|建構函式。 不是由使用者直接呼叫。|
|[RefRows](#refrows)|由[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)和[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)呼叫。 不是由使用者直接呼叫。|
|[ReleaseRows](#releaserows)|釋放資料列。|
|[RestartPosition](#restartposition)|將下一個提取位置重新置放到其初始位置;也就是，第一次建立資料列集的位置。|
|[SetDBStatus](#setdbstatus)|設定指定欄位的狀態旗標。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|指出提供者是否支援反向提取。|
|[m_bCanScrollBack](#bcanscrollback)|指出提供者是否可以將其游標向後滾動。|
|[m_bReset](#breset)|指出提供者是否已重設其游標位置。 在[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)中向後或向後滾動時，這會有特殊意義。|
|[m_iRowset](#irowset)|資料列集的索引，代表資料指標。|
|[m_rgRowHandles](#rgrowhandles)|資料列控制碼清單。|

## <a name="remarks"></a>備註

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))是基底資料列集介面。

## <a name="addrefrows"></a>IRowsetImpl：： AddRefRows

將參考次數 (Reference Count) 加入至現有的資料列控制代碼。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：： AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) 。

## <a name="createrow"></a>IRowsetImpl：： CreateRow

由[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)呼叫的 helper 方法，用來配置新的 `HROW`。

### <a name="syntax"></a>語法

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>參數

*lRowsOffset*<br/>
正在建立之資料列的資料指標位置。

*cRowsObtained*<br/>
傳回給使用者的參考，指出已建立的資料列數目。

*rgRows*<br/>
`HROW`的陣列，傳回至具有新建立之資料列控制碼的呼叫端。

### <a name="remarks"></a>備註

如果資料列存在，這個方法會呼叫[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)並傳回。 否則，它會配置 RowClass 範本變數的新實例，並將它新增至[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)。

## <a name="getdata"></a>IRowsetImpl：：操作

從資料列集的資料列複本擷取資料。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：：執行](/previous-versions/windows/desktop/ms716988(v=vs.85))程式。

某些參數會對應至 OLE DB 程式設計*人員的*不同名稱參考參數，如 `IRowset::GetData`所述：

|OLE DB 範本參數|*OLE DB 程式設計人員的參考*參數|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>備註

也會使用 OLE DB 的資料轉換 DLL 來處理資料轉換。

## <a name="getdbstatus"></a>IRowsetImpl：： GetDBStatus

傳回指定欄位的 DBSTATUS 狀態旗標。

### <a name="syntax"></a>語法

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>參數

*.Currentrow*<br/>
在目前的資料列。

*columnNames*<br/>
在正在要求其狀態的資料行。

### <a name="return-value"></a>傳回值

資料行的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))旗標。

## <a name="getnextrows"></a>IRowsetImpl：： GetNextRows

循序擷取資料列，並且會記住上一個位置。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：： GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) 。

## <a name="irowsetimpl"></a>IRowsetImpl：： IRowsetImpl

建構函式。

### <a name="syntax"></a>語法

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>備註

您通常不需要直接呼叫這個方法。

## <a name="refrows"></a>IRowsetImpl：： RefRows

由[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)和[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)呼叫，以遞增或釋放現有資料列控制碼的參考計數。

### <a name="syntax"></a>語法

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：： AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="releaserows"></a>IRowsetImpl：： ReleaseRows

釋放資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：： ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) 。

## <a name="restartposition"></a>IRowsetImpl：： RestartPosition

將下一個提取位置重新置放到其初始位置;也就是，第一次建立資料列集的位置。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：： RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) 。

### <a name="remarks"></a>備註

在呼叫 `GetNextRow` 之前，不會定義資料列集位置。 您可以藉由呼叫 `RestartPosition` 然後向前提取或向後移動，在 rowet 中向後移動。

## <a name="setdbstatus"></a>IRowsetImpl：： SetDBStatus

設定指定欄位的 DBSTATUS 狀態旗標。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>參數

*statusFlags*<br/>
要為數據行設定的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))旗標。

*.Currentrow*<br/>
目前的資料列。

*columnInfo*<br/>
要設定其狀態的資料行。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

提供者會覆寫這個函式，以提供 DBSTATUS_S_ISNull 和 DBSTATUS_S_DEFAULT 的特殊處理。

## <a name="bcanfetchback"></a>IRowsetImpl：： m_bCanFetchBack

指出提供者是否支援反向提取。

### <a name="syntax"></a>語法

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>備註

連結至 `DBPROPSET_ROWSET` 群組中的 `DBPROP_CANFETCHBACKWARDS` 屬性。 提供者必須支援 `DBPROP_CANFETCHBACKWARDS`，才能讓 `m_bCanFetchBackwards` 為**true**。

## <a name="bcanscrollback"></a>IRowsetImpl：： m_bCanScrollBack

指出提供者是否可以將其游標向後滾動。

### <a name="syntax"></a>語法

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>備註

連結至 `DBPROPSET_ROWSET` 群組中的 `DBPROP_CANSCROLLBACKWARDS` 屬性。 提供者必須支援 `DBPROP_CANSCROLLBACKWARDS`，才能讓 `m_bCanFetchBackwards` 為**true**。

## <a name="breset"></a>IRowsetImpl：： m_bReset

位旗標，用來判斷資料指標位置是否定義在資料列集上。

### <a name="syntax"></a>語法

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>備註

如果取用者以負數 `lOffset` 或*cRows*呼叫[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) ，而 `m_bReset` 為 true，`GetNextRows` 會移到資料列集的結尾。 如果 `m_bReset` 為 false，取用者會收到錯誤碼，符合 OLE DB 規格。 第一次建立資料列集時，以及取用者呼叫[IRowsetImpl：： RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)時，`m_bReset` 旗標會設定為**true** 。 當您呼叫 `GetNextRows`時，它會設定為**false** 。

## <a name="irowset"></a>IRowsetImpl：： m_iRowset

資料列集的索引，代表資料指標。

### <a name="syntax"></a>語法

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="rgrowhandles"></a>IRowsetImpl：： m_rgRowHandles

目前提供者所包含的資料列控制碼對應，以回應 `GetNextRows`。

### <a name="syntax"></a>語法

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>備註

藉由呼叫 `ReleaseRows`來移除資料列控制碼。 如需*MapClass*的定義，請參閱[IRowsetImpl 總覽](../../data/oledb/irowsetimpl-class.md)。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow 類別](../../data/oledb/csimplerow-class.md)