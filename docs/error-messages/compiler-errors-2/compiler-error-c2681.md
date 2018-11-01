---
title: 編譯器錯誤 C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: 8b311052d3a3525090d954c0dc8cee20e985b1b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632684"
---
# <a name="compiler-error-c2681"></a>編譯器錯誤 C2681

'type': 無效的運算式型別名稱

轉型運算子會嘗試將無效的型別轉換。 例如，如果您使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子，將運算式轉換成指標類型，來源運算式必須是指標。

下列範例會產生 C2681:

```
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```