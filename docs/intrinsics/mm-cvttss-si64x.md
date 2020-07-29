---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 6d920a5c59cacb23c7fb155c7ac8e813a9b0e8d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217983"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Microsoft 特定的**

以截斷單精確度浮點數到64位整數（）指令的形式，發出轉換的 x64 擴充版本 `cvttss2si` 。

## <a name="syntax"></a>語法

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>參數

*value*\
在**`__m128`** 包含單精確度浮點值的結構。

## <a name="return-value"></a>傳回值

第一個浮點值轉換成64位整數的結果。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**標頭檔** \<intrin.h>

## <a name="remarks"></a>備註

內建函式與不同之處在于 `_mm_cvtss_si64x` ，不精確的轉換會向零截斷。 因為 **`__m128`** 結構代表 xmm 暫存器，所以產生的指令會將資料從 XMM 登錄移至系統記憶體。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[__m128](../cpp/m128.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
