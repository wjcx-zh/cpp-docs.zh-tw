---
title: "__writefsbyte、__writefsdword、__writefsqword、__writefsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writefsword"
  - "__writefsbyte"
  - "__writefsqword"
  - "__writefsdword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "writefsbyte 內建"
  - "__writefsword 內建"
  - "writefsqword 內建"
  - "writefsdword 內建"
  - "__writefsdword 內建"
  - "__writefsqword 內建"
  - "__writefsbyte 內建"
  - "writefsword 內建"
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __writefsbyte、__writefsdword、__writefsqword、__writefsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 寫入至指定相對於 FS 區段開頭的位移位置的記憶體。  
  
## 語法  
  
```  
void __writefsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writefsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writefsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writefsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從寫入 FS 開頭的位移。  
  
 \[in\] `Data`  
 要寫入的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__writefsbyte`|x86|  
|`__writefsword`|x86|  
|`__writefsdword`|x86|  
|`__writefsqword`|x86|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 這些常式會僅當作內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_readfsbyte、\_\_readfsdword、\_\_readfsqword、\_\_readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)