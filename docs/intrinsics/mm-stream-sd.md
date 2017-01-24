---
title: "_mm_stream_sd | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_stream_sd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 _mm_stream_sd"
  - "movntsd 指令"
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_stream_sd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將 64 位元資料寫入記憶體位置而不侵害快取。  
  
## 語法  
  
```  
void _mm_stream_sd(  
   double * Dest,  
   __m128d Source  
);  
```  
  
#### 參數  
 \[\] out`Dest`  
 來源資料寫入的位置的位置指標。  
  
 \[in\] `Source`  
 128 位元的值，包含`double`中撰寫它的下方 64 位元的值。.  
  
## 傳回值  
 無。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_mm_stream_sd`|SSE4a|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建會產生`movntsd` 指令。  若要判斷硬體支援，針對這個指令，請呼叫`__cpuid`與內建`InfoType=0x80000001` ，並檢查位元 6 的`CPUInfo[2] (ECX)`。  這個位元為 1，如果硬體可支援這個指令，而 0 否則。  
  
 如果您執行的程式碼，會使用`_mm_stream_sd`不支援的硬體上內建`movntsd`指令時，結果會發生無法預期。  
  
## 範例  
  
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
  
  **\[0\] d \=\-1，d \[1\] \= 1**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [\_mm\_stream\_ss](../intrinsics/mm-stream-ss.md)   
 [\_mm\_store\_sd](http://msdn.microsoft.com/zh-tw/8e672d0d-0a96-45b9-a783-392a2457de42)   
 [\_mm\_sfence](http://msdn.microsoft.com/zh-tw/b6c0d18e-3628-4318-826b-45f66782e870)   
 [Streaming SIMD Extensions that Support the Cache](http://msdn.microsoft.com/zh-tw/8f03493a-d5f5-4457-892e-0b6540494872)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)