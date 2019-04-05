---
title: _mm_stream_sd
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: 3555b71e15d6f9c618a83f573d6da3cda9e7b705
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023512"
---
# <a name="mmstreamsd"></a>_mm_stream_sd

**Microsoft 特定的**

將 64 位元的資料寫入記憶體位置而不到處快取。

## <a name="syntax"></a>語法

```
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]將在其中寫入來源資料的位置指標。

*原始程式檔*<br/>
[in]128 位元值，包含`double`以寫入下 64 位元的值...

## <a name="return-value"></a>傳回值

無。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建函式會產生`movntsd`指令。 若要判斷此指令的硬體支援，請呼叫`__cpuid`與內建`InfoType=0x80000001`，並檢查位元 6 的`CPUInfo[2] (ECX)`。 如果硬體可支援此指令，以及 0 否則，此位元為 1。

如果您執行使用的程式碼`_mm_stream_sd`內建函式不支援的硬體上`movntsd`指令，結果會無法預測。

## <a name="example"></a>範例

```
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

**END Microsoft 特定的**

進階 Micro 裝置，inc.copyright 2007著作權所有，並保留一切權利。 進階 Micro 裝置，inc.的權限重製

## <a name="see-also"></a>另請參閱

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)<br/>
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)