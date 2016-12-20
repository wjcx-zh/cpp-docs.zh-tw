---
title: "__umulh | Microsoft Docs"
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
  - "__umulh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__umulh 內建函式"
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __umulh
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 傳回兩個 64 位元不帶正負號整數之乘積的 64 高位元。  
  
## 語法  
  
```  
unsigned __int64 __umulh(     unsigned __int64 a,     unsigned __int64 b  );  
```  
  
#### 參數  
 \[in\] `a`  
 要相乘的第一個數字。  
  
 \[in\] `b`  
 要相乘的第二個數字。  
  
## 傳回值  
 相乘的 128 位元結果的 64 高位元。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__umulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 這些常式只可做為內建函式。  
  
## 範例  
  
```  
// umulh.cpp  
// processor: X64  
#include <cstdio>  
#include <intrin.h>  
  
int main()  
{  
    unsigned __int64 i = 0x10;  
    unsigned __int64 j = 0xFEDCBA9876543210;  
    unsigned __int64 k = i * j; // k has the low 64 bits  
                                // of the product.  
    unsigned __int64 result;  
    result = __umulh(i, j); // result has the high 64 bits  
                            // of the product.  
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);  
    return 0;  
}  
```  
  
  **0x10 \* 0xfedcba9876543210 \= 0xfedcba98765432100**   
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)