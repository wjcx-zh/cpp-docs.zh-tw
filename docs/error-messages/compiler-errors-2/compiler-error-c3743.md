---
title: 編譯器錯誤 C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: 137913e0c6909712cbb6745666112d315925ab0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618994"
---
# <a name="compiler-error-c3743"></a>編譯器錯誤 C3743

可以只攔截/取消攔截整個介面當 event_receiver 的 'layout_dependent' 參數為 true 時

[__Unhook](../../cpp/unhook.md)函式而異，它會採用根據值傳遞至參數的數目`layout_dependent`中的參數[event_receiver](../../windows/event-receiver.md)類別。

下列範例會產生 C3743:

```
// C3743.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];
[object] __interface I { HRESULT f(); };

[event_receiver(com, layout_dependent=true), coclass]
struct R : I {
        HRESULT f() {
      return 0;
   }
        R() {
   }

   R(I* a) {
      __hook(I, a, &R::f);   // C3743
      // The following line resolves the error.
      // __hook(I, a);
   }
};
```