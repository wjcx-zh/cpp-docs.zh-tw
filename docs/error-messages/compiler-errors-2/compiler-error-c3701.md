---
title: 編譯器錯誤 C3701
ms.date: 11/04/2016
f1_keywords:
- C3701
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
ms.openlocfilehash: c15cd9ce841d79787b3be9829c76038803b54d4d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508058"
---
# <a name="compiler-error-c3701"></a>編譯器錯誤 C3701

' function '： event_source 沒有任何事件

您嘗試在沒有事件方法的類別上使用 [event_source](../../windows/attributes/event-source.md) 。 若要修正這個錯誤，請將一或多個事件加入至類別。

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
