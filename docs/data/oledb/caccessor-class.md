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
ms.openlocfilehash: cfc91f971fc975bcdd2c8ae37d798ff2f5a1cab0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283946"
---
# <a name="caccessor-class"></a>CAccessor 類別

代表其中一個存取子類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>參數

*T*<br/>
使用者記錄類別。

## <a name="remarks"></a>備註

它是用來記錄以靜態方式繫結至資料來源。 記錄包含緩衝區。 此類別支援多個存取子資料列集。

當您知道結構和資料庫類型時，請使用這個存取子類型。

如果您的存取子包含指向的記憶體的欄位 (例如`BSTR`或介面)，必須釋出，呼叫成員函式[caccessorrowset:: Freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md)下一步 再讀取記錄。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)