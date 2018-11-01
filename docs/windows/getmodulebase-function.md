---
title: GetModuleBase 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 40289903eba2ce7ac35d4d0b208c3b609efb09f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650810"
---
# <a name="getmodulebase-function"></a>GetModuleBase 函式
擷取[ModuleBase](../windows/modulebase-class.md)指標，這是用來遞增和遞減參考計數[RuntimeClass](../windows/runtimeclass-class.md)物件。

## <a name="syntax"></a>語法

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>傳回值

`ModuleBase` 物件的指標。

## <a name="remarks"></a>備註

此函式在內部用來遞增和遞減物件的參考計數。

您可以使用此函式，來控制參考計數，藉由呼叫[modulebase:: Incrementobjectcount](../windows/modulebase-incrementobjectcount-method.md)並[modulebase:: Decrementobjectcount](../windows/modulebase-decrementobjectcount-method.md)。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)