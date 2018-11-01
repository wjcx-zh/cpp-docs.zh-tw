---
title: 編譯器警告 (層級 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 0d0b0b912ef15294f9a4362a79dffd6d7eeabed8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474915"
---
# <a name="compiler-warning-level-1-c4733"></a>編譯器警告 (層級 1) C4733

內嵌 asm 指定給 'FS:0': 未註冊為安全的處理常式的處理常式

修改在 加入新的例外狀況處理常式的 FS:0 值的函式可能無法運作且安全的例外狀況，因為處理常式可能不會註冊為有效的例外狀況處理常式 (請參閱[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md))。

若要解決這個警告，請移除 FS:0 定義或關閉這個警告並使用[。SAFESEH](../../assembler/masm/dot-safeseh.md)指定安全例外狀況處理常式。

下列範例會產生 C4733:

```
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```