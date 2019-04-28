---
title: 編譯器錯誤 C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 4e26742de6c294018f81c6f49c1719fdb11d5149
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328532"
---
# <a name="compiler-error-c3704"></a>編譯器錯誤 C3704

'function': vararg 方法無法引發事件

您嘗試使用[__event](../../cpp/event.md) vararg 方法上。 若要修正這個錯誤，取代`fireEvent(int i, ...)`呼叫`fireEvent(int i)`呼叫下列程式碼範例所示。

下列範例會產生 C3704:

```
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```