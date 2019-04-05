---
title: CNoAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: 0cf1b47cc03d1839ae5c547393c3c193dab439d4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027658"
---
# <a name="cnoaccessor-class"></a>CNoAccessor 類別

可用來當做樣板引數 (`TAccessor`) 的範本類別，例如`CCommand`和`CTable`，需要存取子類別引數。

## <a name="syntax"></a>語法

```cpp
class CNoAccessor
```

## <a name="remarks"></a>備註

使用`CNoAccessor`做為範本引數，當您不想要支援的參數或輸出資料行的類別。

`CNoAccessor` 會實作下列的虛設常式方法，其中每一個對應到其他存取子類別的方法：

- `BindColumns` -繫結至存取子的資料行。

- `BindParameters` -繫結至資料行的建立的參數。

- `Bind` -建立繫結。

- `Close` -關閉存取子。

- `ReleaseAccessors` -釋放存取子類別建立的。

- `FreeRecordMemory` -會釋出任何需要先釋放目前記錄中的資料行。

- `GetColumnInfo` -從開啟的資料列集取得資料行資訊。

- `GetNumAccessors` -擷取類別所建立的存取子的數目。

- `IsAutoAccessor` -如果會自動擷取資料的存取子在移動操作傳回 true。

- `GetHAccessor` -擷取指定的存取子的存取子控制代碼。

- `GetBuffer` -擷取書籤緩衝區的指標。

- `NoBindOnNullRowset` -可防止在空白資料列集上的資料繫結。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)