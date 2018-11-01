---
title: 編譯器警告 (層級 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 936dfb5464eabe7b1ac44df24445224fb9e204a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457880"
---
# <a name="compiler-warning-level-4-c4740"></a>編譯器警告 (層級 4) C4740

流量流入或流出內嵌組譯程式碼會隱藏全域最佳化

當沒有在跳至或共`asm`區塊中，全域最佳化已停用該函式。

下列範例會產生 C4740:

```
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```