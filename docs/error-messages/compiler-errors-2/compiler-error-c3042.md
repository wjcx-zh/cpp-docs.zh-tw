---
title: "編譯器錯誤 C3042 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3042
dev_langs: C++
helpviewer_keywords: C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15099fd212c58df0369749a497a277ecb7f6987e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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