---
title: "編譯器錯誤 C3003 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3003
dev_langs:
- C++
helpviewer_keywords:
- C3003
ms.assetid: 22e74f99-bb7f-4518-ab0d-934d5d49bcc7
caps.latest.revision: 6
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
ms.openlocfilehash: c80fe6777bc980269c6c092d6a715d3ad683e2d4
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3003"></a>編譯器錯誤 C3003
'directive': OpenMP 指示詞名稱不能在指示詞子句後面  
  
 OpenMP 指示詞名稱不能在 OpenMP 指示詞子句後面。  
  
 下列範例會產生 C3003：  
  
```  
// C3003.c  
// compile with: /openmp  
int main()  
{  
   int x, y, z;  
   #pragma omp parallel shared(x, y, z) for   // C3003  
}  
```
