---
title: 編譯器錯誤 C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 86c043889c5342ed4f3edfc4d8a298bcbd345b3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456390"
---
# <a name="compiler-error-c3765"></a>編譯器錯誤 C3765

'event': 無法在 'type' 標記為 event_receiver 的類別/結構中定義事件

如果類別標示有[event_receiver](../../windows/event-receiver.md)屬性，此類別不能包含[__event](../../cpp/event.md)宣告。

下列範例會產生 C3765:

```
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```