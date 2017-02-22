---
title: "__rdtsc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__rdtsc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__rdtsc 內建"
  - "rdtsc 指令"
  - "讀取時間戳記計數器指令"
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# __rdtsc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`rdtsc`指令時，它會傳回處理器的時間戳記。  處理器時間戳記會記錄上次重設後的時脈週期數。  
  
## 語法  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## 傳回值  
 64 位元不帶正負號的整數，表示滴答計數。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__rdtsc`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 使用僅當做內建這個常式。  
  
 與 TSC 值的解譯方式，在這個層代硬體的不同，在舊版的[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]。  請參閱硬體手冊，如需詳細資訊。  
  
## 範例  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
  **3363423610155519 的刻度**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)