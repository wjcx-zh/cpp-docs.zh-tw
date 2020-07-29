---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: ec639004884d022fe6a827c2ec31d3201ea04657
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214213"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Microsoft 特定的**

將64位資料寫入記憶體位置，而不會污染快取。

## <a name="syntax"></a>語法

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>參數

*Dest*\
脫銷將寫入來源資料之位置的指標。

*來源*\
在128位值，其中包含 **`double`** 要在其底部64位中寫入的值。

## <a name="return-value"></a>傳回值

無。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**標頭檔** \<intrin.h>

## <a name="remarks"></a>備註

內建函式會產生 `movntsd` 指令。 若要判斷此指示的硬體支援，請 `__cpuid` 使用呼叫內建函式 `InfoType=0x80000001` 並檢查的位 6 `CPUInfo[2] (ECX)` 。 如果硬體支援此指令，則此位為1，否則為0。

如果您在不支援指令的硬體上執行使用內建的程式碼 `_mm_stream_sd` `movntsd` ，結果會是無法預測的。

## <a name="example"></a>範例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}
```

```Output
d[0] = -1, d[1] = 1
```

**結束 Microsoft 專有**

由 Advanced 微裝置，Inc. 的部分著作權2007已保留擁有權限。 已從 Advanced 微裝置，Inc. 的許可權重現

## <a name="see-also"></a>另請參閱

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
