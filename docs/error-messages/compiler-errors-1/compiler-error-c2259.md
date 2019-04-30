---
title: 編譯器錯誤 C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 0310f20854185a6f8a5ccb0ce7b087c4d7c5f29d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387067"
---
# <a name="compiler-error-c2259"></a>編譯器錯誤 C2259

'class': 無法具現化抽象類別

程式碼會宣告一個抽象類別或結構的執行個體。

您無法執行個體化的類別或結構，具有一或多個純虛擬函式。 若要具現化衍生類別的物件，衍生的類別必須覆寫每個純虛擬函式。

如需詳細資訊，請參閱 <<c0> [ 隱含抽象類別](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)。

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

當您衍生自介面，並實作介面方法衍生類別中具有非公用的存取權限時，您可能會收到 C2259。  這是因為編譯器會預期要具有公用存取的衍生類別中實作的介面方法。 當您實作更嚴格的存取權限的介面成員函式時，編譯器不會考慮要在介面中，依序讓抽象類別衍生的類別定義的介面方法的實作。

有兩個可能的因應措施的問題：

- 將存取權限設為公用之實作的方法。

- 使用衍生類別中實作的介面方法的範圍解析運算子，來實作的方法使用限定名稱的介面名稱。

C2259 也會導致一致性所進行工作，在視覺效果C++2005年 **/zc: wchar_t**現在預設為開啟。 在此情況下，C2599 可以解析由以進行編譯 **/zc: wchar_t-**，以取得此行為，從先前的版本，或最好是藉由更新您的型別，因此它們彼此相容。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

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
