---
title: 編譯器警告 (層級 1) C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 7ec06e80ac8f61802258a62594029b15a55ebe42
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162565"
---
# <a name="compiler-warning-level-1-c4405"></a>編譯器警告 (層級 1) C4405

' identifier '：識別碼是保留字

保留給內嵌組解碼的字會當做變數名稱使用。 這可能會導致無法預期的結果。 若要修正這個警告，請避免使用保留給內嵌組解碼的字組來命名變數。 下列範例會產生 C4405：

```cpp
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```
