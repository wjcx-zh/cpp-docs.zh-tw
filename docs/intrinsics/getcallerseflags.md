---
title: "__getcallerseflags | Microsoft Docs"
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
  - "_getcallerseflags"
  - "_getcallerseflags_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getcallerseflags 內建"
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __getcallerseflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 傳回的 EFLAGS 值從呼叫者的內容。  
  
## 語法  
  
```  
unsigned int __getcallerseflags(void);  
```  
  
## 傳回值  
 EFLAGS 值從呼叫者的內容。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__getcallerseflags`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// getcallerseflags.cpp  
// processor: x86, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__getcallerseflags)  
  
unsigned int g()  
{  
    unsigned int EFLAGS = __getcallerseflags();  
    printf_s("EFLAGS 0x%x\n", EFLAGS);  
    return EFLAGS;  
}  
unsigned int f()  
{  
    return g();  
}  
  
int main()  
{  
    unsigned int i;  
    i = f();  
    i = g();  
    return 0;  
}  
```  
  
  **EFLAGS 0X202 EFLAGS 0X206**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)