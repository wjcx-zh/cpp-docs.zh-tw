---
title: 編譯器警告 (層級 1) C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: e85bdc995fe16f91e2e9c734dacc65ca0b7b622d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182375"
---
# <a name="compiler-warning-level-1-c4405"></a>編譯器警告 (層級 1) C4405

'identifier': 識別項是保留的字

內嵌組譯碼的保留字做為變數的名稱。 這可能會造成無法預期的結果。 若要修正這個警告，避免保留字為內嵌組譯碼命名的變數。 下列範例會產生 C4405:

```
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