---
title: "__writegsbyte、__writegsdword、__writegsqword、__writegsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writegsbyte"
  - "__writegsqword"
  - "__writegsdword"
  - "__writegsword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __writegsqword"
  - "內建 __writegsbyte"
  - "內建 __writegsword"
  - "內建 __writegsdword"
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __writegsbyte、__writegsdword、__writegsqword、__writegsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 寫入至指定相對於 GS 區段開頭的位移位置的記憶體。  
  
## 語法  
  
```  
void __writegsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writegsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writegsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writegsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### 參數  
 \[in\] `Offset`  
 從寫入 GS 開頭的位移。  
  
 \[in\] `Data`  
 要寫入的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__writegsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 這些內建函式只適用於核心模式，而且這些常式會僅當作內建函式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_\_readgsbyte、\_\_readgsdword、\_\_readgsqword、\_\_readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)