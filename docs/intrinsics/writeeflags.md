---
title: "__writeeflags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writeeflags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __writeeflags"
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __writeeflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將指定的值寫入至該程式狀態和控制項 \(EFLAGS\) 註冊。  
  
## 語法  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `Value`|要寫入的 EFLAGS 暫存器的值。  `Value`參數是 32 位元長度為 32 位元平台與 64 位元長度為 64 位元平台。|  
  
## 備註  
 這些常式會僅當作內建函式。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__writeeflags`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_readeflags](../intrinsics/readeflags.md)