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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 03bd90d2848922ee4153b79432bb76245f749ed6
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813572"
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

*endptr*<br/>
停止掃描的字元指標。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtod**會傳回浮點數的值，但標記法會造成溢位，在這種情況下，函數會傳回 +/-**HUGE_VAL**。 **HUGE_VAL**的正負號符合無法表示之值的正負號。 **strtod**如果無法 `0` 執行轉換或下溢，則 strtod 會傳回。

**wcstod**會傳回類似至**strtod**的值：

- 對於這兩個函式，如果發生溢位或下溢， **errno**會設為**ERANGE** 。
- 如果有不正確參數， **errno**會設定為**EINVAL** ，而且會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需此和其他傳回碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個函式都會將輸入字串*strSource*轉換為**double**。 **Strtod**函數會將*strSource*轉換為雙精確度值。 **strtod**會在無法辨識為數字一部分的第一個字元處停止讀取字串*strSource* 。 此字元可能是終止的 null 字元。 **wcstod**是寬字元版本的**strtod**;其*strSource*引數是寬字元字串。 除此之外，這些函式的行為相同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

目前地區設定的 [ **LC_NUMERIC** ] 分類設定會決定*strSource*中的基數點字元辨識。 如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 沒有 **_l**尾碼的函式會使用目前的地區設定;**_strtod_l**與 **_strtod_l**相同，不同之處在于它們會改用傳入的*地區*設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**Null**，則停止掃描的字元指標會儲存在*endptr*所指向的位置。 如果無法執行任何轉換（找不到任何有效的數位或指定了不正確基底），則*strSource*的值會儲存在*endptr*所指向的位置。

**strtod**預期*strSource*會指向下列其中一種格式的字串：

[*空格*][*sign*]{*數位*[*基數**數位*] &#124;*基數**數位*}[{**e** &#124; **e**} [*sign*]*數位**] [空白字元]*[*sign*] {**0x** &#124; **0x**} {*hexdigits* [*基數* *hexdigits*] &#124;*基數* *hexdigits*} [{**p** &#124; **p**} [*sign*] *hexdigits**] [空白字元]*[*sign*] {**INF** &#124;**無限大***} [空白字元]*[*sign*] **NAN** [*sequence*]

選擇性的前置空白字元可能是由空格和定位字元所組成，*它們會被*忽略;*sign*為加號（+）或減號（-）;*數位*是一或多個十進位數;*hexdigits*是一或多個十六進位數位;*基數*是基數點字元、預設 "C" 地區設定中的句號（.），或者，如果目前的地區設定不同或指定了*地區*設定，則為地區設定特定的值;*序列*是英數位元或底線字元的序列。 在 [十進位] 和 [十六進位數位] 表單中，如果在基數點字元前面沒有出現任何數位，則在基數點字元之後至少必須出現一個。 在十進位格式中，十進位數後面可以加上開頭字母（**e**或**e**）和選擇性帶正負號整數的指數。 在十六進位格式中，十六進位數位後面可以加上開頭字母（**p**或**p**）的指數，以及選擇性帶正負號的十六進位整數，表示指數為2的乘冪。 不論是哪一種形式，如果沒有指數部分或基數點字元，則會假設使用字串中的最後一個數位來執行基數點字元。 **INF**和**NAN**形式都會忽略大小寫。 不符合其中一種形式的第一個字元會停止掃描。

這些函式的 UCRT 版本不支援轉換 Fortran 樣式（**d**或**d**）指數位母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。 UCRT 版本支援十六進位字串，以及在舊版中不支援的 INF 和 NAN 值的往返。 這也會導致程式碼中的重大變更。 例如，在舊版中， **strtod**會將字串 "0x1a" 轉譯為0.0，但在 UCRT 版本中則是26.0。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtod**， **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> 或 &lt;stdlib.h> |
|**wcstod**， **_wcstod_l**|C：&lt;stdlib.h> 或 &lt;wchar.h> C++：&lt;cstdlib>、&lt;stdlib.h> 或 &lt;wchar.h> |

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
[多位元組字元序列的轉譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[語言](../../c-runtime-library/locale.md)<br/>
[字串至數值函數](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
