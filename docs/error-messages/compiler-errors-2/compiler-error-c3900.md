---
title: 編譯器錯誤 C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 35df94ccfcd7942f9057cb37ceee349c09b80607
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777411"
---
# <a name="compiler-error-c3900"></a>編譯器錯誤 C3900

'member': 不允許在目前範圍中

屬性區塊可以包含函式宣告和只有內嵌函式定義。 函式以外的任何成員不可以在屬性區塊中。 不允許任何 typedef、 運算子或 friend 函式。 如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md)。

存取方法和函式只能包含事件定義。

下列範例會產生 C3900:

```
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

下列範例會產生 C3900:

```
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