---
title: 編譯器錯誤 C3040 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3040
dev_langs:
- C++
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f895626ac04afc776c279f5e2bf7a857ffbd432
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3040"></a>編譯器錯誤 C3040
'var': 'reduction' 子句中的變數類型與削減運算子 'operator' 不相容  
  
 [reduction](../../parallel/openmp/reference/reduction.md) 子句中的變數不能和削減運算子一起使用。  
  
 下列範例會產生 C3040：  
  
```  
// C3040.cpp  
// compile with: /openmp /c  
#include "omp.h"  
double d;  
  
int main() {  
   #pragma omp parallel reduction(&:d)   // C3040  
      ;  
  
   #pragma omp parallel reduction(-:d)  // OK  
      ;  
}  
```