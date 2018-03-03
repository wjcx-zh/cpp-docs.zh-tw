---
title: "編譯器錯誤 C2247 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2247
dev_langs:
- C++
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eac2f90d689bf230b317a0443b5ec79ab40be632
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2247"></a>編譯器錯誤 C2247
' identifier' 無法存取，因為 'class' 會使用繼承自 'class' 的 'specifier'  
  
 `identifier`繼承自宣告具有私用或受保護的存取權的類別。  
  
 下列範例會產生 C2247:  
  
```  
// C2247.cpp  
class A {  
public:  
   int i;  
};  
class B : private A {};    // B inherits a private A  
class C : public B {} c;   // so even though C's B is public  
int j = c.i;               // C2247, i not accessible  
```  
  
 也可以針對 Visual Studio.NET 2003年所進行的編譯器一致性工作產生這個錯誤： 存取控制與受保護的成員。 受保護的成員 (n) 只在透過繼承自它 (n) 為成員的類別 (A) 的類別 (B) 的成員函式中存取。  
  
 針對 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的程式碼，宣告為 friend 類型的成員。 也可以使用公用繼承。  
  
```  
// C2247b.cpp  
// compile with: /c  
// C2247 expected  
class A {  
public:  
   void f();  
   int n;  
};  
  
class B: protected A {  
   // Uncomment the following line to resolve.  
   // friend void A::f();  
};  
  
void A::f() {  
   B b;  
   b.n;  
}  
```  
  
 也可能因為針對 Visual Studio.NET 2003年所進行的編譯器一致性處理而產生 C2247： 私用基底類別現在無法存取。 類型的私用基底類別的類別 (A) （B） 不應存取的型別 （C），用做基底類別。  
  
 針對 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的程式碼，使用範圍運算子。  
  
```  
// C2247c.cpp  
// compile with: /c  
struct A {};  
  
struct B: private A {};  
  
struct C : B {  
   void f() {  
      A *p1 = (A*) this;   // C2247  
      // try the following line instead  
      // ::A *p2 = (::A*) this;  
   }  
};  
```