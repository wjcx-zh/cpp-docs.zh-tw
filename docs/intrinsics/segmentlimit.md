---
title: __segmentlimit |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __segmentlimit
dev_langs:
- C++
helpviewer_keywords:
- __segmentlimit intrinsic
- lsl instruction
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d31210194f9b9f1c9808176cd7e5495df8da1ebb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395306"
---
# <a name="segmentlimit"></a>__segmentlimit

**Microsoft 專屬**

會產生`lsl`（負載區段上限） 的指示。

## <a name="syntax"></a>語法

```
unsigned long __segmentlimit( 
   unsigned long a 
);
```

#### <a name="parameters"></a>參數

*a*<br/>
[in]常數，指定的區段選取器。

## <a name="return-value"></a>傳回值

區段的限制所指定的區段選取器`a`，前提是選取器是在目前的權限層級的有效且可見。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__segmentlimit`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

如果無法擷取區段上限，此指示將會失敗。 在失敗時，此指示清除 ZF 旗標，並傳回值會是未定義。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
#include <stdio.h>

#ifdef _M_IX86
typedef unsigned int READETYPE;
#else
typedef unsigned __int64 READETYPE;
#endif

#define EFLAGS_ZF      0x00000040
#define KGDT_R3_DATA    0x0020
#define RPL_MASK        0x3

extern "C"
{
unsigned long __segmentlimit (unsigned long);
READETYPE __readeflags();
}

#pragma intrinsic(__readeflags)
#pragma intrinsic(__segmentlimit)

int main(void)
{
   const unsigned long initsl = 0xbaadbabe;
   READETYPE eflags = 0;
   unsigned long sl = initsl;

   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);

   eflags = __readeflags();

   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");

   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");

   // You can verify the value of sl to make sure that the instruction wrote to it
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");

   return 0;
}
```

```Output
Before: segment limit =0xbaadbabe eflags =0x0
After: segment limit =0xffffffff eflags =0x256 eflags.zf = set
Success!
sl was changed
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)