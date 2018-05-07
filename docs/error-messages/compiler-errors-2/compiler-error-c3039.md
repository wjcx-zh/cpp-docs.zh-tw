---
title: 編譯器錯誤 C3039 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3039
dev_langs:
- C++
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bdcfa36d270dc842eec0508969c650e7b30bee4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3039"></a>編譯器錯誤 C3039
'var': OpenMP 'for' 陳述式中的索引變數不可為削減變數  
  
 索引變數是隱含私用，因此變數不能用於封入 [parallel](../../parallel/openmp/reference/reduction.md) 指示詞的 [reduction](../../parallel/openmp/reference/parallel.md) 子句中。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3039：  
  
```  
// C3039.cpp  
// compile with: /openmp /c  
int g_i;  
  
int main() {  
   int i;  
  
   #pragma omp parallel reduction(+: i)  
   {  
      #pragma omp for  
      for (i = 0; i < 10; ++i)   // C3039  
         g_i += i;  
   }  
}  
```