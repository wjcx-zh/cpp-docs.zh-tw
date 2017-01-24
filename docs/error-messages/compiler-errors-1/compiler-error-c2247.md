---
title: "編譯器錯誤 C2247 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2247"
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' 無法存取，因為 'class' 類別使用 'specifier' 來繼承 'class' 類別  
  
 `identifier` 繼承自使用私用或受保護存取宣告的類別。  
  
 下列範例會產生 C2247：  
  
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
  
 對 Visual Studio .NET 2003 的編譯器完成符合標準處理後也會出現這個錯誤：受保護成員的存取控制 \(Access Control\)。  您只能透過類別 \(B\) 的成員函式存取受保護成員 \(n\) \(類別 \(B\) 是繼承自類別 \(A\)，而此受保護成員 \(n\) 是類別 \(A\) 中的成員\)。  
  
 若要使程式碼在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，請將成員宣告為型別的 friend 函式。  也可以使用公用繼承方式。  
  
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
  
 對 Visual Studio .NET 2003 的編譯器完成一致性處理後也可能會出現 C2247：現在已無法存取私用基底類別。  因為類別 \(A\) 是型別 \(B\) 的私用基底類別，所以，以型別 \(B\) 為基底類別的型別 \(C\) 無法存取類別 \(A\)。  
  
 若要使程式碼在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，請使用範圍運算子 \(Scope Operator\)。  
  
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