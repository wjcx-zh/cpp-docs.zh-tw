---
title: "類別樣板 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], operating on type
- class templates
- templates, class templates
ms.assetid: 633a53c8-24ee-4c23-8c88-e7c3cb0b7ac3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b14b45752559c80f4aafb60aa4ba23cb0d51b91
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2018
---
# <a name="class-templates"></a>類別樣板
本主題描述的特定 c + + 類別範本規則。  
  
## <a name="member-functions-of-class-templates"></a>類別樣板的成員函式  
 成員函式可以在類別樣板內部或外部定義。 如果是類別樣板外部定義，這些函式的定義方式就像函式樣板。  
  
```cpp  
// member_function_templates1.cpp  
template<class T, int i> class MyStack  
{  
    T*  pStack;  
    T StackBuffer[i];  
    static const int cItems = i * sizeof(T);  
public:   
    MyStack( void );  
    void push( const T item );  
    T& pop( void );  
};  
  
template< class T, int i > MyStack< T, i >::MyStack( void )  
{  
};  
  
template< class T, int i > void MyStack< T, i >::push( const T item )  
{  
};  
  
template< class T, int i > T& MyStack< T, i >::pop( void )  
{  
};  
  
int main()  
{  
}  
```  
  
 請注意，就像處理所有樣板類別成員函式一般，類別的建構函式成員函式定義會包含樣板引數清單兩次。  
  
 成員函式本身可以是函式樣板，用於指定其他參數，如下列範例所示。  
  
```cpp  
// member_templates.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u);  
};  
  
template<typename T> template <typename U>  
void X<T>::mf(const U &u)  
{  
}  
  
int main()  
{  
}  
  
```  
  
## <a name="nested-class-templates"></a>巢狀的類別樣板  
 樣板可以在類別或類別樣板內定義，在這種情況下，這些樣板稱為成員樣板。 本身是類別的成員樣板稱為巢狀類別樣板。 成員樣板函式的會討論[成員函式樣板](../cpp/member-function-templates.md)。  
  
 巢狀類別樣板會在外部類別的範圍內宣告為類別樣板。 這些樣板可以在封入類別的內部或外部定義。  
  
 下列程式碼將示範一般類別內的巢狀類別樣板。  
  
```cpp  
// nested_class_template1.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class X  
{  
  
   template <class T>  
   struct Y  
   {  
      T m_t;  
      Y(T t): m_t(t) { }     
   };  
  
   Y<int> yInt;  
   Y<char> yChar;  
  
public:  
   X(int i, char c) : yInt(i), yChar(c) { }  
   void print()  
   {  
      cout << yInt.m_t << " " << yChar.m_t << endl;  
   }  
};  
  
int main()  
{  
   X x(1, 'a');  
   x.print();  
}  
```  
  
```cpp  
// nested_class_template2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
class X  
{  
   template <class U> class Y  
   {  
      U* u;  
   public:  
      Y();  
      U& Value();  
      void print();  
      ~Y();  
   };  
  
   Y<int> y;  
public:  
   X(T t) { y.Value() = t; }  
   void print() { y.print(); }  
};  
  
template <class T>   
template <class U>  
X<T>::Y<U>::Y()  
{  
   cout << "X<T>::Y<U>::Y()" << endl;  
   u = new U();  
}  
  
template <class T>   
template <class U>  
U& X<T>::Y<U>::Value()  
{  
   return *u;  
}  
  
template <class T>   
template <class U>  
void X<T>::Y<U>::print()  
{  
   cout << this->Value() << endl;  
}  
  
template <class T>   
template <class U>  
X<T>::Y<U>::~Y()  
{  
   cout << "X<T>::Y<U>::~Y()" << endl;  
   delete u;  
}  
  
int main()  
{  
   X<int>* xi = new X<int>(10);  
   X<char>* xc = new X<char>('c');  
   xi->print();  
   xc->print();  
   delete xi;  
   delete xc;  
}  
  
//Output:   
X<T>::Y<U>::Y()  
X<T>::Y<U>::Y()  
10  
99  
X<T>::Y<U>::~Y()  
X<T>::Y<U>::~Y()
```  
  
 區域類別不可以有成員樣板。  
  
## <a name="template-friends"></a>樣板 friend  
 類別樣板可以有[朋友](friend-cpp.md)。 類別或類別樣板、函式或函式樣板可以是樣板類別的 friend。 friend 也可以是類別樣板或函式樣板的特製化，但不是部分特製化。  
  
 在下列範例中，friend 函式會定義為類別樣板中的函式樣板。 此程式碼會為樣板的每個執行個體產生一個 friend 函式版本。 如果您的 friend 函式取決於與類別相同的樣板參數，這個建構會很有用。  
  
