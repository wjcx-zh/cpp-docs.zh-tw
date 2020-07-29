---
title: 如何：宣告覆寫規範（c + +/CLI）
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: c5ed413f403fb12f116633c0e39f9e7b32b2e9f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221324"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI)

[sealed](../extensions/sealed-cpp-component-extensions.md)、 [abstract](../extensions/abstract-cpp-component-extensions.md)和[override](../extensions/override-cpp-component-extensions.md)在不使用 **/ZW**或[/clr](../build/reference/clr-common-language-runtime-compilation.md)的編譯中提供。

> [!NOTE]
> ISO c + + 11 標準語言具有覆[寫](../cpp/override-specifier.md)識別碼和[最終](../cpp/final-specifier.md)識別碼，而且兩者都受到 Visual Studio 使用， `final` 而不是 **`sealed`** 在要編譯為僅限原生的程式碼中。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示 **`sealed`** 在原生編譯中有效。

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

## <a name="example"></a>範例

### <a name="description"></a>描述

下一個範例顯示 `override` 在原生編譯中有效。

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

## <a name="example"></a>範例

### <a name="description"></a>描述

這個範例顯示 **`abstract`** 在原生編譯中有效。

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
