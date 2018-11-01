---
title: CNoRowset 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 513e393bbc782d87b37dab108428f2970fbb92e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644449"
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