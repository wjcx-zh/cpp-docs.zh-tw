---
title: 編譯器錯誤 C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: 2882764e1c0a84634c500d920f327fbebc4b19a9
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447948"
---
# <a name="compiler-error-c2653"></a>編譯器錯誤 C2653

> '*識別碼*': 不是類別或命名空間的名稱

語言語法需要類別、 結構、 等位或在此命名空間名稱。

當您使用尚未宣告為類別、 結構、 等位或範圍運算子前面的命名空間的名稱時，會發生此錯誤。 若要修正此問題，請宣告名稱，或包含宣告的名稱，才能使用的標頭。

C2653 此外，也可以，如果您嘗試定義*複合的命名空間*，包含一或多個範圍巢狀命名空間名稱的命名空間。 中不允許複合的命名空間定義C++在 c++17 之前。 在 Visual Studio 2015 Update 3 開始，當您指定支援複合的命名空間[/std: c + + 最新](../../build/reference/std-specify-language-standard-version.md)編譯器選項。 從 Visual Studio 2017 15.5 版中，編譯器支援複合的命名空間定義時[/std: c + + 17](../../build/reference/std-specify-language-standard-version.md)指定選項。

## <a name="examples"></a>範例

此範例會產生 C2653，因為已使用範圍名稱，但未宣告。 編譯器預期類別、 結構、 等位或之前的範圍運算子（::）的命名空間名稱。

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

程式碼中就不會編譯為 C + + 17 或更新版本的標準，巢狀命名空間必須使用明確的命名空間宣告，每個巢狀層級：

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual Studio 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
