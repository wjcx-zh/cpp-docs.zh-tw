---
title: "omp_get_wtime | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_get_wtime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_wtime OpenMP function"
ms.assetid: c8dee105-ec1b-42e5-a6e3-edeedcf9854c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# omp_get_wtime
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

傳回某個時間點之間所經歷的時間 \(秒\) 值。  
  
## 語法  
  
```  
double omp_get_wtime( );  
```  
  
## 傳回值  
 傳回值，以秒為單位的時間之間所經歷一些任意的但一致的點。  
  
## 備註  
 該點在程式執行期間，進行後續的比較可能都會保持一致。  
  
 如需詳細資訊，請參閱 [3.3.1 omp\_get\_wtime Function](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md)。  
  
## 範例  
  
```  
// omp_get_wtime.cpp  
// compile with: /openmp  
#include "omp.h"  
#include <stdio.h>  
#include <windows.h>  
  
int main() {  
    double start = omp_get_wtime( );  
    Sleep(1000);  
    double end = omp_get_wtime( );  
    double wtick = omp_get_wtick( );  
  
    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",  
             start, end, end - start);  
  
    printf_s("wtick = %.16g\n1/wtick = %.16g\n",  
             wtick, 1.0 / wtick);  
}  
```  
  
  **啟動 \= 594255.3671159324**  
**結束 \= 594256.3664474116**  
**差異 \= 0.9993314791936427**  
**wtick \= 2.793651148400146e\-007**  
**1\/wtick \= 3579545**   
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)