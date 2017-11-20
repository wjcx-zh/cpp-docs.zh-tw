---
title: "呼叫 C 函式中內嵌組譯碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3cd162026792bf8458c3725011b583d1eeb00772
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="calling-c-functions-in-inline-assembly"></a>在內嵌組譯碼中呼叫 C 函式
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `__asm` 區塊可以呼叫 C 函式，包括 C 程式庫常式。 下列範例會呼叫 `printf` 程式庫常式：  
  
```  
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
  
```  
printf( format, hello, world );  
```  
  
 這個範例會將指標依序推入 `world`、`hello` 和 `format`，然後呼叫 `printf`。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [內嵌組合語言](../../assembler/inline/inline-assembler.md)