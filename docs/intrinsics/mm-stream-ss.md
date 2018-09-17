---
title: _mm_stream_ss |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_ss
dev_langs:
- C++
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef5910f47fdf9c058cfb4493c9df486749da18fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714385"
---
# <a name="mmstreamss"></a>_mm_stream_ss  
  
**Microsoft 專屬**  
  
 將 32 位元資料寫入記憶體位置而不到處快取。  
  
## <a name="syntax"></a>語法  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### <a name="parameters"></a>參數  
  
*目的地*<br/>
[out]寫入來源資料的位置指標。  
  
*Source*<br/>
[in]包含 128 位元數字`float`以寫入下 32 位元的值...  
  
## <a name="return-value"></a>傳回值  
  
 無。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_mm_stream_ss`|SSE4a|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
  
此內建函式會產生`movntss`指令。 若要判斷此指令的硬體支援，請呼叫`__cpuid`與內建`InfoType=0x80000001`，並檢查位元 6 的`CPUInfo[2] (ECX)`。 此位元不支援指令時，1 和 0。  
  
如果您執行使用的程式碼`_mm_stream_ss`內建函式不支援的硬體上`movntss`指令，結果會無法預測。  
  
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

進階 Micro 裝置，inc.copyright 2007著作權所有，並保留一切權利。 進階 Micro 裝置，inc.的權限重製  
  
## <a name="see-also"></a>另請參閱  
 [_mm_stream_sd](../intrinsics/mm-stream-sd.md)   
 [_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)   
 [_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)