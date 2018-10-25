---
title: CColumnAccessor 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e55d4c15ca5d5a3733c44cf89b788b85c905513
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074666"
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