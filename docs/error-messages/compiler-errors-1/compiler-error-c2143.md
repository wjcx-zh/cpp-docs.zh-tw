---
title: 編譯器錯誤 C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: 310083a650f842c6c0f0912efe1ceddb66c4fd6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214746"
---
# <a name="compiler-error-c2143"></a>編譯器錯誤 C2143

語法錯誤： ' token2 ' 之前遺漏 ' token1 '

編譯器必須有特定的 token （也就是空白字元以外的語言元素），並改為找到另一個 token。

請檢查[c + + 語言參考](../../cpp/cpp-language-reference.md)，判斷程式碼的語法不正確。 因為編譯器可能會在遇到造成問題的那一行之後報告此錯誤，所以請檢查錯誤前面的幾行程式碼。

C2143 可能會在不同的情況下發生。

當可以限定名稱的運算子（ `::` 、 `->` 和 `.` ）後面必須接著關鍵字時，就會發生 **`template`** 此錯誤，如下列範例所示：

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

根據預設，C++ 假設 `Ty::PutFuncType` 不是範本；因此下列 `<` 會解譯成小於符號。  您必須明確地告知編譯器 `PutFuncType` 為範本，以便它可以正確地剖析角括號。 若要更正這個錯誤，請 **`template`** 在相依類型的名稱上使用關鍵字，如下所示：

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

使用 **/clr**時可能會發生 C2143，且指示詞 **`using`** 有語法錯誤：

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

當您嘗試使用 CLR 語法編譯原始程式碼檔，而未同時使用 **/clr**時，也可能會發生此錯誤：

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

緊接在語句後面的第一個非空白字元 **`if`** 必須是左括弧。 編譯器無法轉譯任何其他專案：

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

偵測到錯誤的那一行或之前其中一行遺漏了右大括號、括號或分號時，C2143 就會發生：

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

或是在類別宣告中有無效的標記時：

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

或當標記未附加至陳述式。 如果您必須自行放置標籤（例如，在複合陳述式的結尾），請將它附加至 null 語句：

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

對 c + + 標準程式庫中的類型進行不合格的呼叫時，可能會發生此錯誤：

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

或有遺失的 **`typename`** 關鍵字：

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

或者如果您嘗試定義明確具現化：

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

在 C 程式中，變數必須在函式的開頭宣告，而且不能在函式執行非宣告指令之後宣告。

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
