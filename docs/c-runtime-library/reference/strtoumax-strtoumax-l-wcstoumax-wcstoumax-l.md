---
title: strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l
ms.date: 11/04/2016
api_name:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstoumax
- _tcstoumax
- _strtoumax_l
- _wcstoumax_l
- _tcstoumax_l
- strtoumax
helpviewer_keywords:
- _strtoumax_l function
- conversion functions
- wcstoumax function
- _wcstoumax_l function
- strtoumax function
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
ms.openlocfilehash: a4ed09ad51e538f3964fea87fa55e410c79d3a5d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957682"
---
# <a name="strtoumax-_strtoumax_l-wcstoumax-_wcstoumax_l"></a>strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l

將字串轉換成最大的受支援不帶正負號整數類型的整數值。

## <a name="syntax"></a>語法

```C
uintmax_t strtoumax(
   const char *strSource,
   char **endptr,
   int base
);
uintmax_t _strtoumax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
uintmax_t wcstoumax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
uintmax_t _wcstoumax_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*strSource*<br/>
以 Null 終止的待轉換字串。

*endptr*<br/>
停止掃描的字元指標。

*base*<br/>
要使用的數字基底。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtoumax**會傳回已轉換的值（如果有的話）或**UINTMAX_MAX**溢位。 如果無法執行轉換， **strtoumax**會傳回0。 **wcstoumax**會傳回類似至**strtoumax**的值。 對於這兩個函式，如果發生溢位或下溢， **errno**會設為**ERANGE** 。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

這些函式中的每一個都會將輸入字串*strSource*轉換成**uintmax_t**的整數值。

**strtoumax**會在無法辨識為數字一部分的第一個字元處停止讀取字串*strSource* 。 這可能是終止的 null 字元，或者它可能是大於或等於*base*的第一個數位字元。 地區設定的 [ **LC_NUMERIC** ] 分類設定會決定*strSource*中的基數位符辨識。 如需詳細資訊，請參閱 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。 **strtoumax**和**wcstoumax**會使用目前的地區設定; **_strtoumax_l**和 **_wcstoumax_l**是相同的，不同之處在于它們會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**Null**，則停止掃描的字元指標會儲存在*endptr*所指向的位置。 如果無法執行任何轉換（找不到任何有效的數位或指定了不正確基底），則*strSource*的值會儲存在*endptr*所指向的位置。

**Strtoumax**的寬字元版本是**wcstoumax**;其*strSource*引數是寬字元字串。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoumax**|**strtoumax**|**strtoumax**|**wcstoumax**|
|**_tcstoumax_l**|**strtoumax_l**|**_strtoumax_l**|**_wcstoumax_l**|

**strtoumax**預期*strSource*會指向下列格式的字串：

> [*空格*][{ **+** &#124; &#124; &#124; }] [0 [{x}]] [位字母] **-**

空白字元*可能是*由空格和定位字元所組成，這些字元會被忽略。 *數位*是一或多個小數位數。 *字母*是一個或多個字母 ' a ' 到 ' z ' （或 ' a ' 到 ' z '）。 不符合此格式的第一個字元會停止掃描。 如果*base*介於2到36之間，則會使用它做為數位的基底。 如果*base*為0，則會使用*strSource*所指向之字串的初始字元來判斷基底。 如果第一個字元為 '0'，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果*base*為0，而第一個掃描的字元是 ' 0 '，則假設為八進位整數，而 ' 8 ' 或 ' 9 ' 字元會停止掃描。 **strtoumax**允許加號（ **+** ）或減號（ **-** ）前置詞，前置減號表示傳回值是已轉換字串絕對值的兩個補數。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtoumax**|\<stdlib.h>|
|**wcstoumax**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoumax_l**|\<stdlib.h>|
|**_wcstoumax_l**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [strtod](strtod-strtod-l-wcstod-wcstod-l.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l](strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll、_strtoll_l、wcstoll、_wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
