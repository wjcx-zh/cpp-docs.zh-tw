---
title: strtof、_strtof_l、wcstof、_wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: f61aa0edeadd74a254f906dd745e18b059da7f24
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365139"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof、_strtof_l、wcstof、_wcstof_l

將字串轉換為單精確度浮點數值。

## <a name="syntax"></a>語法

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>參數

*strSource*<br/>
以 Null 終止的待轉換字串。

*端點*<br/>
停止掃描的字元指標。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtof**傳回浮點數的值,除非表示形式將導致溢出,在這種情況下,函數傳回 +/-**HUGE_VALF**。 **HUGE_VALF**的符號與無法表示的值的符號匹配。 無法執行轉換或發生,**則 strtof**傳回 0 。

**wcstof**返回的值類似於**strtof。** 對於這兩個函數,如果發生溢出或下溢並調用無效的參數處理程式 **,errno**設置為**ERANGE,** 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個函數會輸入字串*strSource*轉換為**浮點**。 **strtof**函數將*strSource*轉換為單精度值。 **strtof**停止讀取字串*strSource*的第一個字元,它不能識別為數位的一部分。 這可能是終止的 Null 字元。 **wcSTof**是一個寬字元版本的**斯特夫**;其*strSource*參數是寬字元字串。 除此之外，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

當前區域設置**LC_NUMERIC**類別設置決定了*strSource*中半徑字元的識別;有關詳細資訊,請參閱[設定區域設置,_wsetlocale](setlocale-wsetlocale.md)。 沒有 **_l**後綴的函數使用當前區域設置;但是,沒有_l後綴的函數使用當前區域設置。具有後綴的那些是相同的,只是它們使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*端點*不是**NULL,** 則指向停止掃描的字元的指標儲存在*端點指向*的位置。 如果無法執行轉換(未找到有效數位或指定了無效的基),*則 strSource*的值儲存在*endptr*指向的位置。

**strtof**期望*strSource*指向以下形式的字串:

[*空白 ]*【*符號*】[*數字*][__.__*數位*|[**e** &#124; **E**= =*符號*=*數位*|

*空格*可以由忽略的空格和制表符組成;*符號*是加**+**(**-**) 或 減 ( );*數位*是一個或多個十進位數位。 如果基底字元前沒有任何數字，則在基底字元後至少必須要有一個數字。 十進位數字可以跟一個指數,它由介紹性字母 **(e**或**E)** 和可選簽名的整數組成。 如果沒有出現指數部分也沒有出現基底字元，基底字元假設會跟在字串的最後一位數的後面。 不符合此格式的第一個字元會停止掃描。

這些函數的 UCRT 版本不支援轉換 Fortran 樣式 (**d**或**D**) 指數字母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**斯特特_strtof_l** **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> 或 \<stdlib.h>|
|**wcstof**, **_wcstof_l**|C：\<stdlib.h> 或 \<wchar.h> C++：&lt;cstdlib>、\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
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
