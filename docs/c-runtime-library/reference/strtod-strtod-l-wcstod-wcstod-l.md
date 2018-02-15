---
title: "strtod、_strtod_l、wcstod、_wcstod_l | Microsoft Docs"
ms.custom: 
ms.date: 10/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
dev_langs:
- C++
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe18737b52ba2b04e3ee09813c6b48b6ebdf0363
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod、_strtod_l、wcstod、_wcstod_l

將字串轉換成雙精確度值。

## <a name="syntax"></a>語法

```C
double strtod(
   const char *nptr,
   char **endptr
);
double _strtod_l(
   const char *nptr,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *nptr,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *nptr,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*nptr*  
以 Null 終止的待轉換字串。

*endptr*  
停止掃描的字元指標。

*locale*  
要使用的地區設定。

## <a name="return-value"></a>傳回值

`strtod` 傳回值的浮點數，除了當表示法會造成溢位，情況為函式傳回 + /-`HUGE_VAL`。 `HUGE_VAL` 的正負號符合無法表示之值的正負號。 如果沒有任何轉換可執行，`strtod` 會傳回 0，否則會發生反向溢位。

`wcstod` 傳回類似 `strtod` 的值。 如果發生溢位或反向溢位且叫用無效的參數處理常式，這兩個函式的 `errno` 都會設為 `ERANGE`，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如需這個傳回碼及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個函式會將輸入的字串轉換*nptr*至`double`。 `strtod`函式會將轉換*nptr*雙精度值。 `strtod` 停止讀取字串*nptr*無法辨識為數字部分的第一個字元。 這可能是終止的 Null 字元。 `wcstod` 是寬字元版本的`strtod`; 其*nptr*引數是寬字元字串。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcstod`|`strtod`|`strtod`|`wcstod`|
|`_tcstod_l`|`_strtod_l`|`_strtod_l`|`_wcstod_l`|

`LC_NUMERIC`目前的地區設定分類設定判斷基數點中之字元的辨識*nptr*。 如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 功能，但不包含`_l`後置詞使用目前的地區設定;`_strtod_l`等同於`_strtod_l`不同之處在於會使用*地區設定*中傳遞。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不`NULL`，停止掃描的字元指標所指向的位置儲存*endptr*。 如果可以不執行任何轉換 （找不到沒有有效的數字或指定無效的基底） 的值*nptr*儲存在所指位置*endptr*。

`strtod` 必須要有*nptr*指向字串的其中一種下列形式：

[*whitespace*] [*sign*] {*digits* [*radix* *digits*] &#124; *radix* *digits*} [{**e** &#124; **E**} [*sign*] *digits*]  
[*whitespace*] [*sign*] {**0x** &#124; **0X**} {*hexdigits* [*radix* *hexdigits*] &#124; *radix* *hexdigits*} [{**p** &#124; **P**} [*sign*] *hexdigits*]  
[*whitespace*] [*sign*] {**INF** &#124; **INFINITY**}  
[*whitespace*] [*sign*] **NAN** [*sequence*]

選擇性的前置*空白字元*可能包含空格和定位字元字元，會被忽略;*登*是加號 （+） 或減號 （-）。*位數*一或多個十進位數字;*hexdigits*一或多個十六進位數字。*基數*是基數點字元中，可能是句號 （.） 中預設的"C"地區設定，或特定地區設定值，如果目前的地區設定不同，或當*地區設定*指定; *順序*是一連串的英數字元或底線字元。 在十進位和十六進位數字表單中，如果沒有數字基數點字元前至少一個必須出現在之後基數點字元。 以十進位格式，十進位數字後面可以接著指數，其中包含一個字母，簡介 (**e**或**E**) 和選擇性帶正負號的整數。 以十六進位格式，十六進位數字後面可以接著指數，其中包含一個字母，簡介 (**p**或**P**) 和選擇性帶正負號表示十六進位整數為 2 的乘冪的指數。 在任一形式中，如果指數的一部分或基數點字元都不會出現，基數點字元會假設遵循字串中的最後一位數。 在忽略大小寫**INF**和**NAN**表單。 不適用於任何一種形式的第一個字元會停止掃描。

這些函式的 UCRT 版本不支援 Fortran 樣式的轉換 (**d**或**D**) 指數的字母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。 UCRT 版本支援十六進位字串和 INF，NAN 值，不支援在舊版的往返。 這也會造成您的程式碼的重大變更。 例如，"0x1a"字串會解譯由`strtod`做 0.0 在舊版中，而 26.0 UCRT 版本中。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`strtod`, `_strtod_l`|C: &lt;stdlib.h> C++: &lt;cstdlib> 或 &lt;stdlib.h> |
|`wcstod`, `_wcstod_l`|C:&lt;stdlib.h> 或 &lt;wchar.h> C++: &lt;cstdlib>、&lt;stdlib.h> 或 &lt;wchar.h> |

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)   
[浮點支援](../../c-runtime-library/floating-point-support.md)   
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
[地區設定](../../c-runtime-library/locale.md)   
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)   
[strtol、wcstol、_strtol_l、_wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
[atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
[localeconv](../../c-runtime-library/reference/localeconv.md)   
[_create_locale、_wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
[_free_locale](../../c-runtime-library/reference/free-locale.md)