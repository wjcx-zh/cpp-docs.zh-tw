---
title: IRowsetImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- AddRefRows
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
- IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- ReleaseRows
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
ms.openlocfilehash: a1826155bec3313afe503ee1c58f786a5c4739e8
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556981"
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
您的類別，衍生自`IRowsetImpl`。

*RowsetInterface*<br/>
類別衍生自`IRowsetImpl`。

*RowClass*<br/>
儲存體單位`HROW`。

*MapClass*<br/>
提供者所持有的所有資料列控制代碼的儲存體單位。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddRefRows](#addrefrows)|將現有的資料列控制代碼的參考計數。|
|[CreateRow](#createrow)|由呼叫[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)配置新`HROW`。 不直接由使用者呼叫。|
|[GetData](#getdata)|資料擷取的資料列的資料列集的副本。|
|[GetDBStatus](#getdbstatus)|傳回指定之欄位的狀態。|
|[GetNextRows](#getnextrows)|記住先前的位置，循序提取資料列。|
|[IRowsetImpl](#irowsetimpl)|建構函式。 不直接由使用者呼叫。|
|[RefRows](#refrows)|由呼叫[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)並[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)。 不直接由使用者呼叫。|
|[ReleaseRows](#releaserows)|釋放資料列。|
|[RestartPosition](#restartposition)|重新定位至其初始位置; 的下一個提取位置也就是它的位置，第一個資料列集時建立。|
|[SetDBStatus](#setdbstatus)|設定指定之欄位的狀態旗標。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|指出提供者是否支援回溯擷取。|
|[m_bCanScrollBack](#bcanscrollback)|指出是否提供者可以具有其資料指標捲動回溯。|
|[m_bReset](#breset)|指出提供者是否已重設其資料指標位置。 這具有回溯捲動或向後在擷取時的特殊意義[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)。|
|[m_iRowset](#irowset)|表示資料指標的資料列集的索引。|
|[m_rgRowHandles](#rgrowhandles)|資料列控制代碼清單。|

## <a name="remarks"></a>備註

[IRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms720986(v=vs.85))是基底的資料列集介面。

## <a name="addrefrows"></a> Irowsetimpl:: Addrefrows

將現有的資料列控制代碼的參考計數。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>參數

請參閱[irowset:: Addrefrows](https://docs.microsoft.com/previous-versions/windows/desktop/ms719619(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="createrow"></a> Irowsetimpl:: Createrow

所呼叫的協助程式方法[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)配置新`HROW`。

### <a name="syntax"></a>語法

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>參數

*lRowsOffset*<br/>
正在建立的資料列的資料指標位置。

*cRowsObtained*<br/>
參考傳回給使用者指出建立的資料列數目。

*rgRows*<br/>
陣列`HROW`傳回給呼叫者的新建立的資料列控點。

### <a name="remarks"></a>備註

如果資料列存在，這個方法會呼叫[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) ，並傳回。 否則，會配置 RowClass 範本變數的新執行個體，並將它加入[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)。

## <a name="getdata"></a> Irowsetimpl:: Getdata

資料擷取的資料列的資料列集的副本。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>參數

請參閱[irowset:: Getdata](https://docs.microsoft.com/previous-versions/windows/desktop/ms716988(v=vs.85))中*OLE DB 程式設計人員參考*。

某些參數會對應至*OLE DB 程式設計人員參考*參數中所述的不同名稱的`IRowset::GetData`:

|OLE DB 範本參數|*OLE DB 程式設計人員參考*參數|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>備註

也會處理資料轉換使用 OLE DB 資料轉換 DLL。

## <a name="getdbstatus"></a> Irowsetimpl:: Getdbstatus

傳回指定之欄位的 DBSTATUS 狀態旗標。

### <a name="syntax"></a>語法

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>參數

*currentRow*<br/>
[in]目前的資料列。

*columnNames*<br/>
[in]所要求的狀態資料行。

### <a name="return-value"></a>傳回值

[DBSTATUS](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85))旗標資料行。

## <a name="getnextrows"></a> Irowsetimpl:: Getnextrows

記住先前的位置，循序提取資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>參數

請參閱[irowset:: Getnextrows](https://docs.microsoft.com/previous-versions/windows/desktop/ms709827(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="irowsetimpl"></a> Irowsetimpl:: Irowsetimpl

建構函式。

### <a name="syntax"></a>語法

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>備註

您通常不需要直接呼叫這個方法。

## <a name="refrows"></a> Irowsetimpl:: Refrows

由呼叫[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)並[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)遞增，或發行至現有的資料列控制代碼的參考計數。

### <a name="syntax"></a>語法

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>參數

請參閱[irowset:: Addrefrows](https://docs.microsoft.com/previous-versions/windows/desktop/ms719619(v=vs.85))中*OLE DB 程式設計人員參考*。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="releaserows"></a> Irowsetimpl:: Releaserows

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

請參閱[irowset:: Releaserows](https://docs.microsoft.com/previous-versions/windows/desktop/ms719771(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="restartposition"></a> Irowsetimpl:: Restartposition

重新定位至其初始位置; 的下一個提取位置也就是它的位置，第一個資料列集時建立。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>參數

請參閱[irowset:: Restartposition](https://docs.microsoft.com/previous-versions/windows/desktop/ms712877(v=vs.85))中*OLE DB 程式設計人員參考*。

### <a name="remarks"></a>備註

資料列集的位置會是未定義，直到`GetNextRow`呼叫。 您可以移動回溯 rowet 藉由呼叫`RestartPosition`然後提取，或向後捲動。

## <a name="setdbstatus"></a> Irowsetimpl:: Setdbstatus

設定指定之欄位的 DBSTATUS 狀態旗標。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>參數

*statusFlags*<br/>
[DBSTATUS](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85))設定資料行的旗標。

*currentRow*<br/>
目前的資料列。

*columnInfo*<br/>
要設定狀態的資料行。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

提供者會覆寫這個函式，以提供特殊處理為 DBSTATUS_S_ISNULL 和 DBSTATUS_S_DEFAULT。

## <a name="bcanfetchback"></a> Irowsetimpl:: M_bcanfetchback

指出提供者是否支援回溯擷取。

### <a name="syntax"></a>語法

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>備註

連結至`DBPROP_CANFETCHBACKWARDS`屬性中的`DBPROPSET_ROWSET`群組。 提供者必須支援`DBPROP_CANFETCHBACKWARDS`for`m_bCanFetchBackwards`要 **，則為 true**。

## <a name="bcanscrollback"></a> Irowsetimpl:: M_bcanscrollback

指出是否提供者可以具有其資料指標捲動回溯。

### <a name="syntax"></a>語法

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>備註

連結至`DBPROP_CANSCROLLBACKWARDS`屬性中的`DBPROPSET_ROWSET`群組。 提供者必須支援`DBPROP_CANSCROLLBACKWARDS`for`m_bCanFetchBackwards`要 **，則為 true**。

## <a name="breset"></a> Irowsetimpl:: M_breset

位元旗標，用來判斷是否要將資料指標位置定義的資料列集上。

### <a name="syntax"></a>語法

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>備註

如果取用者會呼叫[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)具有負`lOffset`或是*cRows*並`m_bReset`為 true，`GetNextRows`移動至資料列集結尾。 如果`m_bReset`為 false，取用者會收到錯誤碼，OLE DB 規格。 `m_bReset`旗標會設成 **，則為 true**先建立資料列集時，當取用者呼叫[irowsetimpl:: Restartposition](../../data/oledb/irowsetimpl-restartposition.md)。 它會設成**假**當您呼叫`GetNextRows`。

## <a name="irowset"></a> Irowsetimpl:: M_irowset

表示資料指標的資料列集的索引。

### <a name="syntax"></a>語法

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="rgrowhandles"></a> Irowsetimpl:: M_rgrowhandles

目前回應中的提供者所包含的資料列控制代碼的對應`GetNextRows`。

### <a name="syntax"></a>語法

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>備註

會移除資料列控制代碼呼叫`ReleaseRows`。 請參閱[IRowsetImpl 概觀](../../data/oledb/irowsetimpl-class.md)定義*MapClass*。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow 類別](../../data/oledb/csimplerow-class.md)