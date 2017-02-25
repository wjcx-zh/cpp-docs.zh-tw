---
title: "編譯器錯誤 C3054 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3054"
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

目前在泛型類別或函式中不支援 '\#pragma omp parallel'  
  
 如需詳細資訊，請參閱 [Generics](../../windows/generics-cpp-component-extensions.md) 與 [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C3054。  
  
```  
// C3054.cpp // compile with: /openmp /clr /c #include <omp.h> ref struct MyBaseClass { // Delete the following 7 lines to resolve. generic <class ItemType> void Test(ItemType i) {   // C3054 #pragma omp parallel num_threads(4) { int i = omp_get_thread_num(); } } // OK void Test2() { #pragma omp parallel num_threads(4) { int i = omp_get_thread_num(); } } };  
```