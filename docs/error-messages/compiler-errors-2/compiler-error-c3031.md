---
title: "編譯器錯誤 C3031 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3031
dev_langs:
- C++
helpviewer_keywords:
- C3031
ms.assetid: 7e621e7e-eda7-45b5-8836-29599cd05255
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d74a10a87da0f9ed52f2ef91c159b539209f177
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3031"></a>編譯器錯誤 C3031
'var' : 'reduction' 子句中的變數必須有純量算術類型  
  
 錯誤類型的變數已傳遞給簡化子句。  
  
 下列範例會產生 C3031：  
  
```  
// C3031.cpp  
// compile with: /openmp /link vcomps.lib  
#include <stdio.h>  
#include "omp.h"  
  
typedef struct {  
   int n;  
} Incomplete;  
  
extern Incomplete inc;  
int i = 9;  
  
int main() {  
   #pragma omp parallel reduction(+: inc)   // C3031   
      ;  
  
   #pragma omp parallel reduction(+: i)     // OK  
      ;  
}  
```