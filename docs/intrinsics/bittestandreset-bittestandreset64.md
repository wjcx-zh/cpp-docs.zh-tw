---
title: _bittestandreset, _bittestandreset64
ms.date: 11/04/2016
f1_keywords:
- _bittestandreset64_cpp
- _bittestandreset
- _bittestandreset_cpp
- _bittestandreset64
helpviewer_keywords:
- btr instruction
- _bittestandreset intrinsic
- _bittestandreset64 intrinsic
ms.assetid: 8dad63bb-a051-4cd7-a793-3357537dfeaf
ms.openlocfilehash: d8c4675e7efe9e1de8ce6f133d1c361481f1b544
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557660"
---
# <a name="bittestandreset-bittestandreset64"></a>_bittestandreset, _bittestandreset64

**Microsoft 專屬**

產生的指令會檢查位址 `b` 的位元 `a`、傳回其目前值，並將位元重設為 0。

## <a name="syntax"></a>語法

```
unsigned char _bittestandreset(
   long *a,
   long b
);
unsigned char _bittestandreset64(
   __int64 *a,
   __int64 b
);
```

#### <a name="parameters"></a>參數

*a*<br/>
[in、 out]要檢查的記憶體指標。

*b*<br/>
[in]要測試的位元位置。

## <a name="return-value"></a>傳回值

位於指定位置的位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_bittestandreset`|x86、 x64、 ARM|
|`_bittestandreset64`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
// bittestandreset.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <limits.h>
#include <intrin.h>

#pragma intrinsic(_bittestandreset)

// Check the sign bit and reset to 0 (taking the absolute value)
// Returns 0 if the number is positive or zero
// Returns 1 if the number is negative
unsigned char absolute_value(long* p)
{
   const int SIGN_BIT = 31;
   return _bittestandreset(p, SIGN_BIT);
}

int main()
{
    long i = -112;
    unsigned char result;

    // Check the sign bit and reset to 0 (taking the absolute value)

    result = absolute_value(&i);
    if (result == 1)
        printf_s("The number was negative.\n");
}
```

```Output
The number was negative.
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)