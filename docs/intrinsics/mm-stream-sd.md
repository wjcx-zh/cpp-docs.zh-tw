---
title: "_mm_stream_sd |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mm_stream_sd
dev_langs: C++
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da88116f58c6e33d35a69ebb6ac2433a8fe8f4ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mmstreamsd"></a>_mm_stream_sd
**Microsoft 特定的**  
  
 寫入記憶體位置的 64 位元的資料不侵害快取。  
  
## <a name="syntax"></a>語法  
  
```  
void _mm_stream_sd(  
   double * Dest,  
   __m128d Source  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `Dest`  
 要寫入的來源資料的位置指標。  
  
 [輸入] `Source`  
 128 位元值，包含`double`64 位元在其下要寫入值...  
  
## <a name="return-value"></a>傳回值  
 無。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_mm_stream_sd`|SSE4a|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建函式會產生`movntsd`指令。 若要判斷硬體支援此指示，請呼叫`__cpuid`與內建`InfoType=0x80000001`並檢查位元 6 的`CPUInfo[2] (ECX)`。 如果硬體可支援此指示，以及 0 否則，此位元為 1。  
  
 如果您執行程式碼乃使用`_mm_stream_sd`內建函式不支援的硬體上`movntsd`指令，結果會產生無法預測。  
  
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
  
**結束 Microsoft 特定的**  
 進階微裝置，inc.著作權 2007著作權所有，並保留一切權利。 重製進階微裝置，Inc.的權限。  
  
## <a name="see-also"></a>請參閱  
 [_mm_stream_ss](../intrinsics/mm-stream-ss.md)   
 [_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)