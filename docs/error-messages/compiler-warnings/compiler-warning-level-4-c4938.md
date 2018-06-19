---
title: 編譯器警告 （層級 4） C4938 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4938
dev_langs:
- C++
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b069e233072e653f848da61423411875d817cef0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294823"
---
# <a name="compiler-warning-level-4-c4938"></a>編譯器警告 (層級 4) C4938
'var': 浮點削減變數在 /fp:strict 或 #pragma fenv_access 之下可能會造成不一致的結果  
  
 您不應該搭配使用 [/fp:strict](../../build/reference/fp-specify-floating-point-behavior.md) 或 [fenv_access](../../preprocessor/fenv-access.md) 與 OpenMP 浮點削減，因為是以不同的順序計算總和。 因此，結果可能會與沒有 /openmp 的結果不同。  
  
 下列範例會產生 C4938：  
  
```  
// C4938.cpp  
// compile with: /openmp /W4 /fp:strict /c  
// #pragma fenv_access(on)  
extern double *a;   
  
double test(int first, int last) {   
   double sum = 0.0;   
   #pragma omp parallel for reduction(+: sum)   // C4938  
   for (int i = first ; i <= last ; ++i)   
      sum += a[i];   
   return sum;   
}  
```  
  
 如果沒有明確平行化作業，則總和的計算方式如下：  
  
```  
sum = a[first] + a[first + 1] + ... + a[last];   
```  
  
 如果有明確平行化作業 (和兩個執行緒)，則總和的計算方式如下：  
  
```  
sum1 = a[first] + ... a[first + last / 2];   
sum2 = a[(first + last / 2) + 1] + ... a[last];   
sum = sum1 + sum2;  
```