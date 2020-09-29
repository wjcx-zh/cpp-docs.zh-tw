---
title: '如何：將覆寫規範宣告 (c + +/CLI) '
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 92bdc41cf9ebe2389f2d22dab211029899283266
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414590"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI)

[密封](../extensions/sealed-cpp-component-extensions.md)、 [抽象](../extensions/abstract-cpp-component-extensions.md)和覆 [寫](../extensions/override-cpp-component-extensions.md) 適用于未使用 **/ZW** 或 [/clr](../build/reference/clr-common-language-runtime-compilation.md)的編譯。

> [!NOTE]
> ISO c + + 11 標準語言有覆 [寫](../cpp/override-specifier.md) 識別碼和 [最終](../cpp/final-specifier.md) 識別碼，在 Visual Studio 用途中 `final` （而不是以 **`sealed`** 原生方式編譯的程式碼）支援這兩者。

## <a name="example-sealed-is-valid"></a>範例： sealed 有效

### <a name="description"></a>描述

下列範例顯示 **`sealed`** 在原生編譯中是有效的。

### <a name="code"></a>程式碼

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example-override-is-valid"></a>範例：覆寫有效

### <a name="description"></a>描述

下一個範例顯示 `override` 在原生編譯中是有效的。

### <a name="code"></a>程式碼

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example-abstract-is-valid"></a>範例： abstract 有效

### <a name="description"></a>描述

此範例顯示 **`abstract`** 在原生編譯中是有效的。

### <a name="code"></a>程式碼

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>另請參閱

[覆寫規範](../extensions/override-specifiers-cpp-component-extensions.md)
