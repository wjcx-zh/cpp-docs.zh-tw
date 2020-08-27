---
title: 編譯器錯誤 C2702
description: 描述 Microsoft C/c + + 編譯器錯誤 C2702。
ms.date: 08/25/2020
f1_keywords:
- C2702
helpviewer_keywords:
- C2702
ms.assetid: 6def15d4-9a8d-43e7-ae35-42d7cb57c27e
ms.openlocfilehash: 83210f6ab261a5ae6dd7320182c3f4c3539ff4d1
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898427"
---
# <a name="compiler-error-c2702"></a>編譯器錯誤 C2702

> `__except` 可能不會出現在終止區塊中

例外狀況處理常式 (**`__try`** / **`__except`**) 不能嵌套在 **`__finally`** 區塊內。

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
