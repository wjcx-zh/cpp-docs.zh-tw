---
title: 如何:宣告覆寫指定器(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 9f3f6855f257d0af250b9bbdd2c0360b308ce775
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374455"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI)

[密封](../extensions/sealed-cpp-component-extensions.md)、[抽象](../extensions/abstract-cpp-component-extensions.md)和[重寫](../extensions/override-cpp-component-extensions.md)在不使用 **/ZW**或[/clr](../build/reference/clr-common-language-runtime-compilation.md)的編譯中可用。

> [!NOTE]
> ISO C++11 標準語言具有[重寫](../cpp/override-specifier.md)標識符和[最終](../cpp/final-specifier.md)識別符,並且兩者都在`final`Visual Studio 使用中`sealed`支援,而不是在旨在編譯為本機代碼的代碼中。

## <a name="example"></a>範例

### <a name="description"></a>描述

下面的示例顯示在`sealed`本機編譯中有效。

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

下一個範例顯示`override`在本機編譯中有效。

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

此示例顯示在`abstract`本機編譯中有效。

### <a name="code"></a>程式碼

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>另請參閱

[覆寫指定名稱](../extensions/override-specifiers-cpp-component-extensions.md)
