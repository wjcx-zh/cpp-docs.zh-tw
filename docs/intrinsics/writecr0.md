---
title: "__writecr0 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_writecr0"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 _writecr0"
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __writecr0
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將值寫入`Data`到 CR0 暫存器。  
  
## 語法  
  
```  
void writecr0(   
   unsigned __int64 Data   
);  
```  
  
#### 參數  
 \[in\] `Data`  
 要寫入的 CR0 的暫存器的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__writecr0`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建只適用於核心模式，並只可用作 \[內建常式，是。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)