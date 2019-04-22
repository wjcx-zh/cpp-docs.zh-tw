---
title: __umulh
ms.date: 11/04/2016
f1_keywords:
- __umulh
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
ms.openlocfilehash: 3a42de276b483f98e2eaf9d0c8505d7f1d5b5bca
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026561"
---
# <a name="umulh"></a>__umulh

**Microsoft 專屬**

傳回兩個 64 位元不帶正負號整數之乘積的 64 高位元。

## <a name="syntax"></a>語法

```
unsigned __int64 __umulh(
   unsigned __int64 a,
   unsigned __int64 b
);
```

#### <a name="parameters"></a>參數

*a*<br/>
[in]要相乘的第一個數字。

*b*<br/>
[in]要相乘的第二個數字。

## <a name="return-value"></a>傳回值

相乘的 128 位元結果的 64 高位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__umulh`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

這些常式僅以內建函式的形式供您使用。

## <a name="example"></a>範例

```
// umulh.cpp
// processor: X64
#include <cstdio>
#include <intrin.h>

int main()
{
    unsigned __int64 i = 0x10;
    unsigned __int64 j = 0xFEDCBA9876543210;
    unsigned __int64 k = i * j; // k has the low 64 bits
                                // of the product.
    unsigned __int64 result;
    result = __umulh(i, j); // result has the high 64 bits
                            // of the product.
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);
    return 0;
}
```

```Output
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)