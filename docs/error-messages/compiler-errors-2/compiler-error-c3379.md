---
title: 編譯器錯誤 C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 9d99214f3ad7e7db1edc215d94c98e9cf9ec4ca2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742895"
---
# <a name="compiler-error-c3379"></a>編譯器錯誤 C3379

' class '：嵌套類別在其宣告中不能有元件存取規範

當套用至 managed 類型（例如類別或結構）時，[公用](../../cpp/public-cpp.md)和[私](../../cpp/private-cpp.md)用關鍵字會指出類別是否將透過元件中繼資料公開。 `public` 或 `private` 無法套用至嵌套類別，這將會繼承封入類別的元件存取權。

搭配[/clr](../../build/reference/clr-common-language-runtime-compilation.md)使用時，`ref` 和 `value` 關鍵字會指出類別是受控的（請參閱[類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)）。

下列範例會產生 C3379：

```cpp
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```
