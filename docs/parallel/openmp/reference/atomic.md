---
title: "atomic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "atomic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atomic OpenMP directive"
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# atomic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示將會以原子方式更新的記憶體位置。  
  
## 語法  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### 參數  
 `expression`  
 您要防止多個寫入包含左值使用的記憶體位置的陳述式。  如需更多有關合法的運算式形式的詳細資訊，請參閱 OpenMP 規格。  
  
## 備註  
 `atomic`指示詞可支援任何 OpenMP 子句。  
  
 如需詳細資訊，請參閱 [2.6.4 atomic Construct](../../../parallel/openmp/2-6-4-atomic-construct.md)。  
  
## 範例  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
  **執行緒的數目: 10**   
## 請參閱  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)