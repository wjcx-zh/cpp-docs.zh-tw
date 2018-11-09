---
title: to 函式
ms.date: 11/04/2016
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- To
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
ms.openlocfilehash: 8a6a1a69147c135ce539393e535f0e1f2d03ccfa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580743"
---
# <a name="to-functions"></a>to 函式

每個 **to** 函式和其相關聯巨集 (如果有的話) 都會將單一字元轉換為另一個字元。

|||
|-|-|
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper、_toupper、towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|
|[tolower、_tolower、towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||

## <a name="remarks"></a>備註

**to** 函式和巨集轉換如下。

|常式傳回的值|巨集|描述|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|將 `c` 轉換為 ASCII 字元|
|`tolower`|`tolower`|適用時，將 `c` 轉換為小寫|
|`_tolower`|`_tolower`|將 `c` 轉換為小寫|
|`towlower`|無|將 `c` 轉換為對應寬字元小寫字母|
|`toupper`|`toupper`|適用時，將 `c` 轉換為大寫|
|`_toupper`|`_toupper`|將 `c` 轉換為大寫|
|`towupper`|無|將 c 轉換為對應寬字元大寫字母|

若要使用同時定義為巨集之函式版本的 **to** 常式，請使用 `#undef` 指示詞來移除巨集定義，或不包括 CTYPE.H。 如果您使用 /Za 編譯器選項，編譯器會使用函式版本的 `toupper` 或 `tolower`。 `toupper` 和 `tolower` 函式的宣告是在 STDLIB.H 中。

`__toascii` 常式會將所有位元設定為 0，但不含 `c` 的低序位 7 個位元，因此轉換過的值代表 ASCII 字元集中的字元。 如果 `c` 已經代表 ASCII 字元，則 `c` 會保持不變。

`tolower` 和 `toupper` 常式：

- 相依於目前地區設定的 `LC_CTYPE` 分類 (`tolower` 會呼叫 `isupper`，而 `toupper` 會呼叫 `islower`)。

- 如果 `c` 代表目前地區設定中適當大小寫的可轉換字母，而且具有該地區設定的相反大小寫，則會轉換 `c`。 否則，`c` 會保持不變。

`_tolower` 和 `_toupper` 常式：

- 與地區設定無關且更快速的 `tolower` 和 **toupper** 版本。

- 只有在 **isascii(**`c`**)** 且 **isupper(**`c`**)** 或 **islower(**`c`**)** 分別為非零時才能使用。

- 如果 `c` 不是可進行轉換之適當大小寫的 ASCII 字母，則會有未定義的結果。

只有在下列兩個條件都為非零時，`towlower` 和 `towupper` 函式才會傳回轉換的 `c` 複本。 否則，`c` 會保持不變。

- `c` 是適當大小寫的寬字元 (亦即，`iswupper` 或 **iswlower** 分別為非零)。

- 具有目標大小寫的對應寬字元 (亦即，`iswlower` 或 **iswupper** 分別為非零)。

## <a name="example"></a>範例

```
// crt_toupper.c
/* This program uses toupper and tolower to
 * analyze all characters between 0x0 and 0x7F. It also
 * applies _toupper and _tolower to any code in this
 * range for which these functions make sense.
 */

#include <ctype.h>
#include <string.h>

char msg[] = "Some of THESE letters are Capitals.";
char *p;

int main( void )
{
   printf( "%s\n", msg );

   /* Reverse case of message. */
   for( p = msg; p < msg + strlen( msg ); p++ )
   {
      if( islower( *p ) )
         putchar( _toupper( *p ) );
      else if( isupper( *p ) )
         putchar( _tolower( *p ) );
      else
         putchar( *p );
   }
}
```

```Output
Some of THESE letters are Capitals.
sOME OF these LETTERS ARE cAPITALS.
```

## <a name="see-also"></a>請參閱

[資料轉換](../c-runtime-library/data-conversion.md)<br/>
[地區設定](../c-runtime-library/locale.md)<br/>
[is、isw 常式](../c-runtime-library/is-isw-routines.md)