---
title: "_mm_cvtss_si64x | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_cvtss_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cvtss2si 內建"
  - "_mm_cvtss_si64x 內建"
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _mm_cvtss_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]的轉換純量單一精確度浮點數值為 64 位元整數的延伸的版本 \(`cvtss2si`\) 的指令。  
  
## 語法  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### 參數  
 \[in\] `value`  
 `__m128`結構包含浮動的點值。  
  
## 傳回值  
 64 位元整數，第一個浮點數的值轉換成整數的結果。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 結構值的第一個元素會轉換成整數並傳回。  在 MXCSR 捨入的控制項位元用來判斷進位行為。  預設值捨入模式會四捨五入到最接近的偶數數字捨入，如果小數部份是 0.5。  因為`__m128`結構的表示 xmm 暫存器，此內建採用 xmm 暫存器的值，並將它寫入系統記憶體。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// _mm_cvtss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] =  
                           { 101.25, 200.75, 300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvtss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
  **101**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_m128d](../cpp/m128d.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)