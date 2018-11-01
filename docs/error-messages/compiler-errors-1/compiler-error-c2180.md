---
title: 編譯器錯誤 C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 16fcf15eb29743f74bbf2edcb1016f2e15228e5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553308"
---
# <a name="compiler-error-c2180"></a>編譯器錯誤 C2180

控制運算式具有類型 'type'

`if`、`while`、`for` 或 `do` 陳述式中的控制運算式，是轉換成 `void` 的運算式。 若要修正此問題，請將控制運算式變更為會產生 `bool` 的運算式或可轉換成 `bool` 的類型。

下列範例會產生 C2180：

```
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```