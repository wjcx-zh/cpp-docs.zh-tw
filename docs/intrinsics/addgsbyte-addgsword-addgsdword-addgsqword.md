---
title: "__addgsbyte、__addgsword、__addgsdword、__addgsqword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__addgsdword"
  - "__addgsqword"
  - "__addgsword_cpp"
  - "__addgsword"
  - "__addgsbyte_cpp"
  - "__addgsqword_cpp"
  - "__addgsbyte"
  - "__addgsdword_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __addgsword"
  - "內建 __addgsqword"
  - "內建 __addgsdword"
  - "內建 __addgsbyte"
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __addgsbyte、__addgsword、__addgsdword、__addgsqword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將值加入至開頭的相對位移所指定的記憶體位置`GS`區段。  
  
## 語法  
  
```  
void __addgsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __addgsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __addgsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __addgsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從開頭的位移`GS`。  
  
 \[in\] `Data`  
 要新增到記憶體位置的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__addgsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__addgsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__addgsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__addgsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## 備註  
 這些內建函式只適用於核心模式，而且這些常式會僅當作內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_incgsbyte、\_\_incgsword、\_\_incgsdword、\_\_incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)   
 [\_\_readgsbyte、\_\_readgsdword、\_\_readgsqword、\_\_readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [\_\_writegsbyte、\_\_writegsdword、\_\_writegsqword、\_\_writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)