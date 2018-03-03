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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcb7b24bb39ba204653d2a99d6bc1d3e5d8142b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2259"></a>編譯器錯誤 C2259
'class': 無法具現化抽象類別  
  
 程式碼會宣告一個抽象類別或結構的執行個體。  
  
 您無法執行個體化的類別或結構具有一個或多個純虛擬函式。 若要具現化衍生類別的物件，衍生的類別必須覆寫每個純虛擬函式。  
  
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
  
 每當您衍生介面，並且使用非公用存取權限在衍生類別中實作介面方法，您可能會收到 C2259。  這是因為編譯器會預期有公用存取的衍生類別中實作的介面方法。 當您實作的介面，以更具限制性的存取權限的成員函式時，編譯器不會考慮它們反而能夠讓衍生的類別的抽象類別的介面中定義的介面方法的實作。  
  
 有兩個可能的因應措施的問題：  
  
-   請實作方法的公用存取權限。  
  
-   在衍生類別中實作的介面方法中使用範圍解析運算子來限定實作的方法名稱的介面名稱中。  
  
 C2259 在 Visual c + + 2005 中已完成之一致性工作，也會發生**/zc: wchar_t**現在預設為開啟。 在此情況下，C2599 可以解析使用由編譯**/Zc:wchar_t-**，若要取得的行為，從較舊的版本，或者最好是藉由更新您的型別，因此它們彼此相容。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
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
