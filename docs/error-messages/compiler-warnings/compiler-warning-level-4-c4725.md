---
title: 編譯器警告 (層級 4) C4725
ms.date: 11/04/2016
f1_keywords:
- C4725
helpviewer_keywords:
- C4725
ms.assetid: effa0335-71c3-4b3b-8618-da4b9b46a95d
ms.openlocfilehash: c86d1a5351adf5ba29752613f2301a11fb1b93ce
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989517"
---
# <a name="compiler-warning-level-4-c4725"></a>編譯器警告 (層級 4) C4725

指令在一些 Pentium 上可能不正確

您的程式碼包含內嵌組件指令，可能在一些 Pentium 微處理器上不會產生精確的結果。

下列範例會產生 C4725：

```cpp
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
