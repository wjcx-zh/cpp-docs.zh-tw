---
title: "編譯器錯誤 C3039 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3039
dev_langs:
- C++
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: af2d6ef4fe93730265de6081fcb83f074dc6e4ec
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3039"></a>編譯器錯誤 C3039
'var': OpenMP 'for' 陳述式中的索引變數不可為削減變數  
  
 索引變數是隱含私用，所以變數不能在[減少](../../parallel/openmp/reference/reduction.md)中封入子句[平行](../../parallel/openmp/reference/parallel.md)指示詞。  
  
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
