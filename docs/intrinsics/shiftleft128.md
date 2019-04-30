---
title: __shiftleft128
ms.date: 11/04/2016
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5fcb797694c7a45dc4f2113f3d2ed4a2f578c894
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390408"
---
# <a name="shiftleft128"></a>__shiftleft128

**Microsoft 專屬**

移位 128 位元數量，表示兩個距離左邊達 `LowPart` 指定之位元數的 64 位元數量 `HighPart` 和 `Shift`，並傳回結果的較高 64 個位元。

## <a name="syntax"></a>語法

```
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>參數

*LowPart*<br/>
[in]要移位的 128 位元數量低 64 個位元。

*HighPart*<br/>
[in]要移位的 128 位元數量高 64 個位元。

*Shift*<br/>
[in]要移位的位元數。

## <a name="return-value"></a>傳回值

結果的較高 64 個位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__shiftleft128`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`Shift` 值一律為模數 64，使得 (舉例而言) 如果您呼叫 `__shiftleft128(1, 0, 64)`，函式將向左移低部分 `0` 個位元，並傳回 `0` 而非 `1` 的高部分，因為將會預期其他值。

## <a name="example"></a>範例

```
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

[__shiftright128](../intrinsics/shiftright128.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)