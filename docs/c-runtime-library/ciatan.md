---
title: "_CIatan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIatan"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CIatan"
  - "CIatan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIatan 內建"
  - "_CIatan 內建"
ms.assetid: 3baa0429-fe46-4bab-8b00-868e2186dc8c
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIatan
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計算堆疊反正切函數的指數值  
  
## 語法  
  
```  
void __cdecl _CIatan();  
```  
  
## 備註  
 這個版本的 `atan` 函式擁有編譯器了解的特殊化慣用呼叫。  函式因為防止產生複本並幫助暫存器配置而加速執行。  
  
 結果值會被插入堆疊的頂端。  
  
## 需求  
 **平台：** x86  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)