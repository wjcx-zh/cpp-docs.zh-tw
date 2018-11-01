---
title: _mm_cvtss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 259e3933c831ba685fa9d00d0f6471975a31f2cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606839"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x

**Microsoft 專屬**

會產生擴充的 x64 版本的轉換純量單一精確度浮點數為 64 位元整數 (`cvtss2si`) 指令。

## <a name="syntax"></a>語法

```
__int64 _mm_cvtss_si64x( 
   __m128 value 
);
```

#### <a name="parameters"></a>參數

*值*<br/>
[in]`__m128`包含浮動點值的結構。

## <a name="return-value"></a>傳回值

64 位元整數，第一個浮點值轉換成整數的結果。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結構值的第一個項目會轉換成整數，並傳回。 在 MXCSR 捨入的控制位元用來判斷捨入的行為。 捨入模式的預設值是四捨五入到最接近的小數部分是否為 0.5，捨入為偶數。 因為`__m128`結構表示 XMM 暫存器，此內建函式會採用 XMM 暫存器中的值，並將它寫入至系統記憶體。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__m128d](../cpp/m128d.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)