---
title: __mulh
ms.date: 09/02/2019
f1_keywords:
- __mulh
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
ms.openlocfilehash: c3a421cdda1c62620d4c933436fd0b5bab589c0e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221689"
---
# <a name="__mulh"></a>__mulh

**Microsoft 專屬**

傳回 2 64 位帶正負號整數之乘積的高64位。

## <a name="syntax"></a>語法

```C
__int64 __mulh(
   __int64 a,
   __int64 b
);
```

### <a name="parameters"></a>參數

*為*\
[in] 要相乘的第一個數字。

*位元組*\
[in] 要相乘的第二個數字。

## <a name="return-value"></a>傳回值

相乘的 128 位元結果的 64 高位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__mulh`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// mulh.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__mulh)

int main()
{
    __int64 a = 0x0fffffffffffffffI64;
    __int64 b = 0xf0000000I64;

    __int64 result = __mulh(a, b); // the high 64 bits
    __int64 result2 = a * b; // the low 64 bits

    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",
             a, b, result, result2);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
