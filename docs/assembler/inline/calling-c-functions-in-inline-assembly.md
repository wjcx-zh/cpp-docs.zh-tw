---
title: 在內嵌組譯碼中呼叫 C 函式
ms.date: 08/30/2018
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
ms.openlocfilehash: 4d12321cd90f596c94c2337e100663436d512107
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167176"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在內嵌組譯碼中呼叫 C 函式

**Microsoft 專屬**

`__asm` 區塊可以呼叫 C 函式，包括 C 程式庫常式。 下列範例會呼叫 `printf` 程式庫常式：

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

由於函式引數會在堆疊傳遞，您只要在呼叫函式之前推入需要的引述 (如前述範例中的字串指標) 即可。 引數會以反向順序推入，所以會依預期順序退出堆疊。 模擬 C 陳述式

```cpp
printf( format, hello, world );
```

這個範例會將指標依序推入 `world`、`hello` 和 `format`，然後呼叫 `printf`。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>