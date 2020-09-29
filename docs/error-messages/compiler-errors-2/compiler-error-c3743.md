---
title: 編譯器錯誤 C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: b4bb198ae883e53e7947ce7f123bb0d3f092aaf3
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500392"
---
# <a name="compiler-error-c3743"></a>編譯器錯誤 C3743

只有當 event_receiver 的 ' layout_dependent ' 參數為 true 時，才能攔截/解除對整個介面

[__Unhook](../../cpp/unhook.md)函式會根據傳遞給 `layout_dependent` [event_receiver](../../windows/attributes/event-receiver.md)類別中參數的值，而有不同的參數數目。

下列範例會產生 C3743：

```cpp
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
