---
title: 編譯器錯誤 C3701
ms.date: 11/04/2016
f1_keywords:
- C3701
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
ms.openlocfilehash: 6852d130b0f10282b8c22b0053760eca120252c7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758017"
---
# <a name="compiler-error-c3701"></a>編譯器錯誤 C3701

' function '： event_source 沒有事件

您嘗試在沒有事件方法的類別上使用[event_source](../../windows/event-source.md) 。 若要修正此錯誤，請將一或多個事件新增至類別。

下列範例會產生 C3701：

```cpp
// C3701.cpp
[ event_source(native) ]
class CEventSrc {
public:
   // uncomment the following line to resolve this C3701
   // __event void fireEvent(int i);
};   // C3701

int main() {
}
```
