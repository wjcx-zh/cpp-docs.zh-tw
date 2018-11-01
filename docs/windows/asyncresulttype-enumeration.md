---
title: AsyncResultType 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: df91b80fe21ecddabc7062b040387b8c2b2c1bb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551368"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 列舉

指定所傳回的結果的型別`GetResults()`方法。

## <a name="syntax"></a>語法

```cpp
enum AsyncResultType;
```

## <a name="members"></a>成員

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`MultipleResults`|多個結果，以漸進方式之間會顯示一組`Start`狀態，以及之前`Close()`呼叫。|
|`SingleResult`|單一的結果之後, 會呈現`Complete`就會發生事件。|

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)