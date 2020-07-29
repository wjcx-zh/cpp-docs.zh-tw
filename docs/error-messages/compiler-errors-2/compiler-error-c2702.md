---
title: 編譯器錯誤 C2702
ms.date: 11/04/2016
f1_keywords:
- C2702
helpviewer_keywords:
- C2702
ms.assetid: 6def15d4-9a8d-43e7-ae35-42d7cb57c27e
ms.openlocfilehash: eb8a19bf5d29a2a0c69dc27e9b22f76df63ce8e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216072"
---
# <a name="compiler-error-c2702"></a>編譯器錯誤 C2702

__except 可能不會出現在終止區塊中

例外狀況處理常式（ `__try` / **`__except`** ）無法嵌套在 **`__finally`** 區塊內。

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
