---
title: 編譯器錯誤 C2387 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2387
dev_langs:
- C++
helpviewer_keywords:
- C2387
ms.assetid: 6847b8e1-ffac-458d-ab88-0c92f72f2527
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e490e2c0016649054c557026a5fa691162c40c07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2387"></a>編譯器錯誤 C2387
'type': 模稜兩可的基底類別  
  
 編譯器無法明確解析函式呼叫因為有一個以上的基底類別中的函式。  
  
 若要解決這個錯誤，請移除其中一個基底類別繼承，，或明確限定函式呼叫。  
  
 下列範例會產生 C2387:  
  
```  
// C2387.cpp  
namespace N1 {  
   struct B {  
      virtual void f() {  
      }  
   };  
}  
  
namespace N2 {  
   struct B {  
      virtual void f() {  
      }  
   };  
}  
  
struct D : N1::B, N2::B {  
   virtual void f() {  
      B::f();   // C2387  
      // try the following line instead  
      // N1::B::f();  
   }  
};  
  
int main() {  
   D aD;  
   aD.f();  
}  
```