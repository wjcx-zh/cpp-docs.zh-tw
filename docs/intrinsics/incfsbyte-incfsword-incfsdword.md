---
title: "__incfsbyte、__incfsword、__incfsdword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__incfsword"
  - "__incfsbyte_cpp"
  - "__incfsbyte"
  - "__incfsdword"
  - "__incfsword_cpp"
  - "__incfsdword_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __incfsword"
  - "內建 __incfsdword"
  - "內建 __incfsbyte"
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# __incfsbyte、__incfsword、__incfsdword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 新增一個值在相對於開始的位移所指定的記憶體位置`FS`區段。  
  
## 語法  
  
```  
void __incfsbyte(   
   unsigned long Offset   
);  
void __incfsword(   
   unsigned long Offset   
);  
void __incfsdword(   
   unsigned long Offset  
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從開頭的位移`FS`。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__incfsbyte`|x86|  
|`__incfsword`|x86|  
|`__incfsdword`|x86|  
  
## 備註  
 這些內建函式只適用於核心模式，常式，才可以使用與內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_addfsbyte、\_\_addfsword、\_\_addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)   
 [\_\_readfsbyte、\_\_readfsdword、\_\_readfsqword、\_\_readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [\_\_writefsbyte、\_\_writefsdword、\_\_writefsqword、\_\_writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)