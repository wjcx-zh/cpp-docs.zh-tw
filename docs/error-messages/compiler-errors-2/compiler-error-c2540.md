---
title: "編譯器錯誤 C2540 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2540
dev_langs:
- C++
helpviewer_keywords:
- C2540
ms.assetid: 92c805a3-2dd9-46ca-a63d-3845c18ecc95
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 047ee443a5cb8da4f5b5250681ac5e3ac4f917c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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