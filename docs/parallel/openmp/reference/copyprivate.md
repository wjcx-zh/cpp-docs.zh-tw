---
title: "copyprivate | Microsoft Docs"
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
  - "copyprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copyprivate OpenMP clause"
ms.assetid: 02c0209d-abe8-4797-8365-a82b53c3f15d
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# copyprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定一或多個變數應該分擔所有執行緒。  
  
## 語法  
  
```  
copyprivate(var)  
```  
  
## 備註  
 其中，  
  
 `var`  
 若要共用的一或多個變數。  如果指定一個以上的變數，請以逗號分隔變數名稱。  
  
## 備註  
 `copyprivate`適用於[single](../../../parallel/openmp/reference/single.md)指示詞。  
  
 如需詳細資訊，請參閱 [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md)。  
  
## 範例  
  
```  
// omp_copyprivate.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
float x, y, fGlobal = 1.0;  
#pragma omp threadprivate(x, y)  
  
float get_float() {  
   fGlobal += 0.001;  
   return fGlobal;  
}  
  
void use_float(float f, int t) {  
   printf_s("Value = %f, thread = %d\n", f, t);  
}  
  
void CopyPrivate(float a, float b) {  
   #pragma omp single copyprivate(a, b, x, y)   
   {  
      a = get_float();  
      b = get_float();  
      x = get_float();  
      y = get_float();  
    }  
  
   use_float(a, omp_get_thread_num());     
   use_float(b, omp_get_thread_num());     
   use_float(x, omp_get_thread_num());  
   use_float(y, omp_get_thread_num());  
}  
  
int main() {  
   float a = 9.99, b = 123.456;  
  
   printf_s("call CopyPrivate from a single thread\n");  
   CopyPrivate(9.99, 123.456);  
  
   printf_s("call CopyPrivate from a parallel region\n");  
   #pragma omp parallel       
   {  
      CopyPrivate(a, b);  
   }  
}  
```  
  
  **從單一執行緒的呼叫 CopyPrivate**  
**值 \= 1.001000，執行緒 \= 0**  
**值 \= 1.002000，執行緒 \= 0**  
**值 \= 1.003000，執行緒 \= 0**  
**值 \= 1.004000，執行緒 \= 0**  
**從在平行區域呼叫 CopyPrivate**  
**值 \= 1.005000，執行緒 \= 0**  
**值 \= 1.005000，執行緒 \= 1**  
**值 \= 1.006000，執行緒 \= 0**  
**值 \= 1.006000，執行緒 \= 1**  
**值 \= 1.007000，執行緒 \= 0**  
**值 \= 1.007000，執行緒 \= 1**  
**值 \= 1.008000，執行緒 \= 0**  
**值 \= 1.008000，執行緒 \= 1**   
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)