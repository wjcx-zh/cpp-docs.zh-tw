---
title: "_CIsqrt | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIsqrt"
apilocation: 
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CIsqrt"
  - "CIsqrt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIsqrt 內建"
  - "_CIsqrt 內建"
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CIsqrt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計算頂端值的平方根堆疊上。  
  
## 語法  
  
```  
void __cdecl _CIsqrt();  
```  
  
## 備註  
 這個版本的 `sqrt` 函式擁有編譯器了解的特殊化慣用呼叫。  函式因為防止產生複本並幫助暫存器配置而加速執行。  
  
 結果值會被插入堆疊的頂端。  
  
## 需求  
 **平台：** x86  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [sqrt、sqrtf、sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)