---
title: "編譯器錯誤 C3026 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3026
dev_langs:
- C++
helpviewer_keywords:
- C3026
ms.assetid: 3297060e-cc5b-4600-a2db-09bfc4ffa21f
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3953553c8af6da98812c228f4b0bbf8c9428947d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3026"></a>編譯器錯誤 C3026
'clause': 常數運算式必須是正數  
  
 子句已傳遞整數值，但值不是正數。 數字必須是正數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3026：  
  
```  
// C3026.cpp  
// compile with: /openmp /link vcomps.lib  
#include <stdio.h>  
#include "omp.h"  
  
int main()  
{  
    int i;  
    const int i1 = 0;  
  
    #pragma omp parallel for num_threads(i1)   // C3026  
    for (i = 1; i <= 2; ++i)  
        printf_s("Hello World - thread %d - iteration %d\n",  
                 omp_get_thread_num(), i);  
  
    #pragma omp parallel for num_threads(i1 + 1)   // OK  
    for (i = 1; i <= 2; ++i)  
        printf_s("Hello World - thread %d - iteration %d\n",  
                 omp_get_thread_num(), i);  
}  
```
