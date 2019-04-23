---
title: _mm_cvtsi64x_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 3ba9dc56cbb027e8cf9f31d293b3f96908aff5e4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039776"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss

**Microsoft 專屬**

會產生擴充的 x64 版本的純量單精確度浮點值的轉換的 64 位元整數 (`cvtsi2ss`) 指令。

## <a name="syntax"></a>語法

```
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

#### <a name="parameters"></a>參數

*a*<br/>
[in]`__m128`結構，其中包含四個單精確度浮點值。

*b*<br/>
[in]要轉換成浮點值的 64 位元整數。

## <a name="return-value"></a>傳回值

`__m128`結構，其第一個的浮點值是轉換的結果。 其他三個值會複製與`a`。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`__m128`結構代表 XMM 暫存器，因此此內建的允許值`b`從系統記憶體，是要移至 XMM 暫存器。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__m128](../cpp/m128.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)