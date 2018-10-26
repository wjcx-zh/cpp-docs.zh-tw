---
title: 函式 （C/c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- function_CPP
- vc-pragma.function
dev_langs:
- C++
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93faf0c914ef395192fc0df65e71a1c3d33cc00d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065443"
---
# <a name="function-cc"></a>function (C/C++)
指定產生 pragma 引數清單中指定的函式呼叫。

## <a name="syntax"></a>語法

```
#pragma function( function1 [, function2, ...] )
```

## <a name="remarks"></a>備註

如果您使用`intrinsic`pragma （或 /Oi） 來告訴編譯器產生內建函式 （內建函式會產生為內嵌的程式碼中，不是函式呼叫），您可以使用**函式**pragma 明確強制執行函式呼叫。 function pragma 出現後，就會在包含指定內建函式的第一個函式定義生效。 其作用會持續到原始程式檔的結尾，或是的外觀`intrinsic`pragma 指定相同的內建函式。 **函式**pragma 可以用只在函式之外，在全域層級。

如需具有內建形式的函式清單，請參閱[#pragma 內建](../preprocessor/intrinsic.md)。

## <a name="example"></a>範例

```cpp
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

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)