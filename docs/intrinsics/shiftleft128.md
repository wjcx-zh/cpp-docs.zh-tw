---
title: __shiftleft128
ms.date: 09/02/2019
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5da9ac81cedbdd24e10eb438892f88510c32ca24
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217998"
---
# <a name="__shiftleft128"></a>__shiftleft128

**Microsoft 專屬**

移位 128 位元數量，表示兩個距離左邊達 `LowPart` 指定之位元數的 64 位元數量 `HighPart` 和 `Shift`，並傳回結果的較高 64 個位元。

## <a name="syntax"></a>語法

```C
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>參數

*LowPart*\
在要轉移之128位數量的低64位。

*HighPart*\
在要轉移之128位數量的高64位。

*結*\
在要移位的位數。

## <a name="return-value"></a>傳回值

結果的較高 64 個位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__shiftleft128`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

*移位*值一律為模數 64, 因此, 例如, `__shiftleft128(1, 0, 64)`如果您呼叫, 函`0`式會將剩餘的低部分`0`位向左移位, 而不`1`會傳回的高部分, 否則可能會預期。

## <a name="example"></a>範例

```C
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__shiftright128](../intrinsics/shiftright128.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
