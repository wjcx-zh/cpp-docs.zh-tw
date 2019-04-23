---
title: 編譯器錯誤 C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: bd66196c35715304577b8f6785261be8bdcdafec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775852"
---
# <a name="compiler-error-c3912"></a>編譯器錯誤 C3912

'event': 必須是委派類型的事件類型。

事件已宣告，但不是適當的型別。

如需詳細資訊，請參閱 <<c0> [ 事件](../../extensions/event-cpp-component-extensions.md)。

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