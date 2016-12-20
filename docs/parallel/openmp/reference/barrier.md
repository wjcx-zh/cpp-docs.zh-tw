---
title: "barrier | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "barrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "barrier OpenMP directive"
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# barrier
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

同步處理所有的執行緒在小組 ； 在障盾的所有執行緒都暫停，直到所有的執行緒執行的屏障。  
  
## 語法  
  
```  
#pragma omp barrier  
```  
  
## 備註  
 `barrier`指示詞可支援任何 OpenMP 子句。  
  
 如需詳細資訊，請參閱 [2.6.3 barrier Directive](../../../parallel/openmp/2-6-3-barrier-directive.md)。  
  
## 範例  
 範例中，如何使用`barrier`，請參閱[master](../../../parallel/openmp/reference/master.md)。  
  
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)