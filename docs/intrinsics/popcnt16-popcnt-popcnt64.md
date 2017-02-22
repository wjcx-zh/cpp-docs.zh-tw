---
title: "__popcnt16、__popcnt、__popcnt64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__popcnt64"
  - "__popcnt"
  - "__popcnt16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "popcnt 指令"
  - "__popcnt16"
  - "__popcnt64"
  - "__popcnt"
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# __popcnt16、__popcnt、__popcnt64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 計算的其中一個 16\-、 32 或 64 位元不帶正負號的整數中的位元 \(擴展項目個數\)。  
  
## 語法  
  
```  
unsigned short __popcnt16(  
   unsigned short value  
);  
unsigned int __popcnt(  
   unsigned int value  
);  
unsigned __int64 __popcnt64(  
   unsigned __int64 value  
);  
```  
  
#### 參數  
 \[in\] `value`  
 16\-、 32 或 64 位元不帶正負號的整數，我們想要擴展計數。  
  
## 傳回值  
 在一個位元數`value`參數。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__popcnt16`|進階的位元操作|  
|`__popcnt`|進階的位元操作|  
|`__popcnt64`|在 64 位元模式的進階位元操作。|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 每個這些內建函式會產生 `popcnt`指令。  值的大小， `popcnt`指令會傳回其引數的大小相同。  在 32 位元模式有一般沒有 64 位元用途暫存器，因此沒有 64 位元`popcnt`。  
  
 若要判斷硬體支援`popcnt` 指令，請打`__cpuid`與內建`InfoType=0x00000001` ，並檢查 23 不少`CPUInfo[2] (ECX)`。  可說這個位元是 1，如果在指令都有支援，而 0。  如果您執行的程式碼會使用此內建不支援的硬體上`popcnt`指令時，結果會發生無法預期。  
  
## 範例  
  
```  
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
    usr = __popcnt16(us[i]);  
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __popcnt(ui[i]);  
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
  **\_\_popcnt16\(0x0\) \= 0 的 \_\_popcnt16\(0xff\) \= 8 \_\_popcnt16\(0xffff\) \= 16 \_\_popcnt\(0x0\) \= 0 的 \_\_popcnt\(0xff\) \= 8 \_\_oopcnt\(0xffff\) \= 16 \_\_popcnt\(0xffffffff\) \= 32**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)