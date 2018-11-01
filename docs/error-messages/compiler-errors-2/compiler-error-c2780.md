---
title: 編譯器錯誤 C2780
ms.date: 11/04/2016
f1_keywords:
- C2780
helpviewer_keywords:
- C2780
ms.assetid: 423793d8-a3b2-4f35-85f8-ae1d043e2b69
ms.openlocfilehash: 9a427bbd79570a2646447d5326e034035306fac6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547446"
---
# <a name="compiler-error-c2780"></a>編譯器錯誤 C2780

'declaration'：預期 N 引數 - 提供 M

函式樣板包含太少或太多引數。

下列範例會產生 C2780，並示範如何修正此問題：

```
// C2780.cpp
template<typename T>
void f(T, T){}

int main() {
   f(1);  // C2780
   // try the following line instead
   // f(1,2);
}
```