---
title: "using 宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "using 宣告"
  - "宣告命名空間，命名空間中的不合格名稱"
  - "宣告 [C++]，using 宣告"
  - "命名空間 [C++]，不合格的名稱"
  - "using 關鍵字 [C++]"
  - "宣告 [C++]，命名空間"
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# using 宣告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`using` 的宣告引入一個名稱至 `using` 宣告的區域。  
  
## 語法  
  
```  
  
      using [typename][::] nested-name-specifier unqualified-id  
using :: unqualified-id  
```  
  
## 備註  
 名稱會變成其他位置宣告的實體同義字。  它允許從特定命名空間使一個 *個別* 名稱被使用，卻不用 [明確描述](../misc/explicit-qualification.md)。  與 `using` 指示詞相反，它允許 *所有*在命名空間的名稱被使用而不用加以描述。  請參閱 [using 指示詞](../misc/using-directive-cpp.md)以得到更多資訊。  這個關鍵字也被 [輸入別名](../cpp/aliases-and-typedefs-cpp.md)使用。  
  
## 範例  
 using 的宣告的可用於類別定義。  
  
```cpp  
// using_declaration1.cpp  
#include <stdio.h>  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class D : B {  
public:  
   using B::f;  
   using B::g;  
   void f(int) {  
      printf_s("In D::f()\n");  
      f('c');  
   }  
  
   void g(int) {  
      printf_s("In D::g()\n");  
      g('c');  
   }  
};  
  
int main() {  
   D myD;  
   myD.f(1);  
   myD.g('a');  
}  
```  
  
  **在 D::f\(\)**  
**在 B::f\(\)**  
**在 B::g\(\)**   
## 範例  
 當用來宣告成員，using 的宣告中必須參考基底類別的成員。  
  
```cpp  
// using_declaration2.cpp  
#include <stdio.h>  
  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class C {  
public:  
   int g();  
};  
  
class D2 : public B {  
public:  
   using B::f;   // ok: B is a base of D2  
   // using C::g;   // error: C isn't a base of D2  
};  
  
int main() {  
   D2 MyD2;  
   MyD2.f('a');  
}  
```  
  
  **在 B::f\(\)**   
## 範例  
 成員被宣告成一個 using，則可以用詳盡的描述被參考。  `::` 前置詞則會參考全域命名空間。  
  
```cpp  
// using_declaration3.cpp  
#include <stdio.h>  
  
void f() {  
   printf_s("In f\n");  
}  
  
namespace A {  
   void g() {  
      printf_s("In A::g\n");  
   }  
}  
  
namespace X {  
   using ::f;   // global f  
   using A::g;   // A's g  
}  
  
void h() {  
   printf_s("In h\n");  
   X::f();   // calls ::f  
   X::g();   // calls A::g  
}  
  
int main() {  
   h();  
}  
```  
  
  **在 h 中**  
**在 f 中**  
**在 A::g 中**   
## 範例  
 當 using 宣告出現時，宣告建立的同義資料表參考只有在 using 的宣告定義是有效時創建。  定義加入至命名空間中，當 using 宣告不再是有效的同義資料表。  
  
 一個被 using 宣告所定義的名稱是它原本名稱的別名。  它不會影響型別、連接或原始宣告的其他屬性。  
  
```cpp  
// post_declaration_namespace_additions.cpp  
// compile with: /c  
namespace A {  
   void f(int) {}  
}  
  
using A::f;   // f is a synonym for A::f(int) only  
  
namespace A {  
   void f(char) {}  
}  
  
void f() {  
   f('a');   // refers to A::f(int), even though A::f(char) exists  
}  
  
void b() {  
   using A::f;   // refers to A::f(int) AND A::f(char)  
   f('a');   // calls A::f(char);  
}  
```  
  
## 範例  
 關於命名空間中的函式，如果一組區域宣告和單一名稱的 using 宣告被賦予在宣告區域，則它們必須參考相同的實體，否則他們必須全部參考函式。  
  
```cpp  
// functions_in_namespaces1.cpp  
// C2874 expected  
namespace B {  
    int i;  
    void f(int);  
    void f(double);  
}  
  
void g() {  
    int i;  
    using B::i;   // error: i declared twice  
    void f(char);  
    using B::f;   // ok: each f is a function  
}  
```  
  
 在上面的範例中， `using B::i` 陳述式在 `g()` 函式造成第二個 `int i` 的宣告。  因為 `B::f` 引入的函式名稱具有不同的參數型別， `using B::f` 陳述式和`f(char)`函式不衝突。  
  
## 範例  
 當一個函式以 using 宣告引進時，區域函式宣告不能有相同的名稱和型別。  例如：  
  
```cpp  
// functions_in_namespaces2.cpp  
// C2668 expected  
namespace B {  
    void f(int);  
    void f(double);  
}  
  
namespace C {  
    void f(int);  
    void f(double);  
    void f(char);  
}  
  
void h() {  
    using B::f;          // introduces B::f(int) and B::f(double)  
    using C::f;          // C::f(int), C::f(double), and C::f(char)  
    f('h');              // calls C::f(char)  
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?  
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)  
}  
```  
  
## 範例  
 關於繼承，當 using 宣告引進一個基底類別名稱至衍生類別範圍時，在衍生類別的成員函式會覆寫在基底類別成員函式中相同名稱和引數的函式。  
  
```cpp  
// using_declaration_inheritance1.cpp  
#include <stdio.h>  
struct B {  
   virtual void f(int) {  
      printf_s("In B::f(int)\n");  
   }  
  
   virtual void f(char) {  
      printf_s("In B::f(char)\n");  
   }  
  
   void g(int) {  
      printf_s("In B::g\n");  
   }  
  
   void h(int);  
};  
  
struct D : B {  
   using B::f;  
   void f(int) {   // ok: D::f(int) overrides B::f(int)  
      printf_s("In D::f(int)\n");  
   }  
  
   using B::g;  
   void g(char) {   // ok: there is no B::g(char)  
      printf_s("In D::g(char)\n");  
   }  
  
   using B::h;  
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)  
};  
  
void f(D* pd) {  
   pd->f(1);   // calls D::f(int)  
   pd->f('a');   // calls B::f(char)  
   pd->g(1);   // calls B::g(int)  
   pd->g('a');   // calls D::g(char)  
}  
  
int main() {  
   D * myd = new D();  
   f(myd);  
}  
```  
  
  **在 D::f \(int\) 中**  
**在 B::f \(char\) 中**  
**在 B::g\(\) 中**  
**在 D::g \(char\) 中**   
## 範例  
 所有在 using 宣告中被使用的參數均需是可使用的。  特別是，如果衍生類別使用 using 宣告存取基底類別的成員，成員名稱必須是可存取的。  如果名稱是多載的成員函式，則所有功能名稱必須是可存取的。  
  
 如需成員的存取範圍的詳細資訊，請參閱 [Member\-Access Control](../cpp/member-access-control-cpp.md)。  
  
```cpp  
// using_declaration_inheritance2.cpp  
// C2876 expected  
class A {  
private:  
   void f(char);  
public:  
   void f(int);  
protected:  
   void g();  
};  
  
class B : public A {  
   using A::f;   // C2876: A::f(char) is inaccessible  
public:  
   using A::g;   // B::g is a public synonym for A::g  
};  
```  
  
## 請參閱  
 [命名空間](../cpp/namespaces-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)