---
title: 編譯器錯誤 C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: c6eb207342f44655d54e49d4cf0cd2410f7095da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562028"
---
# <a name="compiler-error-c3912"></a>編譯器錯誤 C3912

'event': 必須是委派類型的事件類型。

事件已宣告，但不是適當的型別。

如需詳細資訊，請參閱 <<c0> [ 事件](../../windows/event-cpp-component-extensions.md)。

下列範例會產生 C3912:

```
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```