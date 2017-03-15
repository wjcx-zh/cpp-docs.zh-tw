---
title: "__readdr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readdr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __readdr"
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# __readdr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

讀取指定的偵錯器的值。  
  
## 語法  
  
```  
unsigned         __readdr(unsigned int DebugRegister);  
unsigned __int64 __readdr(unsigned int DebugRegister);  
```  
  
#### 參數  
 \[in\] `DebugRegister`  
 從 0 到 7 的識別 debug 常數暫存器。  
  
## 傳回值  
 指定偵錯暫存器值。  
  
## 備註  
 這些內建函式只適用於核心模式，而且常式都可以使用僅為內建函式。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__readdr`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_readeflags](../intrinsics/readeflags.md)