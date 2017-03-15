---
title: "__writecr3 | Microsoft Docs"
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
  - "_writecr3"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_writecr3 內建"
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writecr3
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 將值寫入`Data`到 CR3 暫存器。  
  
## 語法  
  
```  
void writecr3(   
   unsigned __int64 Data   
);  
```  
  
#### 參數  
 \[in\] `Data`  
 要寫入的 CR3 暫存器的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__writecr3`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建只適用於核心模式，並只可用作 \[內建常式，是。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)