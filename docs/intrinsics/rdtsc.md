---
title: __rdtsc
ms.date: 09/02/2019
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 837b68ca6ac63587cd43a7e8828777221c677e3c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217144"
---
# <a name="__rdtsc"></a>__rdtsc

**Microsoft 專屬**

`rdtsc`產生指示, 此指令會傳回處理器時間戳記。 處理器時間戳記會記錄自上次重設後的頻率週期數目。

## <a name="syntax"></a>語法

```C
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>傳回值

代表滴答計數的64位不帶正負號的整數。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__rdtsc`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅適用于內建函式。

在較早的 x64 版本中, 在較新的硬體世代中, TSC 值的解讀方式不同。 如需詳細資訊, 請參閱硬體手冊。

## <a name="example"></a>範例

```cpp
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

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
