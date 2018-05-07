---
title: 編譯器錯誤 C2540 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2540
dev_langs:
- C++
helpviewer_keywords:
- C2540
ms.assetid: 92c805a3-2dd9-46ca-a63d-3845c18ecc95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a618df6422c68b9fac04ef46192c176b9aa8b30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2540"></a>編譯器錯誤 C2540
非常數運算式當做陣列界限  
  
 陣列必須有常數繫結。  
  
 下列範例會產生 C2540:  
  
```  
// C2540.cpp  
void func(int n, int pC[]) {  
   int i = ((int [n])pC)[1];   // C2540  
}  
  
void func2(int n, int pC[]) {  
   int i = (pC)[1];   // OK  
}  
  
int main() {  
   int pC[100];  
   func(100, pC);  
   func2(100, pC);  
}  
```