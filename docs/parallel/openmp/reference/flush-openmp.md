---
title: "flush (OpenMP) | Microsoft Docs"
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
  - "Flush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "flush OpenMP directive"
ms.assetid: 150ca46e-d4f7-4423-b0a4-838df40aeb67
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# flush (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定所有執行緒都有相同的檢視，供所有的共用物件的記憶體。  
  
## 語法  
  
```  
#pragma omp flush [(var)]  
```  
  
## 備註  
 其中，  
  
 `var` \(選擇項\)  
 代表您要同步處理的物件變數以逗號分隔清單。  如果`var`未指定，清除所有的記憶體。  
  
## 備註  
 **排清**指示詞可支援任何 OpenMP 子句。  
  
 如需詳細資訊，請參閱 [2.6.5 flush Directive](../../../parallel/openmp/2-6-5-flush-directive.md)。  
  
## 範例  
  
```  
// omp_flush.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
void read(int *data) {  
   printf_s("read data\n");  
   *data = 1;  
}  
  
void process(int *data) {  
   printf_s("process data\n");  
   (*data)++;  
}  
  
int main() {  
   int data;  
   int flag;  
  
   flag = 0;  
  
   #pragma omp parallel sections num_threads(2)  
   {  
      #pragma omp section  
      {  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         read(&data);  
         #pragma omp flush(data)  
         flag = 1;  
         #pragma omp flush(flag)  
         // Do more work.  
      }  
  
      #pragma omp section   
      {  
         while (!flag) {  
            #pragma omp flush(flag)  
         }  
         #pragma omp flush(data)  
  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         process(&data);  
         printf_s("data = %d\n", data);  
      }  
   }  
}  
```  
  
  **引線 0: 讀取資料**  
**執行緒 1: 處理程序資料**  
**資料 \= 2**   
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)