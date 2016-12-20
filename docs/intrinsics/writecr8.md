---
title: "__writecr8 | Microsoft Docs"
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
  - "_writecr8"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_writecr8 內建"
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writecr8
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將值寫入`Data`到 CR8 暫存器。  
  
## 語法  
  
```  
void writecr8(   
   unsigned __int64 Data   
);  
```  
  
#### 參數  
 \[in\] `Data`  
 要寫入的 CR8 暫存器的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__writecr8`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建只適用於核心模式，並只可用作 \[內建常式，是。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)