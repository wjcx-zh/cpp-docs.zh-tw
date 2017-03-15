---
title: "__writedr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writedr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __writedr"
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __writedr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將指定的值寫入至指定的偵錯暫存器中。  
  
## 語法  
  
```  
void __writedr(unsigned DebugRegister, unsigned DebugValue);  
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);  
```  
  
#### 參數  
 \[in\] `DebugRegister`  
 介於 0 到 7，識別偵錯的暫存器。  
  
 \[in\] `DebugValue`  
 要寫入偵錯值暫存器。  
  
## 備註  
 這些內建函式只適用於核心模式，而且常式都可以使用僅為內建函式。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__writedr`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_readdr](../intrinsics/readdr.md)