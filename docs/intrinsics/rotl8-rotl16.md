---
title: "_rotl8 _rotl16 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_rotl8"
  - "_rotl16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 _rotl16"
  - "內建的 _rotl8"
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _rotl8 _rotl16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將輸入值依指定的位置數目，向左旋轉至最高有效位元 \(MSB\)。  
  
## 語法  
  
```  
unsigned char _rotl8(     unsigned char value,     unsigned char shift  ); unsigned short _rotl16(     unsigned short value,     unsigned char shift  );  
```  
  
#### 參數  
 \[in\] `value`  
 要旋轉的值。  
  
 \[in\] `shift`  
 要旋轉的位元數。  
  
## 傳回值  
 旋轉的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_rotl8`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_rotl16`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 與左移位運算不同的是，執行左旋轉運算時，在高位階外的高位位元會移到最低有效位元位置。  
  
## 範例  
  
```  
// rotl.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotl8, _rotl16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,  
               i, _rotl8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",  
            s, nBit, _rotl16(s, nBit));  
}  
```  
  
  **將 0x41 向左旋轉 0 個位元得出 0x41**  
**將 0x41 向左旋轉 1 個位元得出 0x82**  
**將 0x41 向左旋轉 2 個位元得出 0x5**  
**將 0x41 向左旋轉 3 個位元得出 0xa**  
**將 0x41 向左旋轉 4 個位元得出 0x14**  
**將 0x41 向左旋轉 5 個位元得出 0x28**  
**將 0x41 向左旋轉 6 個位元得出 0x50**  
**將 0x41 向左旋轉 7 個位元得出 0xa0**  
**將 unsigned short 0x12 向左旋轉 10 個位元得出 0x4800**   
## END Microsoft 特定的  
  
## 請參閱  
 [\_rotr8 \_rotr16](../intrinsics/rotr8-rotr16.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)