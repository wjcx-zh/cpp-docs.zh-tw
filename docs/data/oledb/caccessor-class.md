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
ms.openlocfilehash: 032274d7dc85aa823cd28cf61e4606903f13ad9e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509556"
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

當記錄靜態系結至資料來源時，就會使用它。 記錄包含緩衝區。 此類別支援資料列集上的多個存取子。

當您知道資料庫的結構和類型時，請使用此存取子類型。

如果存取子包含指向記憶體 (的欄位 `BSTR` ，例如必須釋放的或介面) ，則在讀取下一個記錄之前，請先呼叫成員函式 [CAccessorRowset：： FreeRecordMemory](./caccessorrowset-class.md#freerecordmemory) 。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
