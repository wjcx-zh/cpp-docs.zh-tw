---
title: "編譯器警告 (層級 2) C4250 | Microsoft Docs"
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
  - "C4250"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4250"
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4250
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class1' : 經由支配繼承 'class2::member'  
  
 有兩個或更多的成員擁有相同名稱。  `class2` 中的成員會被繼承，是因為它是其他包含此成員的類別之基底類別。  
  
 若要隱藏 C4250，請使用 [warning](../../preprocessor/warning.md) Pragma。  
  
 由於虛擬基底類別是在多個衍生類別之間共用，衍生類別中的名稱會支配基底類別中的名稱。  例如，在下列類別階層架構下，有兩個 func 定義是從菱形之內繼承的：透過弱式類別的 vbc::func\(\) 執行個體，以及透過支配類別的 dominant::func\(\)。  透過菱形類別物件進行資格不符的 func\(\) 呼叫時，一律都是呼叫 dominate::func\(\) 執行個體。如果弱式類別要引入 func\(\) 執行個體，兩種定義都不能支配，呼叫會以旗標標示為模稜兩可。  
  
```  
// C4250.cpp  
// compile with: /c /W2  
#include <stdio.h>  
struct vbc {  
   virtual void func() { printf("vbc::func\n"); }  
};  
  
struct weak : public virtual vbc {};  
  
struct dominant : public virtual vbc {  
   void func() { printf("dominant::func\n"); }  
};  
  
struct diamond : public weak, public dominant {};  
  
int main() {  
   diamond d;  
   d.func();   // C4250  
}  
```  
  
## 範例  
 下列範例會產生 C4250。  
  
```  
// C4250_b.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
class A {  
public:  
   virtual operator int () {  
      return 2;  
   }  
};  
  
class B : virtual public A {  
public:  
   virtual operator int () {  
      return 3;  
   }  
};  
  
class C : virtual public A {};  
  
class E : public B, public C {};   // C4250  
  
int main() {  
   E eObject;  
   cout << eObject.operator int() << endl;  
}  
```  
  
## 範例  
 這個範例示範的是更複雜的情況。  下列範例會產生 C4250。  
  
```  
// C4250_c.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
  
class V {  
public:  
   virtual int f() {  
      return 1024;  
   }  
};  
  
class B : virtual public V {  
public:  
   int b() {  
      return f(); // B::b() calls V::f()  
   }  
};  
  
class M : virtual public V {  
public:  
   int f() {  
      return 7;  
   }  
};  
  
// because of dominance, f() is M::f() inside D,  
// changing the meaning of B::b's f() call inside a D  
class D : public B, public M {};   // C4250  
  
int main() {  
   D d;  
   cout << "value is: " << d.b();   // invokes M::f()  
}  
```