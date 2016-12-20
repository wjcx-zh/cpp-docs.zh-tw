---
title: "編譯器錯誤 C3044 | Microsoft Docs"
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
  - "C3044"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3044"
ms.assetid: 9f3e25b2-4676-49ab-97bf-6c88cd0fa377
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3044
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'section' : 只允許以巢狀方式直接放在 OpenMP 'sections' 指示詞之下  
  
 編譯器發現 `section` 指示詞的使用方式錯誤。 如需詳細資訊，請參閱[章節](../../parallel/openmp/reference/sections-openmp.md)。  
  
 下列範例會產生 C3044：  
  
```  
// C3044.cpp // compile with: /openmp /c #include "omp.h" int main() { int n2 = 2, n3 = 3; #pragma omp parallel { ++n2; #pragma omp sections { ++n2; } #pragma omp section   // C3044 { ++n3; } } #pragma omp parallel { ++n2; #pragma omp sections { #pragma omp section   // OK { ++n3; } } } }  
```