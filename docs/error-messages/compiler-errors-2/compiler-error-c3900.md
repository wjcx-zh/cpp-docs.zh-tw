---
title: 編譯器錯誤 C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: f1289fb9a4d60f2c75b54fd573c83064f1517282
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749096"
---
# <a name="compiler-error-c3900"></a>編譯器錯誤 C3900

' member '：在目前的範圍中不允許

屬性區塊只能包含函式宣告和內嵌函式定義。 屬性區塊中不允許使用函式以外的成員。 不允許使用 typedef、運算子或 friend 函數。 如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md)。

事件定義只能包含存取方法和函數。

下列範例會產生 C3900：

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

下列範例會產生 C3900：

```cpp
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
