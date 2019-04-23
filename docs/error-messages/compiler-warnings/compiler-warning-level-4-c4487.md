---
title: 編譯器警告 (層級 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 231482547856fc07d43ecfb859b31c2ece49fc5e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778000"
---
# <a name="compiler-warning-level-4-c4487"></a>編譯器警告 (層級 4) C4487

'derived_class_function': 符合繼承的非虛擬方法 'base_class_function'，但未在 'new' 明確地標記

在衍生類別中的函式具有相同的簽章，做為非虛擬基底類別。 C4487 會提醒您在衍生的類別函式不覆寫基底類別函式。 明確標記為衍生的類別函式`new`若要解決這個警告。

如需詳細資訊，請參閱 <<c0> [ 新 (新 vtable 中的位置）](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4487。

```
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```