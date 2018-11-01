---
title: 編譯器警告 (層級 4) C4725
ms.date: 11/04/2016
f1_keywords:
- C4725
helpviewer_keywords:
- C4725
ms.assetid: effa0335-71c3-4b3b-8618-da4b9b46a95d
ms.openlocfilehash: 9da830133bbca2abcd5fa77339e698b35dae32f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455636"
---
# <a name="compiler-warning-level-4-c4725"></a>編譯器警告 (層級 4) C4725

指令在一些 Pentium 上可能不正確

您的程式碼包含內嵌組件指令，可能在一些 Pentium 微處理器上不會產生精確的結果。

下列範例會產生 C4725：

```
// C4725.cpp
// compile with: /W4
// processor: x86
double m32fp = 2.0003e-17;

void f() {
   __asm
   {
      FDIV m32fp   // C4725
   }
}

int main() {
}
```