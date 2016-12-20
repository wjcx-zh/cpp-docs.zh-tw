---
title: "__readmsr | Microsoft Docs"
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
  - "__readmsr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "讀取模型特定暫存器"
  - "rdmsr 指令"
  - "內建 __readmsr"
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __readmsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`rdmsr`指令時，其內容所指定的機型專有暫存器`register` ，並傳回其值。  
  
## 語法  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### 參數  
 \[in\] `register`  
 若要讀取模型特定的暫存器。  
  
## 傳回值  
 指定的暫存器中的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__readmsr`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 這個函式只適用於核心模式，並只可用作 \[內建常式，是。  
  
 如需詳細資訊，請參閱 AMD 說明文件。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)