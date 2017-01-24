---
title: "__readcr3 | Microsoft Docs"
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
  - "__readcr3"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readcr3 內建"
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __readcr3
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 讀取 CR3 暫存器，並傳回其值。  
  
## 語法  
  
```  
unsigned __int64 __readcr3(void);  
```  
  
## 傳回值  
 CR3 暫存器中的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__readcr3`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建只適用於核心模式，並只可用作 \[內建常式，是。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)