---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 0e9bacc56f212e804467d1c6e0159a1749235976
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217464"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Microsoft 專屬**

產生將64位整數轉換成純量單精確度浮點值 (`cvtsi2ss`) 指令的 x64 擴充版本。

## <a name="syntax"></a>語法

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>參數

*為*\
在包含`__m128`四個單精確度浮點值的結構。

*位元組*\
在要轉換成浮點值的64位整數。

## <a name="return-value"></a>傳回值

`__m128`結構, 其第一個浮點值是轉換的結果。 其他三個值會從原封不動地複製。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結構表示 XMM 暫存器, 因此內建允許將系統記憶體中的值 b 移到 XMM 暫存器中。 `__m128`

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
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

[__m128](../cpp/m128.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
