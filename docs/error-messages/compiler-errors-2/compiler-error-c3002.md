---
title: 編譯器錯誤 C3002 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3002
dev_langs:
- C++
helpviewer_keywords:
- C3002
ms.assetid: 2d4241a7-c8eb-4d43-a128-dca255d137bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e69b2eede8e186347f7c3812901ef3c1dcc01495
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243270"
---
# <a name="compiler-error-c3002"></a>編譯器錯誤 C3002
'name1 name2': 多重 OpenMP 指示詞名稱  
  
 不允許多個指示詞名稱。  
  
 下列範例會產生 C3002：  
  
```  
// C3002.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp parallel single   // C3002  
}  
```