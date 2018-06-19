---
title: 編譯器錯誤 C3001 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3001
dev_langs:
- C++
helpviewer_keywords:
- C3001
ms.assetid: d0e03478-1b44-47e5-8f5b-70415fa1f8bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4c8275b1fc511ebf4e09b625f64cffae74a3ca6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263081"
---
# <a name="compiler-error-c3001"></a>編譯器錯誤 C3001
'error_text': 需要 OpenMP 指示詞名稱  
  
 `omp` pragma 之後必須是指示詞。  
  
 下列範例會產生 C3001：  
  
```  
// C3001.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp   // C3001 missing token  
}  
```