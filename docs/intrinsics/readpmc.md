---
title: "__readpmc | Microsoft Docs"
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
  - "__readpmc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "讀取效能監視計數器指令"
  - "內建 __readpmc"
  - "rdpmc 指令"
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __readpmc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`rdpmc`指令，會讀取效能監視計數器所指定的`counter`。  
  
## 語法  
  
```  
unsigned __int64 __readpmc(   
   unsigned long counter   
);  
```  
  
#### 參數  
 \[in\] `counter`  
 讀取效能計數器。  
  
## 傳回值  
 指定的效能計數器的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__readpmc`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建可用於核心模式，同時只可用作 \[內建常式，是。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)