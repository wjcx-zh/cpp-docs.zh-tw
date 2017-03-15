---
title: "_ 停用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_disable_cpp"
  - "_disable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ 停用內建"
  - "停用內建"
  - "rsm 指令"
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _ 停用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 停用中斷。  
  
## 語法  
  
```  
void _disable(void);  
```  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_disable`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `_disable` 指示處理器清除中斷旗標。  在 x86 系統中，這個函式會產生清除中斷旗標 \(`cli`\) 指令。  
  
 這個函式只適用於核心模式。  如果在使用者模式中使用，會在執行階段擲回有權限指令例外狀況。  
  
 在 ARM 平台上，此常式僅可作為內建常式使用。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)