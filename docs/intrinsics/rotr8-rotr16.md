---
title: "_rotr8 _rotr16 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_rotr16"
  - "_rotr8"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 _rotr16"
  - "內建的 _rotr8"
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _rotr8 _rotr16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 依指定的位元位置數目，將輸入值旋轉至最低有效位元 \(LSB\) 的右方。  
  
## 語法  
  
```  
unsigned char _rotr8(     unsigned char value,     unsigned char shift  ); unsigned short _rotr16(     unsigned short value,     unsigned char shift  );  
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
|`_rotr8`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_rotr16`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 與向右移位作業不同，執行向右旋轉時，落於低端的低序位位元會移入高序位位元位置。  
  
## 範例  
  
```  
// rotr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotr8, _rotr16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x right by %d bits gives 0x%x\n", c,  
                i, _rotr8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x right by %d bits "  
             "gives 0x%x\n",  
            s, nBit, _rotr16(s, nBit));  
}  
```  
  
  **Rotating 0x41 right by 0 bits gives 0x41**  
**Rotating 0x41 right by 1 bits gives 0xa0**  
**Rotating 0x41 right by 2 bits gives 0x50**  
**Rotating 0x41 right by 3 bits gives 0x28**  
**Rotating 0x41 right by 4 bits gives 0x14**  
**Rotating 0x41 right by 5 bits gives 0xa**  
**Rotating 0x41 right by 6 bits gives 0x5**  
**Rotating 0x41 right by 7 bits gives 0x82**  
**Rotating unsigned short 0x12 right by 10 bits gives 0x480**   
## END Microsoft 特定的  
  
## 請參閱  
 [\_rotl8 \_rotl16](../intrinsics/rotl8-rotl16.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)