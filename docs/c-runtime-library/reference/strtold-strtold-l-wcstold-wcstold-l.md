---
title: strtold、_strtold_l、wcstold、_wcstold_l
ms.date: 4/2/2020
api_name:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
- _o__strtold_l
- _o__wcstold_l
- _o_strtold
- _o_wcstold
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: 9acc98296651f549ceffb1e1deab350a71747ea5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365368"
---
# <a name="strtold-_strtold_l-wcstold-_wcstold_l"></a>strtold、_strtold_l、wcstold、_wcstold_l

將字串轉換為長雙精確度浮點數值。

## <a name="syntax"></a>語法

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
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

**strdd**將浮點數的值傳回為**長****雙**精度值,除非表示形式將導致溢出 - 在這種情況下,函數傳回 +/-**HUGE_VALL**。 **HUGE_VALL**的符號與無法表示的值的符號匹配。 無法執行轉換或發生,**則串劃**傳回 0 。

**wcstold**傳回的值類似於**串聯**。 對於這兩個函數,如果發生溢出或下溢並調用無效的參數處理程式 **,errno**設置為**ERANGE,** 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個函數會輸入字串*strSource*轉換為**長****雙**。 **串字**函數停止讀取字串*strSource*的第一個字元,它不能識別為數位的一部分。 這可能是終止的 Null 字元。 串**字**的寬字元版本是**wcstold;** 其*strSource*參數是寬字元字串。 除此之外，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

當前區域設置的**LC_NUMERIC**類別設置決定了*strSource*中半徑字元的識別。 如需詳細資訊，請參閱 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。 沒有 **_l**後綴的函數使用當前區域設置;**_strtold_l**和 **_wcstold_l**與 **_strtold**和 **_wcstold**相同,只是它們使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*端點*不是**NULL,** 則指向停止掃描的字元的指標儲存在*端點指向*的位置。 如果無法執行轉換(未找到有效數位或指定了無效的基),*則 strSource*的值儲存在*endptr*指向的位置。

**strtold**期望*strSource*指向以下形式的字串:

[*空白 ]*【*符號*】[*數字*][.*數位*|[**d** &#124; **d** &#124; **e** &#124; **e**=*符號*=*數位*|

*空格*可以由忽略的空格和制表符組成;*符號*是加**+**(**-**) 或 減 ( );*數位*是一個或多個十進位數位。 如果基底字元前沒有任何數字，則在基底字元後至少必須要有一個數字。 小數位數的後面會接著包含簡介字母 (**d**、**D**、**e** 或 **E**) 的指數以及選擇性的帶正負號整數。 如果沒有出現指數部分也沒有出現基底字元，基底字元假設會跟在字串的最後一位數的後面。 不符合此格式的第一個字元會停止掃描。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**串 ,** **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
