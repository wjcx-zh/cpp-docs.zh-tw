---
title: 編譯器警告（層級1） C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: ebf7b3baec3519a142c7a1835aa15a980974bb48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052353"
---
# <a name="compiler-warning-level-1-c4803"></a>編譯器警告（層級1） C4803

' method '：引發方法與事件的 ' event ' 具有不同的儲存類別

事件方法必須與事件宣告具有相同的儲存類別。 編譯器會調整事件的方法，讓儲存類別相同。

如果您有從介面中執行事件的類別，就會發生此警告。 編譯器不會針對介面中的事件隱含產生引發方法。 當您在類別中執行該介面時，編譯器會隱含地產生 raise 方法，而該方法將不會是虛擬的，因此會出現警告。 如需事件的詳細資訊，請參閱[事件](../../extensions/event-cpp-component-extensions.md)。

如需如何關閉警告的相關資訊，請參閱[warning](../../preprocessor/warning.md) pragma。

## <a name="example"></a>範例

下列範例會產生 C4803。

```cpp
// C4803.cpp
// compile with: /clr /W1
using namespace System;

public delegate void Del();

ref struct E {
   Del ^ _pd1;
   event Del ^ E1 {
      void add (Del ^ pd1) {
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));
      }

      void remove(Del^ pd1) {
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));
      }

      virtual void raise() {   // C4803 warning (remove virtual)
         if (_pd1)
            _pd1();
      }
   }

   void func() {
      Console::WriteLine("In E::func()");
   }
};

int main() {
   E ^ ep = gcnew E;
   ep->E1 += gcnew Del(ep, &E::func);
   ep->E1();
   ep->E1 -= gcnew Del(ep, &E::func);
   ep->E1();
}
```
