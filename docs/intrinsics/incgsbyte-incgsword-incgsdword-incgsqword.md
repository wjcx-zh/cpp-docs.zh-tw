---
title: "__incgsbyte、__incgsword、__incgsdword、__incgsqword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__incgsdword"
  - "__incgsqword_cpp"
  - "__incgsword_cpp"
  - "__incgsword"
  - "__incgsbyte"
  - "__incgsbyte_cpp"
  - "__incgsqword"
  - "__incgsdword_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __incgsbyte"
  - "內建 __incgsword"
  - "內建 __incgsqword"
  - "內建 __incgsdword"
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __incgsbyte、__incgsword、__incgsdword、__incgsqword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 新增一個值在相對於開始的位移所指定的記憶體位置`GS`區段。  
  
## 語法  
  
```  
void __incgsbyte(   
   unsigned long Offset   
);  
void __incgsword(   
   unsigned long Offset   
);  
void __incgsdword(   
   unsigned long Offset  
);  
void __incgsqword(   
   unsigned long Offset   
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從開頭的位移`GS`。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__incgsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__incgsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__incgsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__incgsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## 備註  
 這些內建函式只適用於核心模式，常式，才可以使用與內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_addgsbyte、\_\_addgsword、\_\_addgsdword、\_\_addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)   
 [\_\_readgsbyte、\_\_readgsdword、\_\_readgsqword、\_\_readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [\_\_writegsbyte、\_\_writegsdword、\_\_writegsqword、\_\_writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)