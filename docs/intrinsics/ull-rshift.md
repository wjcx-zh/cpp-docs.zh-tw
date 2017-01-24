---
title: "__ull_rshift | Microsoft Docs"
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
  - "__ull_rshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 ull_rshift"
  - "內建 __ull_rshift"
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __ull_rshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 在 x64，將右邊的第一個參數所指定的 64 位元值的第二個參數所指定的位元數。  
  
## 語法  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### 參數  
 \[in\] `mask`  
 若要向右移位 64 位元整數值。  
  
 \[in\] `nBit`  
 輪班，模數 x86 上的 32 和模數 x64 上的 64 位元數。  
  
## 傳回值  
 遮罩前移`nBit`位元。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__ull_rshift`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 如果第二個參數大於 31 在 x86 \(63 x64 上\)，該數字會採取模數 32 \(64 x 64 上\)，來判斷要移位的位元數。  `ull`在名稱中會指示`unsigned long long (unsigned __int64)`。  
  
## 範例  
  
```  
// ull_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ull_rshift)  
  
int main()  
{  
   unsigned __int64 mask = 0x100;  
   int nBit = 8;  
   mask = __ull_rshift(mask, nBit);  
   cout << hex << mask << endl;  
}  
```  
  
## Output  
  
```  
1  
```  
  
### 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_ll\_lshift](../intrinsics/ll-lshift.md)   
 [\_\_ll\_rshift](../intrinsics/ll-rshift.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)