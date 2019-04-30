---
title: __writemsr
ms.date: 11/04/2016
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: ac57bac1d132c581ee12048b89d13ed1d1fdb7da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389706"
---
# <a name="writemsr"></a>__writemsr

**Microsoft 專屬**

會產生寫入模型特定註冊 (`wrmsr`) 指令。

## <a name="syntax"></a>語法

```
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

#### <a name="parameters"></a>參數

*註冊*<br/>
[in]模型特定暫存器。

*值*<br/>
[in]要寫入的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writemsr`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此函式可能只使用核心模式中，此常式僅可作為內建。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)