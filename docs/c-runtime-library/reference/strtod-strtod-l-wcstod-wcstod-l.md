---
title: strtod、_strtod_l、wcstod、_wcstod_l
ms.date: 4/2/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a688846d5db4d508327745728f8933c91bfd54e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337661"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod、_strtod_l、wcstod、_wcstod_l

將字串轉換成雙精確度值。

## <a name="syntax"></a>語法

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*strSource*<br/>
以 Null 終止的待轉換字串。

*端點*<br/>
停止掃描的字元指標。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtod**傳回浮點數的值,除非表示形式將導致溢出,在這種情況下,函數傳回 +/-**HUGE_VAL**。 **HUGE_VAL**的符號與無法表示的值的符號匹配。 無法執行轉換或發生,**則 strtod**傳回 0 。

**wcstod**返回類似於**strstrd**的值。 對於這兩個函數,如果發生溢出或下溢並調用無效的參數處理程式 **,errno**設置為**ERANGE,** 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如需這個傳回碼及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個函數會輸入字串*strSource*轉換為**雙**。 **strstrd**函數將*strSource*轉換為雙精度值。 **strtod**停止讀取字串*strSource*的第一個字元,它不能識別為數位的一部分。 這可能是終止的 Null 字元。 **wcstod**是一個寬字元版本的**斯特。** 其*strSource*參數是寬字元字串。 除此之外，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

當前區域設置**的LC_NUMERIC**類別設置決定了*strSource*中半徑點字元的識別。 如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 沒有 **_l**後綴的函數使用當前區域設置;**_strtod_l**與 **_strtod_l,** 只是它們使用傳入*區域設定*。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*端點*不是**NULL,** 則指向停止掃描的字元的指標儲存在*端點指向*的位置。 如果無法執行轉換(未找到有效數位或指定了無效的基),*則 strSource*的值儲存在*endptr*指向的位置。

**strtod**期望*strSource*指向以下形式之一的字串:

[*空白 ]*【*符號*】[*數字*:*半徑**數字*- &#124;*半徑**格式格式為數字**[e** ** &#124; **E**=**NAN***符號*[*數位**]** 空白 **** 符號 **radix**hexdigits***0x** &#124; **0X***sequence*= 十*六進位數字*-*&#124;半径*六*進位元 *****p** &#124; **P**=*符號*=*六進位數字**** 空白 *** 符號 [**INF** &#124; **INFINITY**] [*空白*]***

可選的前導*空格*可以由忽略的空格和製表元組成;*符號*是加(+)或減(-);*數位*是一個或多個十進位數位;*六進位數位*是一個或多個十六進位數位;*radix*是 radix 點字元,在預設「C」區域設定中為句點 (.),或者在當前區域設置不同或指定*區域設置*時特定於區域設置的值;*序列*是字母數字或下劃線字元的序列。 在十進位和十六進位數位窗體中,如果半徑點字元之前沒有數位,則半徑點字元之後必須至少顯示一個數位。 在十進位形式中,小數位數可以跟一個指數,它由介紹性字母 **(e**或**E)** 和可選簽名的整數組成。 在十六進位形式中,十六進位數位可以跟一個指數,它由介紹性字母 **(p**或**p)** 和可選簽名的十六進位整數組成,表示指數為 2 的冪。 在這兩種形式中,如果既不出現指數零件,也不出現半徑點字元,則假定半徑點字元遵循字串中的最後一個數位。 在**INF**和**NAN**窗體中都會忽略案例。 不適合這些窗體之一的第一個字元將停止掃描。

這些函數的 UCRT 版本不支援轉換 Fortran 樣式 (**d**或**D**) 指數字母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。 UCRT 版本支援 INF 和 NAN 值的十六進位元字串和往返,在早期版本中不支援這些值。 這還可能導致代碼的中斷更改。 例如,字串"0x1a"將在早期版本中被**strstrd**解釋為 0.0,但在 UCRT 版本中為 26.0。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**斯特托德** **, _strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> 或 &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C：&lt;stdlib.h> 或 &lt;wchar.h> C++：&lt;cstdlib>、&lt;stdlib.h> 或 &lt;wchar.h> |

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

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
