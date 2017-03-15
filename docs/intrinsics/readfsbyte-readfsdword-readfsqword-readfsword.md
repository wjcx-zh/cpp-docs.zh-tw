---
title: "__readfsbyte、__readfsdword、__readfsqword、__readfsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readfsword"
  - "__readfsdword"
  - "__readfsbyte"
  - "__readfsqword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readfsword 內建"
  - "readfsword 內建"
  - "__readfsdword 內建"
  - "readfsbyte 內建"
  - "__readfsbyte 內建"
  - "readfsdword 內建"
  - "readfsqword 內建"
  - "__readfsqword 內建"
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __readfsbyte、__readfsdword、__readfsqword、__readfsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 從相對於 FS 區段開頭的位移所指定的位置上讀取記憶體。  
  
## 語法  
  
```  
unsigned char __readfsbyte(   
   unsigned long Offset   
);  
unsigned short __readfsword(   
   unsigned long Offset   
);  
unsigned long __readfsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readfsqword(   
   unsigned long Offset   
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從開頭的位移`FS`以讀取。  
  
## 傳回值  
 記憶體內容的位元組、 字、 doubleword 或 quadword \(如圖所呼叫的函式的名稱由表示\) 的任何位置， `FS:[``Offset``]`。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__readfsbyte`|x86|  
|`__readfsdword`|x86|  
|`__readfsqword`|x86|  
|`__readfsword`|x86|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 這些常式會僅當作內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_writefsbyte、\_\_writefsdword、\_\_writefsqword、\_\_writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)