---
title: 編譯器錯誤 C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: 9054124cbfe2d86c062c6e97651bd69eebe5471c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748745"
---
# <a name="compiler-error-c3912"></a>編譯器錯誤 C3912

' event '：事件的類型必須是委派類型

事件已宣告，但不是正確的類型。

如需詳細資訊，請參閱[事件](../../extensions/event-cpp-component-extensions.md)。

下列範例會產生 C3912：

```cpp
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```
