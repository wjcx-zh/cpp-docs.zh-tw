---
title: "__stosd | Microsoft Docs"
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
  - "__stosd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stosd 指令"
  - "rep stosd 指令"
  - "內建 __stosd"
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __stosd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生存放字串指示 \(`rep stosd`\)。  
  
## 語法  
  
```  
void __stosd(   
   unsigned long* Dest,   
   unsigned long Data,   
   size_t Count   
);  
```  
  
#### 參數  
 \[out\] `Dest`  
 作業的目的地。  
  
 \[in\] `Data`  
 要儲存的資料。  
  
 \[in\] `Count`  
 要寫入的 doublewords 的區塊的長度。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__stosd`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 結果是 doubleword `Data`會寫入一段內`Count`所指的記憶體位置 doublewords `Dest`。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// stosd.c  
// processor: x86, x64  
  
#include <stdio.h>  
#include <memory.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosd)  
  
int main()  
{  
    unsigned long val = 99999;  
    unsigned long a[10];  
  
    memset(a, 0, sizeof(a));  
    __stosd(a+1, val, 2);  
  
printf_s( "%u %u %u %u",  
              a[0], a[1], a[2], a[3]);   
}  
```  
  
  **0 99999 99999 0**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)