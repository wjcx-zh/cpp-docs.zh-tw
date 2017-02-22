---
title: "__rdtscp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__rdtscp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rdtscp 內建"
  - "__rdtscp 內建"
  - "rdtscp 指令"
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __rdtscp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`rdtscp`指令時，會將`TSC_AUX[31:0`\] 的記憶體，並傳回 64 位元的時間戳記計數器 \(`TSC)`的結果。  
  
## 語法  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### 參數  
 \[out\] `Aux`  
 將包含的特定電腦的暫存器內容的位置指標`TSC_AUX[31:0]`。  
  
## 傳回值  
 64 位元不帶正負號的整數的滴答計數。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__rdtscp`|AMD NPT 家族 0Fh 或更新的版本|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建會產生`rdtscp`指令。  若要判斷硬體支援，針對這個指令，請呼叫`__cpuid` 與內建`InfoType=0x80000001` ，並檢查一些 27 `CPUInfo[3] (EDX)`。  可說這個位元是 1，如果在指令都有支援，而 0。  如果您執行的程式碼會使用此內建不支援的硬體上`rdtscp`指令時，結果會發生無法預期。  
  
> [!CAUTION]
>  不像`rdtsc`， `rdtscp`是序列化的指令。 不過，編譯器可以移動此程式碼內建。  
  
 與 TSC 值的解譯方式，在這個層代硬體的不同，在舊版的[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]。  請參閱硬體手冊，如需詳細資訊。  
  
 在 \[值的意義`TSC_AUX[31:0]`的作業系統而定。  
  
## 範例  
  
```  
#include <intrin.h>   
#include <stdio.h>  
int main()   
{  
 unsigned __int64 i;  
 unsigned int ui;  
 i = __rdtscp(&ui);  
 printf_s("%I64d ticks\n", i);  
 printf_s("TSC_AUX was %x\n", ui);  
}  
```  
  
  **3363423610155519 刻度已 0**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [\_\_rdtsc](../intrinsics/rdtsc.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)