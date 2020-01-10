---
title: 編譯器錯誤 C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 403d674eae696eb42a837aef9d6e97c4b5b8f6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758784"
---
# <a name="compiler-error-c2259"></a>編譯器錯誤 C2259

' class '：無法具現化抽象類別

程式碼會宣告抽象類別或結構的實例。

您無法具現化具有一或多個純虛擬函式的類別或結構。 若要具現化衍生類別的物件，衍生的類別必須覆寫每個純虛擬函式。

如需詳細資訊，請參閱[隱含抽象類別](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)。

下列範例會產生 C2259：

```cpp
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

每當您從介面衍生，並在衍生類別中使用 public 以外的存取權限來執行介面方法時，您可能會收到 C2259。  之所以會發生這種情況，是因為編譯器預期衍生類別中所實的介面方法具有公用存取權。 當您針對具有更嚴格存取權限的介面來執行成員函式時，編譯器不會將它們視為介面中定義的介面方法的實作為，而使衍生類別成為抽象類別。

此問題有兩種可能的因應措施：

- 將存取權限公開給已執行的方法。

- 將範圍解析運算子用於衍生類別中所實的介面方法，以使用介面的名稱來限定已執行的方法名稱。

C2259 也可能會因為 Visual Studio 2005 中所執行的一致性工作而發生， **/zc： wchar_t**現在預設為開啟。 在此情況下，您可以藉由使用 **/zc： wchar_t-** 來進行編譯，以從舊版取得行為，或最好是藉由更新您的類型，使其相容。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

下列範例會產生 C2259：

```cpp
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

下列範例會產生 C2259：

```cpp
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
