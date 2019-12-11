---
title: 編譯器警告 (層級 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: b83b3b33727db300367156e10f902aaa6ff4bfdb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990780"
---
# <a name="compiler-warning-level-4-c4487"></a>編譯器警告 (層級 4) C4487

' derived_class_function '：符合繼承的非虛擬方法 ' base_class_function '，但未明確標記為 ' new '

衍生類別中的函式具有與非虛擬基類函數相同的簽章。 C4487 會提醒您，衍生類別函式不會覆寫基類函數。 將衍生類別函式明確標示為 `new`，以解決這個警告。

如需詳細資訊，請參閱[new （vtable 中的新位置）](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4487。

```cpp
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
