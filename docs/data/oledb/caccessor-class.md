---
title: CAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: 2b30cef2baf8c13c5001e44901b984aa1293494d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212299"
---
# <a name="caccessor-class"></a>CAccessor 類別

表示其中一個存取子類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>參數

*T*<br/>
使用者記錄類別。

## <a name="remarks"></a>備註

當記錄以靜態方式系結至資料來源時，會使用它。 記錄包含緩衝區。 這個類別支援資料列集上的多個存取子。

當您知道資料庫的結構和類型時，請使用此存取子類型。

如果您的存取子包含指向必須釋放之記憶體（例如 `BSTR` 或介面）的欄位，則在讀取下一筆記錄之前，請先呼叫成員函式[CAccessorRowset：： FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) 。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
