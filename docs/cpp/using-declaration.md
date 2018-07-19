---
title: 使用宣告 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- using declaration
- declaring namespaces, unqualified names in namespaces
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
- declarations [C++], namespaces
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c40a69e9c8d584d91a1b6401ec0da57368641975
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941521"
---
# <a name="using-declaration"></a>using 宣告
Using 宣告引入的名稱，在其中的宣告式區域至使用宣告會出現。  
  
## <a name="syntax"></a>語法  
  
```  
using [typename] nested-name-specifier unqualified-id ;  
using declarator-list ;  
```  
  
### <a name="parameters"></a>參數
  
*巢狀名稱規範*  
    結束範圍解析運算子的命名空間、 類別或列舉型別名稱和範圍解析運算子 （:）、 序列。 單一的範圍解析運算子可用來從全域命名空間引入名稱使用。 關鍵字**typename**是選擇性的可用來解析相依時引入從基底類別的類別樣板的名稱。  
  
*非限定識別碼*  
    不合格的識別碼的運算式，可能是識別項、 多載的運算子名稱、 使用者定義常值運算子或轉換函式名稱、 類別解構函式名稱或範本的名稱和引數清單。  
  
*宣告子清單*  
    以逗號分隔清單的 [**typename**]*巢狀名稱規範**非限定識別碼*宣告子，後面接選擇省略符號。
    
## <a name="remarks"></a>備註  
Using 宣告導入了實體的同義字的非限定的名稱宣告其他位置。 它可讓特定的命名空間，而不用明確限定性條件，在出現的宣告區域中的單一名稱。 這是相對於[using 指示詞](../cpp/namespaces-cpp.md#using_directives)，可讓*所有*無限制使用的命名空間中的名稱。 **使用**關鍵字也可用於[輸入別名](../cpp/aliases-and-typedefs-cpp.md)。  
  
## <a name="example"></a>範例  
 A 可以使用 using 宣告類別定義中。  
  
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
   using B::f;    // B::f(char) is now visible as D::f(char)  
   using B::g;    // B::g(char) is now visible as D::g(char)  
   void f(int) {  
      printf_s("In D::f()\n");  
      f('c');     // Invokes B::f(char) instead of recursing  
   }  
  
   void g(int) {  
      printf_s("In D::g()\n");  
      g('c');     // Invokes B::g(char) instead of recursing  
   }  
};  
  
int main() {  
   D myD;  
   myD.f(1);  
   myD.g('a');  
}  
```  
  
```Output  
In D::f()  
In B::f()  
In B::g()  
```  
  
## <a name="example"></a>範例  
當用來宣告的成員，使用宣告必須參考的基底類別成員。  
  
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
  
```Output  
In B::f()  
```  
  
## <a name="example"></a>範例  
使用 using 宣告的成員宣告可以參考使用明確限定性條件。 `::`前置詞是指全域命名空間。  
  
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
   using ::f;   // global f is also visible as X::f  
   using A::g;   // A's g is now visible as X::g 
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
  
```Output  
In h  
In f  
In A::g  
```  
  
## <a name="example"></a>範例  
使用時進行宣告，宣告所建立的同義字只是指在使用有效的定義宣告。 定義在使用之後新增到命名空間宣告不是有效的同義字。  
  
定義的名稱**使用**宣告為其原始名稱的別名。 它不會影響類型、 連結或原始宣告的其他屬性。  
  
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
  
## <a name="example"></a>範例  
對於在命名空間，如果一組本機宣告的函式並使用宣告來宣告的區域會提供一個名稱，它們必須全部參考相同的實體，或它們必須全部參考函式。  
  
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
  
 在上述範例`using B::i`陳述式會導致第二個`int i`宣告於`g()`函式。 `using B::f`陳述式沒有與衝突`f(char)`函式，因為所導入的函式名稱`B::f`有不同的參數類型。  
  
## <a name="example"></a>範例  
 區域函式宣告不能有和由 using 宣告引入的函式名稱和類型相同。 例如:   
  
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
  
## <a name="example"></a>範例  
 對於繼承中，使用時宣告引入名稱從基底類別衍生的類別範圍內，在衍生的類別覆寫虛擬成員函式中具有相同的名稱和引數類型的基底類別的成員函式。  
  
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
   pd->f(1);     // calls D::f(int)  
   pd->f('a');   // calls B::f(char)  
   pd->g(1);     // calls B::g(int)  
   pd->g('a');   // calls D::g(char)  
}  
  
int main() {  
   D * myd = new D();  
   f(myd);  
}  
```  
  
```Output  
In D::f(int)  
In B::f(char)  
In B::g  
In D::g(char)  
```  
  
## <a name="example"></a>範例  
所有的執行個體名稱中使用所述的宣告必須是可存取。 特別是，如果在衍生的類別可讓您使用 using 宣告，以存取基底類別的成員名稱的成員必須可存取。 如果名稱就是多載的成員函式，則所有函式必須是可存取。  
  
如需協助工具成員的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [命名空間](../cpp/namespaces-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)