---
title: 編譯器錯誤 C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f59cb33bed15847ed1a7a2dbe99ea030babf3337
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177153"
---
# <a name="compiler-error-c2668"></a>編譯器錯誤 C2668

' function '：不明確地呼叫多載函式

無法解析指定的多載函式呼叫。 您可能想要明確轉換一或多個實際參數。

您也可以透過範本使用來取得這個錯誤。 如果在相同的類別中，您有一般成員函式和具有相同簽章的樣板化成員函式，則必須先產生樣板化函數。 這是目前的視覺效果C++執行限制。

## <a name="example"></a>範例

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

## <a name="example"></a>範例

解決這個錯誤的另一種方法是[使用 using](../../cpp/using-declaration.md)宣告：

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

## <a name="example"></a>範例

針對 Visual Studio .NET 2003 進行的編譯器一致性工作，也可能會產生此錯誤：常數0的轉換發生不明確的轉換。

使用常數0的轉換轉換是不明確的，因為 int 需要轉換成 long 和 void *。 若要解決這個錯誤，請將0轉型為所使用之函式參數的確切類型，因此不需要進行任何轉換（此程式碼將在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++）中生效。

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

## <a name="example"></a>範例

之所以會發生這個錯誤，是因為 CRT 現在具有所有數學函數的 float 和 double 形式。

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

## <a name="example"></a>範例

之所以會發生這個錯誤，是因為 pow （int，int）已從 CRT 中的 math 移除。

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>範例

此程式碼會在 Visual Studio 2015 中成功，但在 Visual Studio 2017 及更新版本中使用 C2668 失敗。 在 Visual Studio 2015 中，編譯器會使用與一般 copy-initialization 相同的方式錯誤地處理 copy-list-initialization；它只會考慮轉換建構函式來進行多載解析。

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
