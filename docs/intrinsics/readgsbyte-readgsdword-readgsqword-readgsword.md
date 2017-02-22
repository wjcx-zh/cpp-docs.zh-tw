---
title: "__readgsbyte、__readgsdword、__readgsqword、__readgsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readgsbyte"
  - "__readgsdword"
  - "__readgsqword"
  - "__readgsword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readgsword 內建"
  - "__readgsdword 內建"
  - "__readgsqword 內建"
  - "__readgsbyte 內建"
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __readgsbyte、__readgsdword、__readgsqword、__readgsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 從相對於 GS 區段開頭的位移所指定的位置上讀取記憶體。  
  
## 語法  
  
```  
unsigned char __readgsbyte(   
   unsigned long Offset   
);  
unsigned short __readgsword(   
   unsigned long Offset   
);  
unsigned long __readgsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readgsqword(   
   unsigned long Offset   
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從開頭的位移`GS`以讀取。  
  
## 傳回值  
 記憶體內容的位元組、 字、 雙字或 quadword \(如圖所呼叫的函式的名稱由表示\) 的任何位置， `GS:[``Offset``]`。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__readgsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 這些內建函式只適用於核心模式，常式，才可以使用與內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_writegsbyte、\_\_writegsdword、\_\_writegsqword、\_\_writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)