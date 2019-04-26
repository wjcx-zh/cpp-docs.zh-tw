---
title: 編譯器警告 (層級 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 936dfb5464eabe7b1ac44df24445224fb9e204a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187026"
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