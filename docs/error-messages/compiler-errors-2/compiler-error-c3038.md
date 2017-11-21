---
title: "編譯器錯誤 C3038 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3038
dev_langs: C++
helpviewer_keywords: C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ddd3aaface0e500dc92778333cd3672398909da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3038"></a>編譯器錯誤 C3038
'var': 'private' 子句中的變數在封入內容中不可為削減變數  
  
 在平行指示詞的 [reduction](../../parallel/openmp/reference/reduction.md) 子句中出現的變數，不能指定於繫結至平行建構之工作共用指示詞的 [private](../../parallel/openmp/reference/private-openmp.md) 子句中。  
  
 下列範例會產生 C3038：  
  
```  
// C3038.cpp  
// compile with: /openmp /c  
int g_i, g_i2;  
  
int main() {  
   int i;  
  
   #pragma omp parallel reduction(+: g_i)  
   {  
      #pragma omp for private(g_i)   // C3038  
      // try the following line instead  
      // #pragma omp for private(g_i2)  
      for (i = 0; i < 10; ++i)  
         g_i += i;  
   }  
}  
```