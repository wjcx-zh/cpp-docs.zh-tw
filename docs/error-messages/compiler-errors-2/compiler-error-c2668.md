---
title: 編譯器錯誤 C2668 |Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3b318c663bb036629086d0bca9a67641e3c4c4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093749"
---
# <a name="compiler-error-c2668"></a>編譯器錯誤 C2668

'function': 模稜兩可的呼叫多載函式

無法解析指定的多載函式呼叫。 若要明確轉換一或多個實際的參數。

您也可以透過範本使用，取得此錯誤。 如果在相同類別中，您會有一般成員函式，並使用相同的簽章的樣板化的成員函式，必須先使用樣板化的其中一個。 這是目前的 Visual c + + 實作的限制。

在函式樣板的部分排序，請參閱知識庫文件 Q240869 如需詳細資訊。

如果您正在建置 ATL 專案包含 COM 物件支援`ISupportErrorInfo`，請參閱知識庫文章 Q243298。

## <a name="example"></a>範例

下列範例會產生 C2668:

```
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

若要解決此錯誤的另一個方法是使用[using 宣告](../../cpp/using-declaration.md):

```
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

也可因為針對 Visual Studio.NET 2003年所進行的編譯器一致性處理而產生這個錯誤： 在常數 0 轉換模稜兩可的轉換。

在使用常數 0 轉換的轉換模稜兩可，因為長時間且以 void *，int 需要轉換兩個。 若要解決這個錯誤，轉型成確切的型別，正如，因此無法進行轉換需要進行 （此程式碼是有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中的 Visual c + +） 的函式參數的 0。

```
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

因為 CRT，現在有的浮點數和雙精度浮點格式的所有數學函式，會發生此錯誤。

```
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

此錯誤可能是因為 pow （int，int） 已從 CRT 中的 math.h> 中移除。

```
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>範例

此程式碼成功地在 Visual Studio 2015，但無法在 Visual Studio 2017 和更新版本為 C2668。 在 Visual Studio 2015 中，編譯器會使用與一般 copy-initialization 相同的方式錯誤地處理 copy-list-initialization；它只會考慮轉換建構函式來進行多載解析。

```
C++
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