---
title: 編譯器錯誤 C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 5bb2dba57c680882bb4bf8e4026f5720276b47b4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509379"
---
# <a name="compiler-error-c3765"></a>編譯器錯誤 C3765

' event '：無法在標記為 event_receiver 的類別/結構 ' type ' 中定義事件

如果類別標示 [event_receiver](../../windows/attributes/event-receiver.md) 屬性，則類別不能包含 [__event](../../cpp/event.md) 宣告。

下列範例會產生 C3765：

```cpp
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```
