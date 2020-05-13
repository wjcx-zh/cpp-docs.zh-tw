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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a7ff3a8eaa3d9d42a5f1a9a7bf277a847aeccfee
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910862"
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

*endptr*<br/>
停止掃描的字元指標。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtof**會傳回浮點數的值，但標記法會造成溢位，在這種情況下，函數會傳回 +/-**HUGE_VALF**。 **HUGE_VALF**的正負號符合無法表示之值的正負號。 如果無法執行轉換或下溢，則**strtof**會傳回0。

**wcstof**會傳回類似至**strtof**的值。 對於這兩個函式，如果發生溢位或下溢，且叫用不正確參數處理常式（如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述），則**errno**會設定為**ERANGE** 。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個函式都會將輸入字串*strSource*轉換成**float**。 **Strtof**函數會將*strSource*轉換成單精確度值。 **strtof**會在無法辨識為數字一部分的第一個字元處停止讀取字串*strSource* 。 這可能是終止的 Null 字元。 **wcstof**是寬字元版本的**strtof**;其*strSource*引數是寬字元字串。 除此之外，這些函式的行為相同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

目前地區設定的 [ **LC_NUMERIC** ] 分類設定會決定*strSource*中的基底字元辨識。如需詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md)。 沒有 **_l**尾碼的函式會使用目前的地區設定;具有尾碼的是相同的，不同之處在于它們會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**Null**，則停止掃描的字元指標會儲存在*endptr*所指向的位置。 如果無法執行任何轉換（找不到任何有效的數位或指定了不正確基底），則*strSource*的值會儲存在*endptr*所指向的位置。

**strtof**預期*strSource*會指向下列格式的字串：

[*空格*][*sign*][*數位*][__.__*數位*][{**e** &#124; **e**} [*sign*]*數位*]

空白字元*可能是*由空格和定位字元所組成，這些字元會被忽略;*sign*可以是加號（**+**）或減號（**-**）;和*數位*是一或多個小數位數。 如果基底字元前沒有任何數字，則在基底字元後至少必須要有一個數字。 十進位數後面可以加上一個指數，其中包含一個簡介字母（**e**或**e**）和一個選擇性帶正負號的整數。 如果沒有出現指數部分也沒有出現基底字元，基底字元假設會跟在字串的最後一位數的後面。 不符合此格式的第一個字元會停止掃描。

這些函式的 UCRT 版本不支援轉換 Fortran 樣式（**d**或**d**）指數位母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtof**， **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> 或 \<stdlib.h>|
|**wcstof**， **_wcstof_l**|C：\<stdlib.h> 或 \<wchar.h> C++：&lt;cstdlib>、\<stdlib.h> 或 \<wchar.h>|

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
[語言](../../c-runtime-library/locale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
