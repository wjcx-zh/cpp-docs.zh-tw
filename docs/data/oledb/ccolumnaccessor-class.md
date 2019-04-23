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
ms.openlocfilehash: 2d65fb047e758f449ed76c954bb4ac0c3623f6dd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032124"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor 類別

產生插入的取用者程式碼。

## <a name="syntax"></a>語法

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>備註

插入的程式碼，在每個資料行繫結為不同的存取子。 您應該要知道此類別會在插入程式碼 （例如，您可能會遇到它進行偵錯時），但您通常一律不要直接使用它或它的方法。

`CColumnAccessor` 會實作下列的虛設常式方法，其中每一個對應到其他存取子類別方法的功能：

- `CColumnAccessor` 建構函式具現化並初始化`CColumnAccessor`物件。

- `CreateAccessor` 資料行繫結結構配置記憶體，並初始化資料行的資料成員。

- `BindColumns` 將資料行的繫結至存取子。

- `SetParameterBuffer` 配置參數緩衝區。

- `AddParameter` 將參數項目加入至參數項目結構。

- `HasOutputColumns` 判斷存取子是否有輸出資料行

- `HasParameters` 判斷存取子是否有參數。

- `BindParameters` 將建立的參數繫結至資料行。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)