---
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: bc6e33da5ac7b25727f6e24c3af6e6a926b29847
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230502"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Microsoft 特定的**

產生將純量單精確度浮點數轉換為64位整數（）指令的 x64 擴充版本 `cvtss2si` 。

## <a name="syntax"></a>語法

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>參數

*value*\
在**`__m128`** 包含浮點值的結構。

## <a name="return-value"></a>傳回值

64位整數，這是將第一個浮點值轉換成整數的結果。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_cvtss_si64x`|x64|

**標頭檔** \<intrin.h>

## <a name="remarks"></a>備註

結構值的第一個元素會轉換成整數，並傳回。 MXCSR 中的進位控制位是用來判斷舍入行為。 預設進位模式會四捨五入為最接近的值，如果小數部分為0.5，則四捨五入為偶數。 因為 **`__m128`** 結構代表 xmm 暫存器，所以內建函式會從 xmm 暫存器取得值，並將它寫入系統記憶體。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[__m128d](../cpp/m128d.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
