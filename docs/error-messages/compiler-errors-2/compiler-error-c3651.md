---
title: 編譯器錯誤 C3651
ms.date: 11/04/2016
f1_keywords:
- C3651
helpviewer_keywords:
- C3651
ms.assetid: a03e692e-c219-4654-9827-8415cfa5a22d
ms.openlocfilehash: 9468b1e9193bfa52ed133f6fdfa398e02e40c4ef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756314"
---
# <a name="compiler-error-c3651"></a>編譯器錯誤 C3651

' member '：不能當做明確覆寫使用，必須是基類的成員

已指定明確的覆寫，但正在覆寫的函式是在不是基底類型的類型中。

如需詳細資訊，請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

下列範例會產生 C3651：

```cpp
// C3651.cpp
// compile with: /clr /c
ref class C {
public:
   virtual void func2();
};

ref class Other {
public:
   virtual void func();
};

ref class D : public C {
public:
   virtual void func() new sealed = Other::func;   // C3651
   virtual void func2() new sealed = C::func2;   // OK
};
```
