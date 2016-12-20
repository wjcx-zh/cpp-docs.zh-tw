---
title: "_BitScanForward _BitScanForward64 | Microsoft Docs"
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
  - "_BitScanForward"
  - "_BitScanForward_cpp"
  - "_BitScanForward64_cpp"
  - "_BitScanForward64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 _BitScanForward"
  - "內建的 BitScanForward"
  - "bsf 指令"
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _BitScanForward _BitScanForward64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 從遮罩資料的最低有效位元 \(MSB\) 到最高有效位元 \(LSB\) 搜尋設定位元 \(1\)。  
  
## 語法  
  
```  
unsigned char _BitScanForward(    unsigned long * Index,    unsigned long Mask ); unsigned char _BitScanForward64(    unsigned long * Index,    unsigned __int64 Mask );  
```  
  
#### 參數  
 \[輸出\] `Index`  
 會使用找到的第一個設定位元 \(1\) 的位元位置載入。  
  
 \[in\] `Mask`  
 要搜尋的 32 位元或 64 位元值。  
  
## 傳回值  
 如果遮罩是零，則為 0；否則為非零。  
  
## 備註  
 如果找到設定位元，會在第一個參數中傳回找到的第一個設定位元的位元位置。  如果找不到設定位元，就會傳回 0；否則，會傳回 1。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_BitScanForward`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_BitScanForward64`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 範例  
  
```  
// BitScanForward.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanForward)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanForward(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## 輸入  
  
```  
12  
```  
  
## 範例輸出  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 2  
```  
  
### END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)