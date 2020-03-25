---
title: CColumnAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2a3b1dac51a8300a915a7177c36f15512b583fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212106"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor 類別

產生插入的取用者程式碼。

## <a name="syntax"></a>語法

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>備註

在插入的程式碼中，每個資料行都會系結為個別的存取子。 請注意，插入的程式碼中會使用這個類別（例如，當您在進行偵錯工具時可能會遇到這種情況），但您通常不需要直接使用它或其方法。

`CColumnAccessor` 會實作為下列 stub 方法，其中每一個都對應至其他存取子類別方法的功能：

- `CColumnAccessor` 的函式;具現化並初始化 `CColumnAccessor` 物件。

- `CreateAccessor` 會為數據行系結結構配置記憶體，並初始化資料行資料成員。

- `BindColumns` 將資料行系結至存取子。

- `SetParameterBuffer` 配置參數的緩衝區。

- `AddParameter` 會將參數專案新增至參數專案結構。

- `HasOutputColumns` 判斷存取子是否有輸出資料行

- `HasParameters` 判斷存取子是否有參數。

- `BindParameters` 會將建立的參數系結至資料行。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
