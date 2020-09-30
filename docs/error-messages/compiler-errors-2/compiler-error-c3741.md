---
title: 編譯器錯誤 C3741
ms.date: 11/04/2016
f1_keywords:
- C3741
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
ms.openlocfilehash: e551fa3dbf67d2158081bea9d19051d4703d9c43
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501302"
---
# <a name="compiler-error-c3741"></a>編譯器錯誤 C3741

' class '：當 event_receiver = true 的 ' layout_dependent ' 參數時，必須是 coclass

若 `layout_dependent=true` 為 [event_receiver](../../windows/attributes/event-receiver.md) 類別，則類別也必須有 [coclass](../../windows/attributes/coclass.md) 屬性。

下列範例會產生 C3741

```cpp
// C3741.cpp
// compile with: /c
// C3741 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I{ HRESULT f(); };

// Delete the following line to resolve.
[ event_receiver(com, layout_dependent=true)]

// class or struct must be declared with coclass
// Uncomment the following line to resolve.
// [ event_receiver(com, layout_dependent=true), coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct R : I {
   HRESULT f(){ return 0; }
   R(){}
   R(I* a){ __hook(I, a); }
};
```
