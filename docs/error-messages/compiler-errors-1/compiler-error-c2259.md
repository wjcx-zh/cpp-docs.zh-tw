---
title: "編譯器錯誤 C2259 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2259
dev_langs:
- C++
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 0837d8f5e48ccf0de0ba8630801667da2ddb6bfa
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2259"></a>編譯器錯誤 C2259
'class': 無法具現化抽象類別  
  
 程式碼會宣告一個抽象類別或結構的執行個體。  
  
 您無法執行個體化的類別或結構與一或多個純虛擬函式。 若要具現化衍生類別的物件，衍生的類別必須覆寫每個純虛擬函式。  
  
 如需詳細資訊，請參閱[隱含抽象類別](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)。  
  
 下列範例會產生 C2259:  
  
```  
// C2259.cpp  
// compile with: /c  
class V {  
public:  
   void virtual func() = 0;  
};  
class A : public V {};  
class B : public V {  
public:  
   void func();  
};  
V v;  // C2259, V is an abstract class  
A a;  // C2259, A inherits func() as pure virtual  
B b;  // OK, B defines func()  
```  
  
 當您從介面衍生並實作介面方法衍生類別中具有非公用的存取權限時，您可能會收到 C2259。  這是因為編譯器會預期有公用存取的衍生類別中實作的介面方法。 當您實作的介面，以更具限制性的存取權限的成員函式時，編譯器不會考慮它們都是介面，因此可將衍生的類別的抽象類別中定義的介面方法的實作。  
  
 有兩個可能的因應措施的問題︰  
  
-   將存取權限已實作的方法公開。  
  
-   使用衍生類別中實作的介面方法的範圍解析運算子限定實作的方法名稱的介面名稱。  
  
 C2259 也會導致在 Visual c + + 2005 中，已完成一致性處理**/zc: wchar_t**現在預設為開啟。 在此情況下，C2599 可以解析使用由編譯**/Zc:wchar_t-**，以取得此行為，從先前的版本，或最好是藉由更新您的型別，因此它們彼此相容。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
 下列範例會產生 C2259:  
  
```  
// C2259b.cpp  
// compile with: /c  
#include <windows.h>   
  
class MyClass {  
public:  
   // WCHAR now typedef'ed to wchar_t  
   virtual void func(WCHAR*) = 0;  
};  
  
class MyClass2 : MyClass {  
public:  
   void func(unsigned short*);  
};  
  
MyClass2 x;   // C2259  
  
// OK  
class MyClass3 {  
public:  
   virtual void func(WCHAR*) = 0;  
   virtual void func2(wchar_t*) = 0;  
   virtual void func3(unsigned short*) = 0;  
};  
  
class MyClass4 : MyClass3 {  
public:  
   void func(WCHAR*) {}  
   void func2(wchar_t*) {}  
   void func3(unsigned short*) {}  
};  
  
MyClass4 y;  
```  
  
 下列範例會產生 C2259:  
  
```  
// C2259c.cpp  
// compile with: /clr  
interface class MyInterface {  
   void MyMethod();  
};  
  
ref class MyDerivedClass: public MyInterface {  
private:  
   // Uncomment the following line to resolve.  
   // public:  
   void MyMethod(){}  
   // or the following line  
   // void MyInterface::MyMethod() {};  
};  
  
int main() {  
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259  
}  
```  

