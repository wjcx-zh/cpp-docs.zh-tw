---
title: "在內嵌組譯碼中呼叫 C 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 呼叫函式"
  - "函式呼叫, C 函式"
  - "函式呼叫, 在內嵌組譯碼中"
  - "函式 [C], 在內嵌組譯碼中呼叫"
  - "內嵌組譯碼, 呼叫函式"
  - "Visual C, 函式"
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 在內嵌組譯碼中呼叫 C 函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 `__asm` 區塊可以呼叫 C 函式，包括 C 程式庫常式。  下列範例會呼叫 `printf` 程式庫常式：  
  
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
  
 由於函式引數會在堆疊傳遞，您只要在呼叫函式之前推入需要的引述 \(如前述範例中的字串指標\) 即可。  引數會以反向順序推入，所以會依預期順序退出堆疊。  模擬 C 陳述式  
  
```  
printf( format, hello, world );  
```  
  
 這個範例會將指標依序推入 `world`、`hello` 和 `format`，然後呼叫 `printf`。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [內嵌組譯工具](../../assembler/inline/inline-assembler.md)