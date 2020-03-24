---
title: 具有變數引數清單的C++函式（）
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: f456f31dec631f7d9340563a93dfafeea49a72b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178440"
---
# <a name="functions-with-variable-argument-lists--c"></a>具有變數引數清單的C++函式（）

最後一個成員是省略符號 (...) 的函式宣告可以接受可變數目的引數。 在這些情況下，C++ 只會針對明確宣告的引數提供類型檢查。 需要撰寫連引數數目和類型都可以不同的一般函式時，您可以使用變數引數清單。 函數系列是使用可變引數清單的函式範例。`printf`*引數-宣告清單*

## <a name="functions-with-variable-arguments"></a>具有變數引數的函式

若要在宣告之後存取引數，請使用標準 include 檔中包含的宏 \<stdarg.h> >，如下所述。

**Microsoft 專屬**

如果省略符號是最後一個引數，且省略符號在逗號之後，則 Microsoft C++ 允許將省略符號指定為引數。 因此，`int Func( int i, ... );` 宣告是合法的，`int Func( int i ... );` 則不合法。

**END Microsoft 特定的**

宣告接受可變引數數目的函式至少需要一個預留位置引數 (即使不使用該引數)。 如果未提供這個預留位置引數，就無法存取其餘引數。

將**char**類型的引數當做變數引數傳遞時，它們會轉換成**int**類型。同樣地，當**float**類型的引數當做變數引數傳遞時，它們會轉換成**double**類型。 其他類型的引數受限於一般整數和浮點數提升。 如需詳細資訊，請參閱[標準轉換](standard-conversions.md)。

需要變數清單的函式是使用引數清單中的省略符號 (...) 宣告。 使用 \<stdarg.h> 中所述的類型和宏 > 包含檔案，以存取由變數清單傳遞的引數。 如需這些宏的詳細資訊，請參閱[va_arg、va_copy、va_end、va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。 (位於 C 執行階段程式庫文件中)。

下列範例顯示宏如何與類型一起使用（在 \<stdarg.h> 中宣告 >）：

```cpp
// variable_argument_lists.cpp
#include <stdio.h>
#include <stdarg.h>

//  Declaration, but not definition, of ShowVar.
void ShowVar( char *szTypes, ... );
int main() {
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );
}

//  ShowVar takes a format string of the form
//   "ifcs", where each character specifies the
//   type of the argument in that position.
//
//  i = int
//  f = float
//  c = char
//  s = string (char *)
//
//  Following the format specification is a variable
//  list of arguments. Each argument corresponds to
//  a format character in the format string to which
// the szTypes parameter points
void ShowVar( char *szTypes, ... ) {
   va_list vl;
   int i;

   //  szTypes is the last argument specified; you must access
   //  all others using the variable-argument macros.
   va_start( vl, szTypes );

   // Step through the list.
   for( i = 0; szTypes[i] != '\0'; ++i ) {
      union Printable_t {
         int     i;
         float   f;
         char    c;
         char   *s;
      } Printable;

      switch( szTypes[i] ) {   // Type to expect.
         case 'i':
            Printable.i = va_arg( vl, int );
            printf_s( "%i\n", Printable.i );
         break;

         case 'f':
             Printable.f = va_arg( vl, double );
             printf_s( "%f\n", Printable.f );
         break;

         case 'c':
             Printable.c = va_arg( vl, char );
             printf_s( "%c\n", Printable.c );
         break;

         case 's':
             Printable.s = va_arg( vl, char * );
             printf_s( "%s\n", Printable.s );
         break;

         default:
         break;
      }
   }
   va_end( vl );
}
//Output:
// 32.400002
// a
// Test string
```

前述範例說明了下列重要概念：

1. 您必須先建立清單標記做為 `va_list` 類型的變數，才能存取任何變數引數。 在上述範例中，標記稱為 `vl`。

1. 個別引數是使用 `va_arg` 巨集存取。 您必須告知 `va_arg` 巨集要擷取的引數類型，以便從堆疊傳送正確的位元組數目。 如果您對 `va_arg` 指定的大小類型不正確，且與呼叫程式所提供的大小不同，則結果將無法預期。

1. 您應該將使用 `va_arg` 巨集取得的結果明確轉型為您需要的類型。

您必須呼叫 `va_end` 巨集終止處理變數引數。
