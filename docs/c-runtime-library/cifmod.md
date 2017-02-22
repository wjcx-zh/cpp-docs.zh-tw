---
title: "_CIfmod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIfmod"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CIfmod"
  - "CIfmod"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIfmod 內建"
  - "_CIfmod 內建"
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIfmod
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計算頂端兩個值的浮點數餘數堆疊上。  
  
## 語法  
  
```  
void __cdecl _CIfmod();  
```  
  
## 備註  
 這個版本的 `fmod` 函式擁有編譯器了解的特殊化慣用呼叫。  函式因為防止產生複本並幫助暫存器配置而加速執行。  
  
 結果值會被插入堆疊的頂端。  
  
## 需求  
 **平台：** x86  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmod、fmodf](../c-runtime-library/reference/fmod-fmodf.md)