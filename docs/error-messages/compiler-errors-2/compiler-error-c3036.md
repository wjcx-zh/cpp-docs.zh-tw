---
title: 編譯器錯誤 C3036 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3036
dev_langs:
- C++
helpviewer_keywords:
- C3036
ms.assetid: 10c6993e-bc42-4a07-85c7-cdc34ac30906
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dbd3e6da3021303e1c66583383c2f514af4794a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246287"
---
# <a name="compiler-error-c3036"></a>編譯器錯誤 C3036
'operator': OpenMP 'reduction' 子句中有無效的運算子語彙基元  
  
 未正確指定 [reduction](../../parallel/openmp/reference/reduction.md) 子句。  
  
 下列範例會產生 C3036：  
  
```  
// C3036.cpp  
// compile with: /openmp  
static float a[1000], b[1000], c[1000];  
void test1(int first, int last) {  
   static float dp = 0.0f;  
   #pragma omp for nowait reduction(.:dp)   // C3036  
   // try the following line instead  
   // #pragma omp for nowait reduction(+: dp)  
   for (int i = first ; i <= last ; ++i)  
      dp += a[i] * b[i];  
}  
```