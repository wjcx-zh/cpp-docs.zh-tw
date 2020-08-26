---
title: CArrayRowset 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
ms.openlocfilehash: c5f12afa09bc1c62d3287bab93159e217721906f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843244"
---
# <a name="carrayrowset-class"></a>CArrayRowset 類別

使用陣列語法存取資料列集的元素。

## <a name="syntax"></a>語法

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>,
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>參數

*TAccessor*<br/>
您希望資料列集使用的存取子類別型別。

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|--|--|
| [CArrayRowset](#carrayrowset) | 建構函式。 |
| [快照式](#snapshot) | 將整個資料列集讀入記憶體中。 |

### <a name="operators"></a>運算子

| 名稱 | 描述 |
|--|--|
| [運算子&#91;&#93;](#operator) | 存取資料列集的元素。 |

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|--|--|
| [CArrayRowset::m_nRowsRead](#nrowsread) | 已讀取的資料列數目。 |

## <a name="carrayrowsetcarrayrowset"></a><a name="carrayrowset"></a> CArrayRowset：： CArrayRowset

建立新的 `CArrayRowset` 物件。

### <a name="syntax"></a>語法

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>參數

*N 上限*<br/>
[in] 資料列集的最大資料列數。

## <a name="carrayrowsetsnapshot"></a><a name="snapshot"></a> CArrayRowset：： Snapshot

將整個資料列集讀取至記憶體，建立其影像或快照。

### <a name="syntax"></a>語法

```cpp
HRESULT Snapshot() throw();
```

## <a name="carrayrowsetoperator"></a><a name="operator"></a> CArrayRowset：： operator

提供在資料列集中存取資料列，類似陣列的語法。

### <a name="syntax"></a>語法

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>參數

*TAccessor*<br/>
指定儲存在資料列集中存取子類型的範本參數。

*nRow*<br/>
[in] 要存取的資料列號碼 (陣列項目)。

### <a name="return-value"></a>傳回值

所要求資料列的內容。

### <a name="remarks"></a>備註

如果 *nRow* 超過資料列集中的資料列數目，則會擲回例外狀況。

## <a name="carrayrowsetm_nrowsread"></a><a name="nrowsread"></a> CArrayRowset：： m_nRowsRead

包含已讀取之資料列集中的資料列數目。

### <a name="syntax"></a>語法

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset 類別](../../data/oledb/crowset-class.md)
