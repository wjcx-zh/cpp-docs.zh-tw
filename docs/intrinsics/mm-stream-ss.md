---
title: "_mm_stream_ss | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_stream_ss"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movntss 指令"
  - "_mm_stream_ss 內建"
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _mm_stream_ss
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將 32 位元資料寫入記憶體位置而不侵害快取。  
  
## 語法  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### 參數  
 \[out\] `Dest`  
 要寫入的來源資料的位置的位置指標。  
  
 \[in\] `Source`  
 128 位元數字，其中包含`float`中撰寫它的下方 32 位元的值。.  
  
## 傳回值  
 無。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_mm_stream_ss`|SSE4a|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建會產生`movntss` 指令。  若要判斷硬體支援，針對這個指令，請呼叫`__cpuid`與內建`InfoType=0x80000001`，並檢查位元 6 的`CPUInfo[2] (ECX)`。  當支援指令時，這個位元為 1，否則為 0。  
  
 如果您執行的程式碼，會使用`_mm_stream_ss`不支援的硬體上內建`movntss`指令時，結果會發生無法預期。  
  
## 範例  
  
```  
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
  
  **\[0\] f \=\-1，\[1\] f \= \[2\] 的\-2 f \=\-3，f \[3\] \= 3**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [\_mm\_stream\_sd](../intrinsics/mm-stream-sd.md)   
 [\_mm\_stream\_ps](http://msdn.microsoft.com/zh-tw/f7af2f19-c0d4-43c6-b5f6-a658d2b1d869)   
 [\_mm\_store\_ss](http://msdn.microsoft.com/zh-tw/dfeeea35-8faf-4f54-8a9e-6723e226fb08)   
 [\_mm\_sfence](http://msdn.microsoft.com/zh-tw/b6c0d18e-3628-4318-826b-45f66782e870)   
 [Streaming SIMD Extensions that Support the Cache](http://msdn.microsoft.com/zh-tw/8f03493a-d5f5-4457-892e-0b6540494872)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)