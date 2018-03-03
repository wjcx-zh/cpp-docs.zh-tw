---
title: "編譯器錯誤 C2276 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2276
dev_langs:
- C++
helpviewer_keywords:
- C2276
ms.assetid: 62005ad9-6cb9-4b1f-965d-b875adaf695e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df0ef658b55ac4d94c30d4c7f2338a0f22f6947e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2276"></a>編譯器錯誤 C2276
'operator': 界限的成員函式運算式中不合法的操作  
  
 編譯器發現建立成員的指標的語法問題。  
  
 下列範例會產生 C2276:  
  
```  
// C2276.cpp  
class A {  
public:  
   int func(){return 0;}  
} a;  
  
int (*pf)() = &a.func;   // C2276  
// try the following line instead  
// int (A::*pf3)() = &A::func;  
  
class B {  
public:  
   void mf() {  
      &this -> mf;   // C2276  
      // try the following line instead  
      // &B::mf;  
   }  
};  
  
int main() {  
   A a;  
   &a.func;   // C2276  
   // try the following line instead  
   // &A::func;  
}  
```