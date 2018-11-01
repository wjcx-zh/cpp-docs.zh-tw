---
title: 編譯器錯誤 C3739
ms.date: 11/04/2016
f1_keywords:
- C3739
helpviewer_keywords:
- C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
ms.openlocfilehash: 34f035c089b183670e87a23eb62f995b2af23c9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567488"
---
# <a name="compiler-error-c3739"></a>編譯器錯誤 C3739

'class': event_receiver 的 'layout_dependent' 參數為 true 時才支援語法

您嘗試攔截整個介面的事件，但`layout_dependent`上[event_receiver](../../windows/event-receiver.md)屬性不是，則為 true，您必須一次連接單一的事件。

下列範例會產生 C3739:

```
// C3739.cpp
struct A
{
   __event void e();
};

// event_receiver is implied
// [ event_receiver(layout_dependent=false)]

// use the following line instead
// [event_receiver(com, layout_dependent=true), coclass ]
struct B
{
   void f();
   B(A* a)
   {
      __hook(A, a, &B::f);   // C3739
      // use the following line instead to hook a single event
      // __hook(&A::e, a, &B::f);
   }
};

int main()
{
}
```