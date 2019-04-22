---
title: GetModuleBase 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 4d8c8467b7aeb9c21bf5f4ee19c60e6e60880688
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784345"
---
# <a name="getmodulebase-function"></a>GetModuleBase 函式

擷取[ModuleBase](modulebase-class.md)指標，這是用來遞增和遞減參考計數[RuntimeClass](runtimeclass-class.md)物件。

## <a name="syntax"></a>語法

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>傳回值

`ModuleBase` 物件的指標。

## <a name="remarks"></a>備註

此函式在內部用來遞增和遞減物件的參考計數。

您可以使用此函式，來控制參考計數，藉由呼叫[modulebase:: Incrementobjectcount](modulebase-class.md#incrementobjectcount)並[modulebase:: Decrementobjectcount](modulebase-class.md#decrementobjectcount)。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)