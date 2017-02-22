---
title: "_mm_cvttss_si64x | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_cvttss_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mm_cvttss_si64x 內建"
  - "cvttss2si 指令"
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_cvttss_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 發出 x64 延伸的版本的截斷的單精確度浮點編號，64 位元整數，與 \[轉換 \(`cvttss2si`\) 的指令。  
  
## 語法  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### 參數  
 \[in\] `value`  
 `__m128`結構包含單精度浮點數值。  
  
## 傳回值  
 第一個浮點數的值轉換為 64 位元整數的結果。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_mm_cvttss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 設定不同的內建於`_mm_cvtss_si64x`只有一個不正確的轉換會被截斷趨近於零。  因為`__m128`結構是表示 xmm 暫存器、 產生的指令將資料從 xmm 暫存器移至系統記憶體。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// _mm_cvttss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvttss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] = { 101.5, 200.75,  
                                          300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvttss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
  **101**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_m128](../cpp/m128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)