```cpp  
// template_friend1.cpp  
// compile with: /EHsc  
  
#include <iostream>  
using namespace std;  
  
template <class T> class Array {  
   T* array;  
   int size;  
  
public:  
   Array(int sz): size(sz) {  
      array = new T[size];  
      memset(array, 0, size * sizeof(T));  
   }  
  
   Array(const Array& a) {  
      size = a.size;  
      array = new T[size];  
      memcpy_s(array, a.array, sizeof(T));  
   }  
  
   T& operator[](int i) {  
      return *(array + i);  
   }  
  
   int Length() { return size; }  
  
   void print() {  
      for (int i = 0; i < size; i++)        
         cout << *(array + i) << " ";  
  
      cout << endl;  
   }  
  
   template<class T>  
   friend Array<T>* combine(Array<T>& a1, Array<T>& a2);  
};  
  
template<class T>  
Array<T>* combine(Array<T>& a1, Array<T>& a2) {  
   Array<T>* a = new Array<T>(a1.size + a2.size);  
   for (int i = 0; i < a1.size; i++)  
      (*a)[i] = *(a1.array + i);  
  
   for (int i = 0; i < a2.size; i++)  
      (*a)[i + a1.size] = *(a2.array + i);  
  
   return a;  
}  
  
int main() {  
   Array<char> alpha1(26);  
   for (int i = 0 ; i < alpha1.Length() ; i++)  
      alpha1[i] = 'A' + i;  
  
   alpha1.print();  
  
   Array<char> alpha2(26);  
   for (int i = 0 ; i < alpha2.Length() ; i++)  
      alpha2[i] = 'a' + i;  
  
   alpha2.print();  
   Array<char>*alpha3 = combine(alpha1, alpha2);  
   alpha3->print();  
   delete alpha3;  
}  
//Output:   
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z   
a b c d e f g h i j k l m n o p q r s t u v w x y z   
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z a b c d e f g h i j k l m n o p q r s t u v w x y z   
```  
  
 下一個範例內含具有樣板特製化的 friend。 如果原始函式樣板為 friend，則函式樣板特製化會自動為 friend。  
  
 您也可以只將樣板的特製化版本宣告為 friend，如下列程式碼的 friend 宣告之前的註解所示。 如果要這麼做，您必須將 friend 樣板特製化的定義置於樣板類別之外。  
  
```cpp  
// template_friend2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
class Array;  
  
template <class T>  
void f(Array<T>& a);  
  
template <class T> class Array  
{  
    T* array;  
    int size;  
  
public:  
    Array(int sz): size(sz)  
    {  
        array = new T[size];  
        memset(array, 0, size * sizeof(T));  
    }  
    Array(const Array& a)  
    {  
        size = a.size;  
        array = new T[size];  
        memcpy_s(array, a.array, sizeof(T));  
    }  
    T& operator[](int i)  
    {  
        return *(array + i);  
    }  
    int Length()  
    {   
        return size;  
    }  
    void print()  
    {  
        for (int i = 0; i < size; i++)  
        {  
            cout << *(array + i) << " ";  
        }  
        cout << endl;  
    }  
    // If you replace the friend declaration with the int-specific  
    // version, only the int specialization will be a friend.  
    // The code in the generic f will fail  
    // with C2248: 'Array<T>::size' :  
    // cannot access private member declared in class 'Array<T>'.  
    //friend void f<int>(Array<int>& a);  
  
    friend void f<>(Array<T>& a);  
};  
  
// f function template, friend of Array<T>  
template <class T>  
void f(Array<T>& a)  
{  
    cout << a.size << " generic" << endl;  
}  
  
// Specialization of f for int arrays  
// will be a friend because the template f is a friend.  
template<> void f(Array<int>& a)  
{  
    cout << a.size << " int" << endl;  
}  
  
int main()  
{  
    Array<char> ac(10);  
    f(ac);  
  
    Array<int> a(10);  
    f(a);  
}  
//Output:  
10 generic  
10 int  
```  
  
 下一個範例會顯示在類別樣板中宣告的 friend 類別樣板。 類別樣板接著會做為 friend 類別的樣板引數。 friend 類別樣板必須定義在其宣告的類別樣板之外。 friend 樣板的任何特製化或部分特製化也是原始類別樣板的 friend。  
  
```cpp  
// template_friend3.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
class X  
{  
private:  
   T* data;  
   void InitData(int seed) { data = new T(seed); }  
public:  
   void print() { cout << *data << endl; }  
   template <class U> friend class Factory;  
};  
  
template <class U>  
class Factory  
{  
public:  
   U* GetNewObject(int seed)  
   {  
      U* pu = new U;  
      pu->InitData(seed);  
      return pu;  
   }  
};  
  
int main()  
{  
   Factory< X<int> > XintFactory;  
   X<int>* x1 = XintFactory.GetNewObject(65);  
   X<int>* x2 = XintFactory.GetNewObject(97);  
  
   Factory< X<char> > XcharFactory;  
   X<char>* x3 = XcharFactory.GetNewObject(65);  
   X<char>* x4 = XcharFactory.GetNewObject(97);  
   x1->print();  
   x2->print();  
   x3->print();  
   x4->print();  
}  
//Output:   
65  
97  
A  
a  
```  
  
## <a name="reuse-of-template-parameters"></a>重複使用的樣板參數  
 樣板參數可以重複使用的樣板參數清單中。 例如，下列程式碼是可行的：  
  
```cpp  
// template_specifications2.cpp  
  
class Y   
{  
};  
template<class T, T* pT> class X1   
{  
};  
template<class T1, class T2 = T1> class X2   
{  
};  
  
Y aY;  
  
X1<Y, &aY> x1;  
X2<int> x2;  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [範本](../cpp/templates-cpp.md)
