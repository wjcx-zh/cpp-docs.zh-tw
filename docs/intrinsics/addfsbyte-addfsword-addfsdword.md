---
title: "__addfsbyte、__addfsword、__addfsdword | Microsoft Docs"
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
  - "__addfsbyte_cpp"
  - "__addfsdword"
  - "__addfsword_cpp"
  - "__addfsbyte"
  - "__addfsword"
  - "__addfsdword_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__addfsdword 內建"
  - "__addfsword 內建"
  - "__addfsbyte 內建"
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __addfsbyte、__addfsword、__addfsdword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將值加入至開頭的相對位移所指定的記憶體位置`FS`區段。  
  
## 語法  
  
```  
void __addfsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __addfsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __addfsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從開頭的位移`FS`。  
  
 \[in\] `Data`  
 要新增到記憶體位置的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__addfsbyte`|x86|  
|`__addfsword`|x86|  
|`__addfsdword`|x86|  
  
## 備註  
 這些常式會僅當作內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_incfsbyte、\_\_incfsword、\_\_incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)   
 [\_\_readfsbyte、\_\_readfsdword、\_\_readfsqword、\_\_readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [\_\_writefsbyte、\_\_writefsdword、\_\_writefsqword、\_\_writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)