---
title: __writemsr
ms.date: 09/02/2019
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: 7819477edb8d4e6b18a1213a73ba67065ea7ff57
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219129"
---
# <a name="__writemsr"></a>__writemsr

**Microsoft 專屬**

產生寫入模型特定的 Register (`wrmsr`) 指令。

## <a name="syntax"></a>語法

```C
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

### <a name="parameters"></a>參數

*參加*\
在模型特定的暫存器。

*Value*\
在要寫入的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writemsr`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此函式只能用於核心模式, 而且此常式僅可作為內建。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
