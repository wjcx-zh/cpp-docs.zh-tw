---
title: CSimpleRow 類別
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: 00d8164425ada573020971f66312b2282cc72c45
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441143"
---
# <a name="csimplerow-class"></a>CSimpleRow 類別

針對[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)類別中使用的資料列控制碼，提供預設的執行。

## <a name="syntax"></a>語法

```cpp
class CSimpleRow
```

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddRefRow](#addrefrow)|將參考次數 (Reference Count) 加入至現有的資料列控制代碼。|
|[比較](#compare)|比較兩個數據列，以查看它們是否參考相同的資料列實例。|
|[CSimpleRow](#csimplerow)|建構函式。|
|[ReleaseRow](#releaserow)|釋放資料列。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_dwRef](#dwref)|現有資料列控制碼的參考計數。|
|[m_iRowset](#irowset)|代表資料指標之資料列集的索引。|

## <a name="remarks"></a>備註

資料列控制碼在邏輯上是結果資料列的唯一標記。 `IRowsetImpl` 會針對[IRowsetImpl：： GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)中要求的每個資料列建立新的 `CSimpleRow`。 `CSimpleRow` 也可以取代為您自己的資料列控制碼的執行，因為它是 `IRowsetImpl`的預設樣板引數。 取代此類別的唯一需求是讓取代類別提供接受**LONG**類型之單一參數的函式。

## <a name="addrefrow"></a>CSimpleRow：： AddRefRow

以執行緒安全的方式，將參考計數加入至現有的資料列控制碼。

### <a name="syntax"></a>語法

```cpp
DWORD AddRefRow();
```

## <a name="compare"></a>CSimpleRow：： Compare

比較兩個數據列，以查看它們是否參考相同的資料列實例。

### <a name="syntax"></a>語法

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>參數

*pRow*<br/>
`CSimpleRow` 物件的指標。

### <a name="return-value"></a>傳回值

HRESULT 值通常 S_OK，表示兩個數據列都是相同的資料列實例，或是 S_FALSE，表示兩個數據列不同。 如需其他可能的傳回值，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetIdentity：： IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) 。

## <a name="csimplerow"></a>CSimpleRow：： CSimpleRow

建構函式。

### <a name="syntax"></a>語法

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>參數

*iRowsetCur*<br/>
在目前資料列集的索引。

### <a name="remarks"></a>備註

將[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)設定為*iRowsetCur*。

## <a name="releaserow"></a>CSimpleRow：： ReleaseRow

以執行緒安全的方式釋放資料列。

### <a name="syntax"></a>語法

```cpp
DWORD ReleaseRow();
```

## <a name="dwref"></a>CSimpleRow：： m_dwRef

現有資料列控制碼的參考計數。

### <a name="syntax"></a>語法

```cpp
DWORD m_dwRef;
```

## <a name="irowset"></a>CSimpleRow：： m_iRowset

代表資料指標之資料列集的索引。

### <a name="syntax"></a>語法

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)