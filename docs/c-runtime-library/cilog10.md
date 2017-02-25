---
title: "_CIlog10 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIlog10"
apilocation: 
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIlog10"
  - "_CIlog10"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CIlog10 內建"
  - "CIlog10 內建"
ms.assetid: 05d7fcaa-3cff-4cc5-8d44-015e7cacba24
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIlog10
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行 `log10` 作業在堆疊頂端的值上。  
  
## 語法  
  
```  
void __cdecl _CIlog10();  
```  
  
## 備註  
 這個版本的 `log10` 函式擁有編譯器了解的特殊化慣用呼叫。  函式因為防止產生複本並幫助暫存器配置而加速執行。  
  
 結果值會被插入堆疊的頂端。  
  
## 需求  
 **平台：** x86  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)