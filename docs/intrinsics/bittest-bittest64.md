---
title: "_bittest _bittest64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_bittest64"
  - "_bittest_cpp"
  - "_bittest64_cpp"
  - "_bittest"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 _bittest"
  - "內建的 _bittest64"
  - "bt 指令"
ms.assetid: 15e62afb-abea-4ee7-a6b1-13efa2034937
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _bittest _bittest64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 產生 `bt` 指令，該指令會檢查位址 `a` 的位置 `b` 中的位元，並傳回該位元的值。  
  
## 語法  
  
```  
unsigned char _bittest(    long *a,    long b ); unsigned char _bittest64(    __int64 *a,    __int64 b );  
```  
  
#### 參數  
 \[in\] `a`  
 要檢查的記憶體指標。  
  
 \[in\] `b`  
 要測試的位元位置。  
  
## 傳回值  
 位於指定位置的位元。  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`_bittest`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_bittest64`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## 備註  
 此常式僅可作為內建常式使用。  
  
## 範例  
  
```  
// bittest.cpp  
// processor: x86, ARM, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
long num = 78002;  
  
int main()  
{  
    unsigned char bits[32];  
    long nBit;  
  
    printf_s("Number: %d\n", num);  
  
    for (nBit = 0; nBit < 31; nBit++)  
    {  
        bits[nBit] = _bittest(&num, nBit);  
    }  
  
    printf_s("Binary representation:\n");  
    while (nBit--)  
    {  
        if (bits[nBit])  
            printf_s("1");  
        else  
            printf_s("0");  
    }  
}  
```  
  
  **號碼：78002**  
**二進位表示法：**  
**0000000000000010011000010110010**   
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)