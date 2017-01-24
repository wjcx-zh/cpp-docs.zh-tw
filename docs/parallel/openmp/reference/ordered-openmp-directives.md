---
title: "ordered (OpenMP Directives) | Microsoft Docs"
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
  - "ordered"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ordered OpenMP directive"
ms.assetid: e1aa703e-d07d-4f6a-9b2a-f4f25203d850
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ordered (OpenMP Directives)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定在平行化程式碼，如應該像循序迴圈中執行迴圈。  
  
## 語法  
  
```  
#pragma omp ordered  
   structured-block  
```  
  
## 備註  
 **訂購**指示詞必須是動態的範圍內[for](../../../parallel/openmp/reference/for-openmp.md)或**平行的**建構包含**訂購**子句。  
  
 **訂購**指示詞可支援任何 OpenMP 子句。  
  
 如需詳細資訊，請參閱 [2.6.6 ordered Construct](../../../parallel/openmp/2-6-6-ordered-construct.md)。  
  
## 範例  
  
```  
// omp_ordered.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
static float a[1000], b[1000], c[1000];  
  
void test(int first, int last)   
{  
    #pragma omp for schedule(static) ordered  
    for (int i = first; i <= last; ++i) {  
        // Do something here.  
        if (i % 2)   
        {  
            #pragma omp ordered   
            printf_s("test() iteration %d\n", i);  
        }  
    }  
}  
  
void test2(int iter)   
{  
    #pragma omp ordered  
    printf_s("test2() iteration %d\n", iter);  
}  
  
int main( )   
{  
    int i;  
    #pragma omp parallel  
    {  
        test(1, 8);  
        #pragma omp for ordered  
        for (i = 0 ; i < 5 ; i++)  
            test2(i);  
    }  
}  
```  
  
  **test\(\) 反覆項目 1**  
**test\(\) 的反覆項目 3**  
**test\(\) 的反覆項目 5**  
**test\(\) 的反覆項目 7**  
**test2\(\) 反覆項目 0**  
**test2\(\) 反覆項目 1**  
**test2\(\) 的反覆項目 2**  
**test2\(\) 的反覆項目 3**  
**test2\(\) 的反覆項目 4**   
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)