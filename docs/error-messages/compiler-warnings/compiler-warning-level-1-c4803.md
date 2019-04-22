---
title: 編譯器警告 (層級 1) C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: bb8f5fe9d55a44193325a2fcfe9ef7675a2b3b89
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779215"
---
# <a name="compiler-warning-level-1-c4803"></a>編譯器警告 (層級 1) C4803

'method': 產生的方法具有不同的儲存類別的事件 'event'

事件方法必須具有相同的儲存體類別，為事件宣告。 編譯器會調整事件的方法，使儲存體類別都相同。

如果您有一個類別，實作事件介面中的，可能會發生這個警告。 編譯器不會以隱含方式產生事件的引發方法，以在介面中。 當您在類別中實作該介面時，編譯器會以隱含方式產生引發方法及該方法不是虛擬的因此這項警告。 如需有關事件的詳細資訊，請參閱 <<c0> [ 事件](../../extensions/event-cpp-component-extensions.md)。

請參閱[警告](../../preprocessor/warning.md)pragma，如需有關如何關閉警告資訊。

## <a name="example"></a>範例

下列範例會產生 C4803。

```
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
