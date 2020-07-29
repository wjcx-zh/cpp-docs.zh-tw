---
title: 編譯器錯誤 C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 3794a1ce0fcbe60c06cb3efca45a3081e85c17ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210016"
---
# <a name="compiler-error-c2180"></a>編譯器錯誤 C2180

控制運算式具有類型 'type'

**`if`**、、或語句中的控制運算式 **`while`** **`for`** **`do`** 是轉換成的運算式 **`void`** 。 若要修正此問題，請將控制運算式變更為產生 **`bool`** 或可轉換成之型別的 **`bool`** 。

下列範例會產生 C2180：

```c
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```
