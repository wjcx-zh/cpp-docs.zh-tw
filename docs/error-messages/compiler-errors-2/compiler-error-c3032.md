---
title: "編譯器錯誤 C3032 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3032"
ms.assetid: 6a92bd8e-319f-4a99-aef4-a9021f6f9928
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var'：'clause' 子句中的變數不能有不完整類型 'type'  
  
 傳遞給特定子句的類型必須為編譯器完整可見的類型。  
  
 下列範例會產生 C3032：  
  
```  
// C3032.cpp // compile with: /openmp /link vcomps.lib #include "omp.h" struct Incomplete; extern struct Incomplete inc; int main() { int i = 9; #pragma omp parallel private(inc)   // C3032 ; #pragma omp parallel private(i)     // OK ; }  
```