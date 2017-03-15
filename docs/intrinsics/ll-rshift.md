---
title: "__ll_rshift | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__ll_rshift_cpp"
  - "__ll_rshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__ll_rshift 內建"
  - "ll_rshift 內建"
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __ll_rshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將右邊的第一個參數所指定的 64 位元值的第二個參數所指定的位元數。  
  
## 語法  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### 參數  
 \[in\] `Mask`  
 若要向右移位 64 位元整數值。  
  
 \[in\] `nBit`  
 輪班，模數 64 x 64 上, 及取餘數在 x86 32 位元數。  
  
## 傳回值  
 遮罩前移`nBit`位元。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__ll_rshift`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 如果第二個參數大於 64 x 64 \(在 x86 32\) 上，該數字不會採取模數 64 \(在 x86 32\) 來決定要移位的位元數。  `ll`前置詞會指示這是一項作業，在`long long`、 另一個名稱為`__int64`，64 位元帶正負號整數類資料型別。  
  
## 範例  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## Output  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 **附註**如果`_ull_rshift`已被使用，向右移位標的值的 MSB 本來應該是零，因此您想要的結果可能尚未取得負數值的情況下。  
  
### 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_ll\_lshift](../intrinsics/ll-lshift.md)   
 [\_\_ull\_rshift](../intrinsics/ull-rshift.md)