---
title: 編譯器錯誤 C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f6b0539e7c794852f7e4b28d60f4b402a020bed1
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743200"
---
# <a name="compiler-error-c2668"></a>編譯器錯誤 C2668

' function '：對多載函式的呼叫不明確

無法解析指定的多載函式呼叫。 您可能會想要明確地轉換一或多個實際參數。

您也可以透過範本使用來取得此錯誤。 如果在相同的類別中，您擁有具有相同簽章的一般成員函式和樣板化成員函式，則必須先取得樣板化的成員函式。 這是目前的 Visual C++ 執行的限制。

## <a name="examples"></a>範例

下列範例會產生 C2668：

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

解決這個錯誤的另一個方法是 [使用](../../cpp/using-declaration.md)宣告：

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

這項錯誤也可能是因為編譯器一致性工作所做的結果，而這項工作是針對 Visual Studio .NET 2003：常數0的 cast 轉換不明確的轉換所產生。

使用常數0的轉換轉換是不明確的，因為 int 需要將轉換為 long 和 void *。 若要解決這個錯誤，請將0轉換成它所用的函式參數的確切型別，如此一來，就不需要進行任何轉換 (此程式碼在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++) 中是有效的。

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

發生此錯誤的原因可能是 CRT 現在具有所有數學函式的 float 和雙重形式。

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

發生此錯誤的原因可能是 pow (int，int) 已從 CRT 中的 math 移除。

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

這段程式碼會在 Visual Studio 2015 中成功，但在 Visual Studio 2017 和更新版本中，C2668 會失敗。 在 Visual Studio 2015 中，編譯器會使用與一般 copy-initialization 相同的方式錯誤地處理 copy-list-initialization；它只會考慮轉換建構函式來進行多載解析。

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```
