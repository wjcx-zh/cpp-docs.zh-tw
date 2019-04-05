---
title: function (C/C++)
ms.date: 11/04/2016
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: c57ff2053b3c1fd52474c7eb0dd598641632f789
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027255"
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