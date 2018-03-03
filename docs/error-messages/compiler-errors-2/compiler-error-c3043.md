---
title: "編譯器錯誤 C3043 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3043
dev_langs:
- C++
helpviewer_keywords:
- C3043
ms.assetid: 0ef55e63-e82b-48eb-9d44-690950ac34c6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c13b7457d8415bd020e3cd85a64273ec24ffe28a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3043"></a>編譯器錯誤 C3043
OpenMP 'critical' 指示詞不能以巢狀方式置於相同名稱的 'critical' 指示詞中  
  
 [critical](../../parallel/openmp/reference/critical.md) 指示詞不能以巢狀方式置於使用相同名稱的 `critical` 指示詞中。  
  
 下列範例會產生 C3043：  
  
```  
// C3043.cpp  
// compile with: /openmp /c  
#include "omp.h"  
  
int main() {  
   int n1 = 1, n2 = 2, n3 = 3;  
  
   #pragma omp parallel  
   {  
      ++n2;  
  
      #pragma omp critical(MyTest)  
      {  
         ++n2;  
  
         #pragma omp critical(MyTest)   // C3043  
         // try the following line instead  
         // #pragma omp critical(MyTest2)  
         {  
            ++n3;  
         }  
      }  
   }  
}  
```