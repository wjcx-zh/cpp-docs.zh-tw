---
title: CBulkRowset 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: e66a183c7bbafa16b3aefea8da1472255b507468
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212119"
---
# <a name="cbulkrowset-class"></a>CBulkRowset 類別

藉由使用單一呼叫來抓取多個資料列控制碼，以提取和運算元據列來大量處理資料。

## <a name="syntax"></a>語法

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>參數

*TAccessor*<br/>
存取子類別。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddRefRows](#addrefrows)|遞增參考計數。|
|[CBulkRowset](#cbulkrowset)|建構函式。|
|[MoveFirst](#movefirst)|會抓取第一個資料列，視需要執行新的大量提取。|
|[MoveLast](#movelast)|移至最後一個資料列。|
|[MoveNext](#movenext)|抓取下一個資料列。|
|[MovePrev](#moveprev)|移至上一個資料列。|
|[MoveToBookmark](#movetobookmark)|提取以書簽標記的資料列，或從該書簽指定之位移的資料列。|
|[MoveToRatio](#movetoratio)|從資料列集中的小數位置開始提取資料列。|
|[ReleaseRows](#releaserows)|將目前的資料列（`m_nCurrentRow`）設定為零，並釋放所有資料列。|
|[SetRows](#setrows)|設定要由一個呼叫抓取的資料列控制碼數目。|

## <a name="example"></a>範例

下列範例示範如何使用 `CBulkRowset` 類別。

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="cbulkrowsetaddrefrows"></a><a name="addrefrows"></a>CBulkRowset：： AddRefRows

呼叫[IRowset：： AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) ，以遞增目前從 bulk 資料列集取得之所有資料列的參考計數。

### <a name="syntax"></a>語法

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cbulkrowsetcbulkrowset"></a><a name="cbulkrowset"></a>CBulkRowset：： CBulkRowset

建立新的 `CBulkRowset` 物件並且將預設資料列計數設定為 10。

### <a name="syntax"></a>語法

```cpp
CBulkRowset();
```

## <a name="cbulkrowsetmovefirst"></a><a name="movefirst"></a>CBulkRowset：： MoveFirst

抓取第一個資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cbulkrowsetmovelast"></a><a name="movelast"></a>CBulkRowset：： MoveLast

移至最後一個資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cbulkrowsetmovenext"></a><a name="movenext"></a>CBulkRowset：： MoveNext

抓取下一個資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。 當已到達資料列集的結尾時，會傳回 DB_S_ENDOFROWSET。

## <a name="cbulkrowsetmoveprev"></a><a name="moveprev"></a>CBulkRowset：： MovePrev

移至上一個資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cbulkrowsetmovetobookmark"></a><a name="movetobookmark"></a>CBulkRowset：： MoveToBookmark

提取書簽所標記的資料列，或從該書簽指定之位移（*lSkip*）的資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>參數

*書簽*<br/>
[in] 標記您要從中擷取資料之位置的書籤。

*lSkip*<br/>
[in] 從書籤到目標資料列的資料列計數。 如果*lSkip*為零，則第一個提取的資料列會是已加上書簽的資料列。 如果*lSkip*是1，則第一個提取的資料列就是已加上書簽的資料列之後的資料列。 如果*lSkip*為-1，則第一個提取的資料列是已加上書簽的資料列之前的資料列。

### <a name="return-value"></a>傳回值

請參閱 OLE DB 程式設計*人員參考*中的[IRowset：：執行](/previous-versions/windows/desktop/ms716988(v=vs.85))程式。

## <a name="cbulkrowsetmovetoratio"></a><a name="movetoratio"></a>CBulkRowset：： MoveToRatio

從資料列集中的小數位置開始提取資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>參數

*nNumerator*<br/>
在用來判斷從中提取資料之小數位置的分子。

*nDenominator*<br/>
在用來決定從中提取資料之小數位置的分母。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

`MoveToRatio` 會根據下列公式，大致地提取資料列：

`(nNumerator *  RowsetSize ) / nDenominator`

其中 `RowsetSize` 是資料列集的大小（以資料列數來測量）。 此公式的精確度取決於特定的提供者。 如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetScroll：： GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) 。

## <a name="cbulkrowsetreleaserows"></a><a name="releaserows"></a>CBulkRowset：： ReleaseRows

呼叫[IRowset：： ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) ，以遞減目前從 bulk 資料列集取得之所有資料列的參考計數。

### <a name="syntax"></a>語法

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cbulkrowsetsetrows"></a><a name="setrows"></a>CBulkRowset：： SetRows

設定每個呼叫所擷取的資料列控制代碼數。

### <a name="syntax"></a>語法

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>參數

*nRows*<br/>
[in] 新的資料列集大小 (資料列數)。

### <a name="remarks"></a>備註

如果您呼叫這個函式，它必須在開啟資料列集之前。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
