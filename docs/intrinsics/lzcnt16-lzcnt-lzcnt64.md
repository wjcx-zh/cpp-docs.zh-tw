---
title: "__lzcnt16，__lzcnt，__lzcnt64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__lzcnt64"
  - "__lzcnt16"
  - "__lzcnt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__lzcnt 內建"
  - "lzcnt 指令"
  - "lzcnt16 內建"
  - "lzcnt 內建"
  - "__lzcnt16 內建"
  - "lzcnt64 內建"
  - "__lzcnt64 內建"
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __lzcnt16，__lzcnt，__lzcnt64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 計數的前置字元零 16\-、 32 或 64 位元的整數。  
  
## 語法  
  
```  
unsigned short __lzcnt16(  
   unsigned short value  
);  
unsigned int __lzcnt(  
   unsigned int value  
);  
unsigned __int64 __lzcnt64(  
   unsigned __int64 value  
);  
```  
  
#### 參數  
 \[in\] `value`  
 16\-、 32 或 64 位元不帶正負號的整數，若要掃描的以零開始。  
  
## 傳回值  
 前置零的位元中的`value`參數。  如果`value`為零，則傳回值是輸入運算元的值 \(16、 32 或 64\) 的大小。  如果最重要的位元的`value`為 1，則傳回值為零。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__lzcnt16`|進階的位元操作|  
|`__lzcnt`|進階的位元操作|  
|`__lzcnt64`|在 64 位元模式的進階位元操作。|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 每個這些內建函式會產生`lzcnt`指令。  值的大小， `lzcnt`指令會傳回其引數的大小相同。  在 32 位元模式有一般沒有 64 位元用途暫存器，因此沒有 64 位元`lzcnt`。  
  
 若要判斷硬體支援 `lzcnt`指令呼叫`__cpuid`與內建`InfoType=0x80000001` ，並檢查位元 5 的`CPUInfo[2] (ECX)`。  這個位元會支援指令時，若為 1 和 0 否則。  如果您執行的程式碼會使用此內建不支援的硬體上 `lzcnt`指令時，結果會發生無法預期。  
  
## 範例  
  
```  
// Compile this test with: /EHsc  
#include <iostream>   
#include <intrin.h>   
using namespace std;   
  
int main()   
{  
  unsigned short us[3] = {0, 0xFF, 0xFFFF};  
  unsigned short usr;  
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};  
  unsigned int   uir;  
  
  for (int i=0; i<3; i++) {  
    usr = __lzcnt16(us[i]);  
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __lzcnt(ui[i]);  
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
  **\_\_lzcnt16\(0x0\) \= 16 \_\_lzcnt16\(0xff\) \= 8 \_\_lzcnt16\(0xffff\) \= 0 的 \_\_lzcnt\(0x0\) \= 32 \_\_lzcnt\(0xff\) \= 24 \_\_lzcnt\(0xffff\) \= 16 \_\_lzcnt\(0xffffffff\) \= 0**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)