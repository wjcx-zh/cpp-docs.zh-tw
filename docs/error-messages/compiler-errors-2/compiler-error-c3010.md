---
title: "編譯器錯誤 C3010 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3010
dev_langs: C++
helpviewer_keywords: C3010
ms.assetid: e959d038-bba6-432a-9c0a-0470474de7d9
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44003e751d87e946c5f56717f24d997ab0ea46a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3010"></a>編譯器錯誤 C3010
'label' : 不允許跳出 OpenMP 結構化區塊  
  
 程式碼不能跳入或跳出 OpenMP 區塊。  
  
 下列範例會產生 C3010：  
  
```  
// C3010.c  
// compile with: /openmp  
int main() {  
   #pragma omp parallel   
   {  
      #pragma omp parallel  
      {  
         goto lbl3;  
      }  
   }  
   lbl3:;   // C3010  
}  
```