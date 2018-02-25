---
title: "_mm_stream_ss |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_stream_ss
dev_langs:
- C++
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 420952d58bb46012741ee95ced4cf39c12d381cd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="mmstreamss"></a>_mm_stream_ss  
  
**Microsoft 特定的**  
  
 寫入記憶體位置的 32 位元的資料不侵害快取。  
  
## <a name="syntax"></a>語法  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### <a name="parameters"></a>參數  
  
 [輸出] `Dest`  
 來源資料所寫入之位置指標。  
  
 [輸入] `Source`  
 包含 128 位元數字`float`32 位元在其下要寫入值...  
  
## <a name="return-value"></a>傳回值  
  
 無。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_mm_stream_ss`|SSE4a|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
  
此內建函式會產生`movntss`指令。 若要判斷硬體支援此指示，請呼叫`__cpuid`與內建`InfoType=0x80000001`並檢查位元 6 的`CPUInfo[2] (ECX)`。 此位元否則就會支援指令時，1 和 0。  
  
如果您執行程式碼乃使用`_mm_stream_ss`內建函式不支援的硬體上`movntss`指令，結果會產生無法預測。  
  
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
  
**結束 Microsoft 特定的**  

進階微裝置，inc.著作權 2007著作權所有，並保留一切權利。 重製進階微裝置，Inc.的權限。  
  
## <a name="see-also"></a>請參閱  
 [_mm_stream_sd](../intrinsics/mm-stream-sd.md)   
 [_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)   
 [_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)