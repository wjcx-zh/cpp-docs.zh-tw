---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 005f4f697d64f6ea68b35dc32daf1217be463a2a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217339"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Microsoft 專屬**

將32位資料寫入記憶體位置, 而不會污染快取。

## <a name="syntax"></a>語法

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷寫入來源資料之位置的指標。

*Source*\
在128位數位, 包含要在其`float`底部32位中寫入的值。

## <a name="return-value"></a>傳回值

無。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

內建函式會產生`movntss`指令。 若要判斷此指示的硬體支援, 請`__cpuid`使用`InfoType=0x80000001`呼叫內建函式並檢查的`CPUInfo[2] (ECX)`位6。 當支援指令時, 這個位是 1, 否則為0。

如果您在不`_mm_stream_ss` `movntss`支援指令的硬體上執行使用內建的程式碼, 結果會是無法預測的。

## <a name="example"></a>範例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**結束 Microsoft 專屬**

由 Advanced 微裝置, Inc. 的部分著作權2007著作權所有，並保留一切權利。 已從 Advanced 微裝置, Inc. 的許可權重現

## <a name="see-also"></a>另請參閱

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
