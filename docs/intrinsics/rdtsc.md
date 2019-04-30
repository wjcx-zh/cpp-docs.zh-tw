---
title: __rdtsc
ms.date: 11/04/2016
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 6f30be3340ae1be237bb2f8a008a8cb60c7351f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396570"
---
# <a name="rdtsc"></a>__rdtsc

**Microsoft 專屬**

會產生`rdtsc`指令，這會傳回處理器時間戳記。 處理器時間戳記記錄自上次重設的時脈週期數。

## <a name="syntax"></a>語法

```
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>傳回值

64 位元不帶正負號的整數，代表滴答計數。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__rdtsc`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式是只提供內建函式。

在這一代硬體的 TSC 值的解譯不同於在舊版的 x64。 請參閱硬體手冊，如需詳細資訊。

## <a name="example"></a>範例

```
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)