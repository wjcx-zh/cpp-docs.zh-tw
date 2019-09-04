---
title: function pragma
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: f99f3c878789a6c47fdb0d48e0a8690d65fa8062
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220133"
---
# <a name="function-pragma"></a>function pragma

告知編譯器產生 pragma 引數清單中所指定函式的呼叫, 而不是內嵌它們。

## <a name="syntax"></a>語法

> **#pragma 函數 (** *function1* [ **,** *function2* ...] **)**

## <a name="remarks"></a>備註

內建函式通常會產生為內嵌程式碼, 而不是函式呼叫。 如果您使用內建[pragma](intrinsic.md)或[/Oi](../build/reference/oi-generate-intrinsic-functions.md)編譯器選項來指示編譯器產生內建函式, 您可以使用**function** pragma 明確強制執行函式呼叫。 一旦出現函式 pragma, 它就會在包含指定內建函式的第一個函式定義生效。 效果會持續到原始程式檔的結尾, 或是指定相同內建函式的`intrinsic` pragma 外觀。 在全域層級上 , 您只能在函式外部使用函式 pragma。

如需具有內建表單的函式清單, 請參閱內建[pragma](intrinsic.md)。

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

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
