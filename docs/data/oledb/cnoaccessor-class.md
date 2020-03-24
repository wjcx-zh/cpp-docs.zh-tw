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
ms.openlocfilehash: c82d756690c6c2a719cb03f458c471aa44e3d5b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211727"
---
# <a name="cnoaccessor-class"></a>CNoAccessor 類別

可用來做為範本類別的樣板引數（`TAccessor`），例如需要存取子類別引數的 `CCommand` 和 `CTable`。

## <a name="syntax"></a>語法

```cpp
class CNoAccessor
```

## <a name="remarks"></a>備註

當您不想要讓類別支援參數或輸出資料行時，請使用 `CNoAccessor` 做為樣板引數。

`CNoAccessor` 會執行下列 stub 方法，其中每一個都對應至其他存取子類別方法：

- `BindColumns`-將資料行系結至存取子。

- `BindParameters`-將建立的參數系結至資料行。

- `Bind`-建立系結。

- `Close`-關閉存取子。

- `ReleaseAccessors`-釋放類別所建立的存取子。

- `FreeRecordMemory`-釋放目前記錄中需要釋放的任何資料行。

- `GetColumnInfo`-從已開啟的資料列集取得資料行資訊。

- `GetNumAccessors`-抓取類別所建立的存取子數目。

- `IsAutoAccessor`-如果在移動作業期間自動取得存取子的資料，則傳回 true。

- `GetHAccessor`-抓取所指定存取子的存取子控制碼。

- `GetBuffer`-抓取書簽緩衝區的指標。

- `NoBindOnNullRowset`-防止空資料列集上的資料系結。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
