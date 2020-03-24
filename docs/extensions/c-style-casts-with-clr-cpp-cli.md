---
title: 使用 -clr 進行 C-Style 轉換 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: 2b7e492c62047e3b38224637f842d8a7fcbae84f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172590"
---
# <a name="c-style-casts-with-clr-ccli"></a>使用 /clr 進行 C-Style 轉換 (C++/CLI)

以下主題僅適用於 Common Language Runtime。

搭配 CLR 類型使用時，編譯器會嘗試依照下方多個轉換的列出順序，將 C-Style 轉換對應至其中之一：

1. const_cast

2. safe_cast

3. safe_cast plus const_cast

4. static_cast

5. static_cast plus const_cast

如果上面列出的轉換都無效，而且如果運算式的型別和目標型別為 CLR 參考型別，C-Style 轉換會對應至執行階段檢查 (castclass MSIL 指令)。 否則，C-Style 轉換會被視為無效，且編譯器會發出錯誤。

## <a name="remarks"></a>備註

不建議使用 C-Style 轉換。 以 [/clr (Common Language Runtime 編譯)](../build/reference/clr-common-language-runtime-compilation.md) 進行編譯時，請使用 [safe_cast](safe-cast-cpp-component-extensions.md)。

以下範例示範對應至 **const_cast** 的 C-Style 轉換。

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

以下範例示範對應至 **safe_cast** 的 C-Style 轉換。

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

以下範例示範對應至 **safe_cast** plus **const_cast** 的 C-Style 轉換。

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

以下範例示範對應至 **static_cast** 的 C-Style 轉換。

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

以下範例示範對應至 **static_cast** plus **const_cast** 的 C-Style 轉換。

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

以下範例示範對應至執行階段檢查的 C-Style 轉換。

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

以下範例示範會導致編譯器發出錯誤的無效 C-Style 轉換。

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>需求

編譯器選項：`/clr`

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
