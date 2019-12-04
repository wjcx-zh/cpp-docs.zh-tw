---
title: 編譯器錯誤 C3655
ms.date: 11/04/2016
f1_keywords:
- C3655
helpviewer_keywords:
- C3655
ms.assetid: 724919ab-2915-4b61-8794-44648e162d62
ms.openlocfilehash: 61762612cf5b2153319435532dca100eb77c274d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756301"
---
# <a name="compiler-error-c3655"></a>編譯器錯誤 C3655

' function '：函式已明確覆寫

函數只能明確覆寫一次。 如需詳細資訊，請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

下列範例會產生 C3655：

```cpp
// C3655.cpp
// compile with: /clr /c
public ref struct B {
   virtual void f();
   virtual void g();
};

public ref struct D : B {
   virtual void f() new sealed = B::f;
   virtual void g() new sealed = B::f;   // C3655
   // try the following line instead
   // virtual void g() new sealed = B::g;
};
```
