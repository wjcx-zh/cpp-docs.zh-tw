---
title: CNoRowset 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs:
- C++
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f14ad79e1cbd2207b4eb1582cb80e0107d68ec39
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064234"
---
# <a name="cnorowset-class"></a>CNoRowset 類別

可用來當做樣板引數 (`TRowset`) 的[CCommand](../../data/oledb/ccommand-class.md)或是[CTable](../../data/oledb/ctable-class.md)。

## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>參數

*TAccessor*<br/>
存取子類別。 預設為 `CAccessorBase`。

## <a name="remarks"></a>備註

使用`CNoRowset`做為範本引數，如果命令未傳回資料列集。

`CNoRowset` 會實作下列的虛設常式方法，其中每一個對應到其他存取子類別的方法：

- `BindFinished` -代表當繫結完成時 (傳回`S_OK`)。

- `Close` -釋放資料列和目前的 IRowset 介面。

- `GetIID` -擷取連接點的介面 ID。

- `GetInterface` -擷取介面。

- `GetInterfacePtr` -擷取封裝的介面指標。

- `SetAccessor` -設定存取子的指標。

- `SetupOptionalRowsetInterfaces` -設定的資料列集的選擇性介面。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)