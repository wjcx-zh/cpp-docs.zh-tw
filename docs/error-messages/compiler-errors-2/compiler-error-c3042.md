---
title: 編譯器錯誤 C3042 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3042
dev_langs:
- C++
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32d2f88702bb3c1c2439dd2931ee269c9c1413ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3042"></a>編譯器錯誤 C3042
'copyprivate' 和 'nowait' 子句不可以同時出現在 OpenMP 'directive' 指示詞中  
  
 在指定的指示詞上， [copyprivate](../../parallel/openmp/reference/copyprivate.md) 與 [nowait](../../parallel/openmp/reference/nowait.md) 子句互斥。 若要修正這個錯誤，請移除 `copyprivate` 及/或 `nowait` 子句。  
  
 下列範例會產生 C3042：  
  
```  
// C3042.cpp  
// compile with: /openmp /c  
#include <stdio.h>  
#include "omp.h"  
  
double d;  
  
int main() {  
    #pragma omp parallel private(d)  
   {  
      #pragma omp single copyprivate(d) nowait   // C3042  
      {  
      }  
   }  
}  
```