---
title: 編譯器錯誤 C3739
ms.date: 11/04/2016
f1_keywords:
- C3739
helpviewer_keywords:
- C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
ms.openlocfilehash: 7235d86ed00663b81aaddb87fdeae957c0f73053
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500419"
---
# <a name="compiler-error-c3739"></a>編譯器錯誤 C3739

' class '：只有當 event_receiver 的 ' layout_dependent ' 參數為 true 時，才支援語法

您嘗試連結事件的整個介面，但 `layout_dependent` [event_receiver](../../windows/attributes/event-receiver.md) 屬性不是 true; 您必須一次攔截一個事件。

下列範例會產生 C3739：

```cpp
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
