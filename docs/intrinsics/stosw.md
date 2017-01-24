---
title: "__stosw | Microsoft Docs"
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
  - "__stosw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stosw 指令"
  - "內建 __stosw"
  - "rep stosw 指令"
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __stosw
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生存放字串指示 \(`rep stosw`\)。  
  
## 語法  
  
```  
void __stosw(   
   unsigned short* Dest,   
   unsigned short Data,   
   size_t Count   
);  
```  
  
#### 參數  
 \[out\] `Dest`  
 作業的目的地。  
  
 \[in\] `Data`  
 要儲存的資料。  
  
 \[in\] `Count`  
 要寫入的文字區塊的長度。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__stosw`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 結果是，這個字`Data`會寫入一段內`Count`特定的文字`Dest`的字串。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// stosw.c  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosw)  
  
int main()  
{  
    unsigned short val = 128;  
    unsigned short a[100];  
    memset(a, 0, sizeof(a));  
    __stosw(a+10, val, 2);  
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);     
}  
```  
  
  **0 128 128 0**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)