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
ms.openlocfilehash: 27a07d10256147d3c3ed383744ba1ee5fdfd06a1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504073"
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
衍生自的類別 `IRowsetImpl` 。

*RowsetInterface*<br/>
衍生自的類別 `IRowsetImpl` 。

*RowClass*<br/>
的儲存單位 `HROW` 。

*MapClass*<br/>
提供者所保留的所有資料列控制碼的儲存單位。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[AddRefRows](#addrefrows)|將參考次數 (Reference Count) 加入至現有的資料列控制代碼。|
|[CreateRow](#createrow)|由 [GetNextRows](#getnextrows) 呼叫以配置新的 `HROW` 。 未直接由使用者呼叫。|
|[GetData](#getdata)|從資料列集的資料列複本擷取資料。|
|[GetDBStatus](#getdbstatus)|傳回指定之欄位的狀態。|
|[GetNextRows](#getnextrows)|循序擷取資料列，並且會記住上一個位置。|
|[IRowsetImpl](#irowsetimpl)|建構函式。 未直接由使用者呼叫。|
|[RefRows](#refrows)|由 [AddRefRows](#addrefrows) 和 [ReleaseRows](#releaserows)呼叫。 未直接由使用者呼叫。|
|[ReleaseRows](#releaserows)|釋放資料列。|
|[RestartPosition](#restartposition)|將下一個提取位置重新置放到其初始位置;也就是說，它是在第一次建立資料列集時的位置。|
|[SetDBStatus](#setdbstatus)|設定指定之欄位的狀態旗標。|

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|指出提供者是否支援反向提取。|
|[m_bCanScrollBack](#bcanscrollback)|指出提供者是否可以將其游標向後滾動。|
|[m_bReset](#breset)|指出提供者是否已重設其資料指標位置。 在 [GetNextRows](#getnextrows)中向前或向後滾動時，這會有特殊意義。|
|[m_iRowset](#irowset)|資料列集的索引，表示資料指標。|
|[m_rgRowHandles](#rgrowhandles)|資料列控制碼的清單。|

## <a name="remarks"></a>備註

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) 是基底資料列集介面。

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a> IRowsetImpl：： AddRefRows

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

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a> IRowsetImpl：： CreateRow

[GetNextRows](#getnextrows)呼叫的 helper 方法，可配置新的 `HROW` 。

### <a name="syntax"></a>語法

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>參數

*lRowsOffset*<br/>
正在建立之資料列的游標位置。

*cRowsObtained*<br/>
傳回給使用者的參考，指出所建立的資料列數目。

*rgRows*<br/>
的陣列，這個陣列會 `HROW` 傳回給呼叫端與新建立的資料列控制碼。

### <a name="remarks"></a>備註

如果資料列存在，這個方法會呼叫 [AddRefRows](#addrefrows) 並傳回。 否則，它會配置 RowClass 範本變數的新實例，並將它新增至 [m_rgRowHandles](#rgrowhandles)。

## <a name="irowsetimplgetdata"></a><a name="getdata"></a> IRowsetImpl：：：：的

從資料列集的資料列複本擷取資料。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：：：：](/previous-versions/windows/desktop/ms716988(v=vs.85)) 。

某些參數會對應至不同名稱 OLE DB 程式設計 *人員參考* 參數，如中所述 `IRowset::GetData` ：

|OLE DB 範本參數|*OLE DB 程式設計人員的參考* 參數|
|--------------------------------|------------------------------------------------|
|*pDstData*|*.Pdata*|

### <a name="remarks"></a>備註

也會使用 OLE DB 資料轉換 DLL 來處理資料轉換。

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a> IRowsetImpl：： GetDBStatus

傳回指定之欄位的 DBSTATUS 狀態旗標。

### <a name="syntax"></a>語法

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>參數

*.Currentrow*<br/>
在目前的資料列。

*columnNames*<br/>
在要求狀態的資料行。

### <a name="return-value"></a>傳回值

資料行的 [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) 旗標。

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a> IRowsetImpl：： GetNextRows

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

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a> IRowsetImpl：： IRowsetImpl

建構函式。

### <a name="syntax"></a>語法

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>備註

您通常不需要直接呼叫這個方法。

## <a name="irowsetimplrefrows"></a><a name="refrows"></a> IRowsetImpl：： RefRows

由 [AddRefRows](#addrefrows) 和 [ReleaseRows](#releaserows) 呼叫，以將參考計數遞增或釋放至現有的資料列控制碼。

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

標準 HRESULT 值。

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a> IRowsetImpl：： ReleaseRows

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

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a> IRowsetImpl：： RestartPosition

將下一個提取位置重新置放到其初始位置;也就是說，它是在第一次建立資料列集時的位置。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：： RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) 。

### <a name="remarks"></a>備註

在呼叫之前，不會定義資料列集位置 `GetNextRow` 。 您可以藉由呼叫 `RestartPosition` ，然後再提取或向前滾動，在 rowet 中向後移動。

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a> IRowsetImpl：： SetDBStatus

設定指定之欄位的 DBSTATUS 狀態旗標。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>參數

*statusFlags*<br/>
要為數據行設定的 [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) 旗標。

*.Currentrow*<br/>
目前的資料列。

*columnInfo*<br/>
要設定其狀態的資料行。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

提供者會覆寫此函數，以提供 DBSTATUS_S_ISNull 和 DBSTATUS_S_DEFAULT 的特殊處理。

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a> IRowsetImpl：： m_bCanFetchBack

指出提供者是否支援反向提取。

### <a name="syntax"></a>語法

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>備註

連結至 `DBPROP_CANFETCHBACKWARDS` 群組中的屬性 `DBPROPSET_ROWSET` 。 提供者必須支援 `DBPROP_CANFETCHBACKWARDS` `m_bCanFetchBackwards` 成為 **`true`** 。

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a> IRowsetImpl：： m_bCanScrollBack

指出提供者是否可以將其游標向後滾動。

### <a name="syntax"></a>語法

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>備註

連結至 `DBPROP_CANSCROLLBACKWARDS` 群組中的屬性 `DBPROPSET_ROWSET` 。 提供者必須支援 `DBPROP_CANSCROLLBACKWARDS` `m_bCanFetchBackwards` 成為 **`true`** 。

## <a name="irowsetimplm_breset"></a><a name="breset"></a> IRowsetImpl：： m_bReset

用來判斷資料指標位置是否在資料列集上定義的位旗標。

### <a name="syntax"></a>語法

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>備註

如果取用者以負值或 >crows 呼叫[GetNextRows](#getnextrows) ， `lOffset` *cRows*且 `m_bReset` 為 true，則會 `GetNextRows` 移至資料列集的結尾。 如果 `m_bReset` 為 false，取用者會收到錯誤碼，並符合 OLE DB 規格。 `m_bReset` **`true`** 當第一次建立資料列集時，以及當取用者呼叫[IRowsetImpl：： RestartPosition](#restartposition)時，旗標會設為。 當您呼叫時，它會設為 **`false`** `GetNextRows` 。

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a> IRowsetImpl：： m_iRowset

資料列集的索引，表示資料指標。

### <a name="syntax"></a>Syntax

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a> IRowsetImpl：： m_rgRowHandles

目前提供者所包含的資料列控制碼對應，以回應 `GetNextRows` 。

### <a name="syntax"></a>語法

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>備註

藉由呼叫來移除資料列控制碼 `ReleaseRows` 。 如需*MapClass*的定義，請參閱[IRowsetImpl 總覽](../../data/oledb/irowsetimpl-class.md)。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow 類別](../../data/oledb/csimplerow-class.md)
