---
title: 編譯器警告 (層級 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 0aa4cb9df3f6f9d7499c67fb0b07bee5dabd6d73
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219829"
---
# <a name="compiler-warning-level-4-c4740"></a>編譯器警告 (層級 4) C4740

傳入或傳出的內嵌 asm 程式碼隱藏了全域優化

當區塊跳出或跳出時 **`asm`** ，就會停用該函式的全域優化。

下列範例會產生 C4740：

```cpp
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```
