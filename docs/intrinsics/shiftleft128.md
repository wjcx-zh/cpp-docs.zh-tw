---
title: "__shiftleft128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__shiftleft128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 __shiftleft128"
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# __shiftleft128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 移位 128 位元數量，表示兩個距離左邊達 `Shift` 指定之位元數的 64 位元數量 `LowPart` 和 `HighPart`，並傳回結果的較高 64 個位元。  
  
## 語法  
  
```  
unsigned __int64 __shiftleft128(     unsigned __int64 LowPart,     unsigned __int64 HighPart,     unsigned char Shift  );  
```  
  
#### 參數  
 \[in\] `LowPart`  
 要移位的 128 位元數量的較低 64 個位元。  
  
 \[in\] `HighPart`  
 要移位的 128 位元數量的較高 64 個位元。  
  
 \[in\] `Shift`  
 要移位的位元數。  
  
## 傳回值  
 結果的較高 64 個位元。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__shiftleft128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `Shift` 值一律為模數 64，使得 \(舉例而言\) 如果您呼叫 `__shiftleft128(1, 0, 64)`，函式將向左移低部分 `0` 個位元，並傳回 `0` 而非 `1` 的高部分，因為將會預期其他值。  
  
## 範例  
  
```  
// shiftleft128.c  
// processor: IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__shiftleft128, __shiftright128)  
  
int main()  
{  
    unsigned __int64 i = 0x1I64;  
    unsigned __int64 j = 0x10I64;  
    unsigned __int64 ResultLowPart;  
    unsigned __int64 ResultHighPart;  
  
    ResultLowPart = i << 1;  
    ResultHighPart = __shiftleft128(i, j, 1);  
  
    // concatenate the low and high parts padded with 0's  
    // to display correct hexadecimal 128 bit values  
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);  
  
    ResultHighPart = j >> 1;  
    ResultLowPart = __shiftright128(i, j, 1);  
  
    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);    
}  
```  
  
  **0x100000000000000001 \<\< 1 \= 0x200000000000000002**  
**0x100000000000000001 \>\> 1 \= 0x080000000000000000**   
## END Microsoft 特定的  
  
## 請參閱  
 [\_\_shiftright128](../intrinsics/shiftright128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)