---
title: 區域宣告名稱的名稱解析 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6347f3b0b71dc35544f22101479de23bb4efd686
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="name-resolution-for-locally-declared-names"></a>區域宣告名稱的名稱解析

樣本的名稱本身在參考時可以具有或不具有樣板引數。 在類別樣板的範圍內，名稱本身會參考樣板。 在樣板特製化或部分特製化的範圍內，個別本身可參考特製化或部分特製化。 使用適當的樣板引數可以參考樣板的其他特製化或部分特製化。  
  
## <a name="example"></a>範例

 下列程式碼顯示在特製化或部分特製化的範圍內，類別樣板的名稱 A 的不同解譯。  
  
```cpp
// template_name_resolution3.cpp  
// compile with: /c  
template <class T> class A {  
   A* a1;   // A refers to A<T>  
   A<int>* a2;  // A<int> refers to a specialization of A.  
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.  
};  
  
template <class T> class A<T*> {  
   A* a4; // A refers to A<T*>.  
};  
  
template<> class A<int> {  
   A* a5; // A refers to A<int>.  
};  
```  
  
## <a name="example"></a>範例

 在樣板參數和其他物件之間發生名稱衝突的情況下，樣板參數可以或無法隱藏。 下列規則可協助判斷優先順序。  
  
 樣板參數的範圍是從第一次出現的位置，一直到類別或函式樣板的結尾。 如果名稱再次出現在樣板引數清單或基底類別清單中，其會參考相同的類型。 在 Standard C++ 中，在相同範圍內不可以宣告與樣板參數相同的名稱。 Microsoft 擴充功能允許在樣板的範圍內重新定義樣板參數。 下列範例顯示在類別樣板的基底規格中使用樣板參數。  
  
```cpp
// template_name_resolution4.cpp  
// compile with: /EHsc  
template <class T>  
class Base1 {};  
  
template <class T>  
class Derived1 : Base1<T> {};  
  
int main() {  
   // Derived1<int> d;  
}  
```  
  
## <a name="example"></a>範例

 在類別樣板的外部定義樣板的成員函式時，可以使用不同的樣板參數名稱。 如果樣板成員函式定義使用與宣告不同的樣板參數名稱，而且在定義中使用的名稱與宣告的其他成員發生衝突，則會優先使用樣板宣告中的成員。  
  
```cpp
// template_name_resolution5.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T> class C {  
public:  
   struct Z {  
      Z() { cout << "Z::Z()" << endl; }  
   };  
   void f();  
};  
  
template <class Z>  
void C<Z>::f() {  
   // Z refers to the struct Z, not to the template arg;  
   // Therefore, the constructor for struct Z will be called.  
   Z z;  
}  
  
int main() {  
   C<int> c;  
   c.f();  
}  
```  
  
```Output  
Z::Z()  
```  
  
## <a name="example"></a>範例

 在宣告樣板的命名空間外部定義樣板函式或成員函式時，樣板引數會優先於命名空間的其他成員名稱。  
  
```cpp
// template_name_resolution6.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
namespace NS {  
   void g() { cout << "NS::g" << endl; }  
  
   template <class T> struct C {  
      void f();  
      void g() { cout << "C<T>::g" << endl; }  
   };  
};  
  
template <class T>  
void NS::C<T>::f() {  
   g(); // C<T>::g, not NS::g  
};  
  
int main() {  
   NS::C<int> c;  
   c.f();  
}  
```  
  
```Output  
C<T>::g  
```  
  
## <a name="example"></a>範例

 在樣板類別宣告外部的定義中，如果樣板類別具有未相依於樣板引數的基底類別，而且，如果基底類別或其中一個成員的名稱與樣板引數相同，則基底類別或成員名稱會隱藏樣板引數。  
  
```cpp
// template_name_resolution7.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct B {  
   int i;  
   void print() { cout << "Base" << endl; }  
};  
  
template <class T, int i> struct C : public B {  
   void f();  
};  
  
template <class B, int i>  
void C<B, i>::f() {  
   B b;   // Base class b, not template argument.  
   b.print();  
   i = 1; // Set base class's i to 1.  
}  
  
int main() {  
   C<int, 1> c;  
   c.f();  
   cout << c.i << endl;  
}  
```  
  
```Output  
Base  
1  
```  
  
## <a name="see-also"></a>另請參閱

 [名稱解析](../cpp/templates-and-name-resolution.md)
