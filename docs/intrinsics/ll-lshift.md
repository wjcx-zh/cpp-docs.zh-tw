---
title: "__ll_lshift | Microsoft Docs"
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
  - "__ll_lshift_cpp"
  - "__ll_lshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ll_lshift 內建"
  - "__ll_lshift 內建"
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __ll_lshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將所提供的 64 位元值向左移以指定的位元。  
  
## 語法  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### 參數  
 \[in\] `Mask`  
 64 位元整數的值，向左移位。  
  
 \[in\] `nBit`  
 要移位的位元數。  
  
## 傳回值  
 遮罩移位左`nBit`位元。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__ll_lshift`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 如果您編譯您的程式使用 64 位元架構和`nBit`超過 63，要移位的位元數是`nBit`模數 64。  如果您編譯程式，使用 32 位元架構和`nBit`大於 31，要移位的位元數是`nBit`模數 32。  
  
 `ll`在名稱中會指示這是一項作業，在`long long` \(`__int64`\)。  
  
## 範例  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## Output  
  
```  
10000  
```  
  
 **附註** ，則向左的移位運算的無不帶正負號的版本。  這是因為`__ll_lshift`已使用，則為不帶正負號的輸入的參數。  不像右移位中，左移位中，如沒有正負號相依關係，因為結果中的最小顯著性位元會永遠設為零的正負號的位移值而不考慮。  
  
### 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_ll\_rshift](../intrinsics/ll-rshift.md)   
 [\_\_ull\_rshift](../intrinsics/ull-rshift.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)