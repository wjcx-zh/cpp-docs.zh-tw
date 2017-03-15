---
title: "編譯器錯誤 C3048 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3048"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3048"
ms.assetid: 48e07091-94d9-471d-befe-7e2507631edd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3048
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\#pragma omp atomic' 後面的運算式格式指定錯誤  
  
 不正確地指定不可部分完成的指示詞。  
  
 下列範例會產生 C3048：  
  
```  
// C3048.cpp // compile with: /openmp vcomps.lib #include "omp.h" #include <stdio.h> int main() { int a[10]; omp_set_num_threads(4); #pragma omp parallel { #pragma omp atomic a[0] = 1;   // C3048 // try the following line instead // a[0] += 1; } }  
```