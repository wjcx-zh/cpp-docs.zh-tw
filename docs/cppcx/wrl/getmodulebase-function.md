---
title: GetModuleBase 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 0d130fffa9fad9ae327d03eaa01d84742094cc67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213963"
---
# <a name="getmodulebase-function"></a>GetModuleBase 函式

抓取[ModuleBase](modulebase-class.md)指標，允許遞增和遞減[RuntimeClass](runtimeclass-class.md)物件的參考計數。

## <a name="syntax"></a>語法

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>傳回值

`ModuleBase` 物件的指標。

## <a name="remarks"></a>備註

此函式會在內部用來遞增和遞減物件參考計數。

您可以使用此函數來控制參考計數，方法是呼叫[ModuleBase：： IncrementObjectCount](modulebase-class.md#incrementobjectcount)和[ModuleBase：:D ecrementobjectcount](modulebase-class.md#decrementobjectcount)。

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
