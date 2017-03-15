---
title: "function (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "function_CPP"
  - "vc-pragma.function"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "function pragma"
  - "Pragma, 函式"
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
caps.latest.revision: 10
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# function (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定產生 pragma 引數清單中指定的函式呼叫。  
  
## 語法  
  
```  
  
#pragma function( function1 [, function2, ...] )  
```  
  
## 備註  
 如果您使用 **intrinsic** pragma \(或 \/Oi\) 指定編譯器產生內建函式 \(將內建函式產生為內嵌程式碼，而不是函式呼叫\)，您可以使用 **function** pragma 明確強制執行函式呼叫。  function pragma 出現後，就會在包含指定內建函式的第一個函式定義生效。  其作用會持續到原始程式檔的結尾，或是到指定同一個內建函式的 **intrinsic** pragma 出現為止。  **function** pragma 只能在函式之外 \(也就是在全域層級\) 使用。  
  
 如需具有內建形式之函式的清單，請參閱 [\#pragma intrinsic](../preprocessor/intrinsic.md)。  
  
## 範例  
  
```  
// pragma_directive_function.cpp  
#include <ctype.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
  
// use intrinsic forms of memset and strlen  
#pragma intrinsic(memset, strlen)  
  
// Find first word break in string, and set remaining  
// chars in string to specified char value.  
char *set_str_after_word(char *string, char ch) {  
   int i;  
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */  
  
   for(i = 0; i < len; i++) {  
      if (isspace(*(string + i)))   
         break;  
   }  
  
   for(; i < len; i++)   
      *(string + i) = ch;  
  
   return string;  
}  
  
// do not use strlen intrinsic  
#pragma function(strlen)  
  
// Set all chars in string to specified char value.  
char *set_str(char *string, char ch) {  
   // Uses intrinsic for memset, but calls strlen library function  
   return (char *) memset(string, ch, strlen(string));  
}  
  
int main() {  
   char *str = (char *) malloc(20 * sizeof(char));  
  
   strcpy_s(str, sizeof("Now is the time"), "Now is the time");  
   printf("str is '%s'\n", set_str_after_word(str, '*'));  
   printf("str is '%s'\n", set_str(str, '!'));  
}  
```  
  
  **str is 'Now\*\*\*\*\*\*\*\*\*\*\*\*'**  
**str is '\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!'**   
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)