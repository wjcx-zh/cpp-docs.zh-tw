---
title: 編譯器警告 (層級 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: ae4dd6ebfb00441591a4aa1cdd2ecdfbf37f74d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397298"
---
# <a name="compiler-warning-level-1-c4558"></a>編譯器警告 (層級 1) C4558

je mimo rozsah 'lowerbound-上界' 的運算元 'value' 的值

傳遞至組件語言指令的值超出為參數指定的範圍。 系統會截斷值。

下列範例會產生 C4558:

```
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```