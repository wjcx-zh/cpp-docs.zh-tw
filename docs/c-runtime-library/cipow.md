---
title: "_CIpow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIpow"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIpow"
  - "_CIpow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIpow 內建"
  - "_CIpow 內建"
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIpow
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

依照堆疊頂端的值，計算*x*的*y*次方。  
  
## 語法  
  
```  
void __cdecl _CIpow();  
```  
  
## 備註  
 這個版本的 `pow` 函式擁有編譯器了解的特殊化慣用呼叫。  函式因為防止產生複本並幫助暫存器配置而加速執行。  
  
 結果值會被插入堆疊的頂端。  
  
## 需求  
 **平台：** x86  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [pow、powf、powl](../c-runtime-library/reference/pow-powf-powl.md)