---
title: 編譯器警告（層級1） C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: fbecdda481748aa77eefdab8d61e50350804e09f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051315"
---
# <a name="compiler-warning-level-1-c4733"></a>編譯器警告（層級1） C4733

內嵌 asm 指派給 ' FS： 0 '：處理常式未註冊為安全處理常式

在 FS：0修改值的函式若要加入新的例外狀況處理常式，可能無法處理安全的例外狀況，因為處理常式可能不會註冊為有效的例外狀況處理常式（請參閱[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)）。

若要解決此警告，請移除 FS：0定義或關閉此警告，並使用[。SAFESEH](../../assembler/masm/dot-safeseh.md)以指定安全的例外狀況處理常式。

下列範例會產生 C4733：

```cpp
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