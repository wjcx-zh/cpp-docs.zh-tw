---
title: 編譯器錯誤 C3732
ms.date: 11/04/2016
f1_keywords:
- C3732
helpviewer_keywords:
- C3732
ms.assetid: 2d55a7e1-9c39-4379-a093-2f7beb27e2ca
ms.openlocfilehash: 30ade41ae463923cc5cc9911469e587decacbc64
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752921"
---
# <a name="compiler-error-c3732"></a>編譯器錯誤 C3732

「介面」：引發 COM 事件的自訂介面無法從 IDispatch 繼承

支援 COM 事件的介面無法繼承自 `IDispatch`。 如需詳細資訊，請參閱[COM 中的事件處理](../../cpp/event-handling-in-com.md)。

下列錯誤會產生 C3732：

```cpp
// C3732.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="test")];

// to resolve this C3732, use dual instead of object
// or inherit from IUnknown
[ object ]
__interface I : IDispatch
{
};

[ event_source(com), coclass ]
struct A
{
   __event __interface I;   // C3732
};

int main()
{
}
```
