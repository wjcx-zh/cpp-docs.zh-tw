---
title: 編譯器錯誤 C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: f91eb428fcb49c81187788730128545916955790
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127656"
---
# <a name="compiler-error-c2059"></a>編譯器錯誤 C2059

語法錯誤： ' token '

Token 造成語法錯誤。

下列範例會針對宣告 `j`的程式程式碼產生錯誤訊息。

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

若要判斷錯誤的原因，請同時檢查錯誤訊息中所列的程式程式碼，以及其上方的行。 如果檢查程式程式碼不會產生問題的相關線索，請嘗試將錯誤訊息中所列的程式程式碼批註化，可能會有幾行以上。

如果錯誤訊息出現在緊接在 `typedef` 變數後面的符號上，請確定已在原始程式碼中定義變數。

當預處理器符號名稱重新用為識別碼時，會引發 C2059。 在下列範例中，編譯器會將 `DIGITS.ONE` 視為數位1，這不是有效的列舉元素名稱：

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

如果符號評估為沒有任何值，您可能會收到 C2059，因為使用 **/d**_符號_ **=** 來進行編譯時，會發生此問題。

```cpp
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

當您編譯的應用程式在函式的預設引數中指定結構時，可能會發生 C2059 的另一種情況。 引數的預設值必須是運算式。 初始化運算式清單（例如，用來初始化結構的它）不是運算式。  若要解決這個問題，請定義要執行必要初始化的處理函式。

下列範例會產生 C2059：

```cpp
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

如果轉換格式不正確，可能會發生 C2059。

下列範例會產生 C2059：

```cpp
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

如果您嘗試建立包含句號的命名空間名稱，也可能會發生 C2059。

下列範例會產生 C2059：

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

當可以限定名稱的運算子（`::`、`->`和 `.`）後面必須接著關鍵字 `template`，就會發生 C2059，如下列範例所示：

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
