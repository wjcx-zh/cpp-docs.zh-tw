---
title: 編譯器錯誤 C2702
ms.date: 11/04/2016
f1_keywords:
- C2702
helpviewer_keywords:
- C2702
ms.assetid: 6def15d4-9a8d-43e7-ae35-42d7cb57c27e
ms.openlocfilehash: 03a982ee35f0ac49a12568fc428de333f57f3ffa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758316"
---
# <a name="compiler-error-c2702"></a>編譯器錯誤 C2702

__except 可能不會出現在終止區塊中

例外狀況處理常式（`__try`/`__except`）無法嵌套在 `__finally` 區塊內。

下列範例會產生 C2702：

```cpp
// C2702.cpp
// processor: x86 IPF
int Counter;
int main() {
   __try {}
   __finally {
      __try {}   // C2702
      __except( Counter ) {}   // C2702
   }
}
```
