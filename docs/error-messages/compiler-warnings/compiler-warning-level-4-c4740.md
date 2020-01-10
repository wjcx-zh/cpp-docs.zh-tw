---
title: 編譯器警告 (層級 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 679f577eb7911b401473ee570e367ed5a8a094eb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989484"
---
# <a name="compiler-warning-level-4-c4740"></a>編譯器警告 (層級 4) C4740

傳入或傳出的內嵌 asm 程式碼隱藏了全域優化

當 `asm` 區塊進入或跳出時，就會停用該函式的全域優化。

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
