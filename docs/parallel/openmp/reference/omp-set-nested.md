---
title: "omp_set_nested | Microsoft Docs"
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
  - "omp_set_nested"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_nested OpenMP function"
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_set_nested
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

可讓巢狀的平行處理。  
  
## 語法  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## 備註  
 其中，  
  
 `val`  
 如果不為零，可讓巢狀的平行處理原則。  如果是零，會停用巢狀的平行處理原則。  
  
## 備註  
 巢狀的 OMP 平行處理可以開啟與`omp_set_nested`，或藉由設定[OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md)環境變數。  
  
 將`omp_set_nested`將會覆寫的設定值`OMP_NESTED`環境變數。  
  
 啟用時，環境變數可以中斷否則操作的程式，因為在巢狀處理平行區域以指數方式增加執行緒數量。  例如 OMP 設定為 4 的執行緒數目與 6 倍進行遞迴需要 4096 \(4 \/ 6 次方\) 的函式執行緒在一般情況下，如果執行緒的數目超過處理器數目，將會降低應用程式的效能。  此例外的情況就是應用程式的 I\/O 繫結。  
  
 使用[omp\_get\_nested](../../../parallel/openmp/reference/omp-get-nested.md)以顯示目前設定的`omp_set_nested`。  
  
 如需詳細資訊，請參閱 [3.1.9 omp\_set\_nested Function](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。  
  
## 範例  
  
```  
// omp_set_nested.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_nested(1);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_nested( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_nested( ));  
        }  
}  
```  
  
  **1**  
**1**   
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)