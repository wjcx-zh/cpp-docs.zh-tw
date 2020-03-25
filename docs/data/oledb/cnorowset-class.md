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
ms.openlocfilehash: 19a1e01fd29c74cf1c44081c24bf384704cf2acd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211467"
---
# <a name="cnorowset-class"></a>CNoRowset 類別

可用來做為[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md)的範本引數（`TRowset`）。

## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>參數

*TAccessor*<br/>
存取子類別。 預設值為 `CAccessorBase`。

## <a name="remarks"></a>備註

如果命令不會傳回資料列集，請使用 `CNoRowset` 做為樣板引數。

`CNoRowset` 會執行下列 stub 方法，其中每一個都對應至其他存取子類別方法：

- `BindFinished`-指出系結完成的時間（傳回 `S_OK`）。

- `Close`-釋放資料列和目前的 IRowset 介面。

- `GetIID`-抓取連接點的介面識別碼。

- `GetInterface`-抓取介面。

- `GetInterfacePtr`-捕獲封裝的介面指標。

- `SetAccessor`-設定存取子的指標。

- `SetupOptionalRowsetInterfaces`-設定資料列集的選擇性介面。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
