---
title: 如何： 宣告覆寫規範 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1089f2d9326cf268bd76ad59242e2664060b78fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386518"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI)

[密封](../windows/sealed-cpp-component-extensions.md)，[抽象](../windows/abstract-cpp-component-extensions.md)，和[覆寫](../windows/override-cpp-component-extensions.md)可用在不使用的編譯中 **/ZW**或是[/clr](../build/reference/clr-common-language-runtime-compilation.md)。

> [!NOTE]
>  ISO C + + 11 標準語言有[覆寫](../cpp/override-specifier.md)識別項並[最終](../cpp/final-specifier.md)識別項，以及同時支援 Visual Studio 中使用`final`而不是`sealed`旨在的程式碼中為僅限原生編譯。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示`sealed`是在原生編譯中有效。

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

下一個範例顯示`override`是在原生編譯中有效。

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

這個範例將示範`abstract`是在原生編譯中有效。

### <a name="code"></a>程式碼

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>另請參閱

[覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)