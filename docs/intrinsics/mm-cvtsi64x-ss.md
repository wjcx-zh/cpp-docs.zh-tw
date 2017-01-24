---
title: "_mm_cvtsi64x_ss | Microsoft Docs"
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
  - "_mm_cvtsi64x_ss"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cvtsi2ss 指令"
  - "內建 _mm_cvtsi64x_ss"
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_cvtsi64x_ss
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]的純量單精度浮點數值，轉換的 64 位元整數的延伸的版本 \(`cvtsi2ss`\) 的指令。  
  
## 語法  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### 參數  
 \[in\] `a`  
 `__m128`結構包含四個單精度浮點數值。  
  
 \[in\] `b`  
 以指定須轉換成浮點數值的 64 位元整數。  
  
## 傳回值  
 `__m128`結構，其第一個的浮點數值是轉換的結果。  其他三個值會複製不能改變的`a`。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_mm_cvtsi64x_ss`|x64|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `__m128`結構是表示 xmm 暫存器，所以此內建的允許值`b`從系統記憶體移到 XMM 暫存器。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
  **54.000000 0.000000 0.000000 0.000000**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_m128](../cpp/m128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)