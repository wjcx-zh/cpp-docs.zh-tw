---
title: 編譯器錯誤 C2059
ms.date: 11/04/2016
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 915121b28adbc97032d5949726dc6fd5d3ab5091
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632471"
---
# <a name="compiler-error-c2059"></a>編譯器錯誤 C2059

語法錯誤: 'token'

語彙基元會導致語法錯誤。

下列範例會產生錯誤訊息的一行，宣告`j`。

```
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

若要判斷錯誤的原因，請檢查不只會列在錯誤訊息的那一行，也上面的程式行。 如果檢查的行，就會產生不會知道此問題，請嘗試標記為註解的錯誤訊息中所列的一行，並可能有數行上面。

如果緊接在後面的符號上就會發生的錯誤訊息`typedef`變數，請確定變數定義在原始程式碼中。

如果符號為執行任何動作，因為可能會發生，您可能收到 C2059 時 **/D** `symbol` **=** 用來編譯。

```
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

C2059 可能會發生另一種情況是當您編譯指定結構預設引數的函式中的應用程式。 引數的預設值必須是運算式。 初始設定式清單 — 例如，一個用來初始化結構 — 不是運算式。  若要解決此問題，請定義的建構函式來執行必要的初始化。

下列範例會產生 C2059:

```
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

C2059 可能發生的格式不正確的轉換。

下列範例會產生 C2059:

```
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

如果您嘗試建立命名空間的名稱包含句點，也可能會發生 C2059。

下列範例會產生 C2059:

```
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

可以限定名稱的運算子時，可能會發生 C2059 (`::`， `->`，並`.`) 後面必須接著關鍵字`template`，在此範例中所示：

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};

```

根據預設，C++ 假設 `AY::Rebind` 不是範本；因此下列 `<` 會解譯成小於符號。  您必須明確地告知編譯器 `Rebind` 為範本，以便它可以正確地剖析角括號。 若要更正這個錯誤，請在相依類型名稱上使用 `template` 關鍵字，如下所示：

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};

```