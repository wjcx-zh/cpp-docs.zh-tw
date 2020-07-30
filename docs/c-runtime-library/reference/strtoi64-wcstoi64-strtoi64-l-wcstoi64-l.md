---
title: _strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l
ms.date: 4/2/2020
api_name:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
- _o__strtoi64
- _o__strtoi64_l
- _o__wcstoi64
- _o__wcstoi64_l
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
- _strtoi64
- strtoi64
- _stroi64_l
- _wcstoi64_l
- wcstoi64_l
- _wcstoi64
- wcstoi64
- strtoi64_l
helpviewer_keywords:
- _strtoi64 function
- _wcstoi64 function
- _strtoi64_l function
- string conversion, to integers
- _wcstoi64_l function
- strtoi64_l function
- wcstoi64 function
- strtoi64 function
- wcstoi64_l function
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
ms.openlocfilehash: ede96e39b596225d13c041468eb6172853959c6a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233947"
---
# <a name="_strtoi64-_wcstoi64-_strtoi64_l-_wcstoi64_l"></a>_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l

將字串轉換成 **`__int64`** 值。

## <a name="syntax"></a>語法

```C
__int64 _strtoi64(
   const char *strSource,
   char **endptr,
   int base
);
__int64 _wcstoi64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
__int64 _strtoi64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
__int64 _wcstoi64_l(
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

**_strtoi64**會傳回字串*strSource*中表示的值，但標記法會造成溢位，在這種情況下，它會傳回 **_I64_MAX**或 **_I64_MIN**。 如果沒有任何轉換可執行，函式會傳回 0。 **_wcstoi64**會傳回類似至**strtoi64**的值。

**_I64_MAX**和 **_I64_MIN**是以限制的方式定義。H.

如果*strSource*為**Null** ，或是*基底*為非零且小於2或大於36，則**errno**會設定為**EINVAL**。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>備註

**_Strtoi64**函數會將*strSource*轉換成 **`__int64`** 。 這兩個函式會在無法辨識為數字一部分的第一個字元處停止讀取字串*strSource* 。 這可能是終止的 null 字元，或者它可能是大於或等於*base*的第一個數位字元。 **_wcstoi64**是寬字元版本的 **_strtoi64**;其*strSource*引數是寬字元字串。 除此之外，這些函式的行為相同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoi64**|**_strtoi64**|**_strtoi64**|**_wcstoi64**|
|**_tcstoi64_l**|**_strtoi64_l**|**_strtoi64_l**|**_wcstoi64_l**|

地區設定的**LC_NUMERIC**類別設定會決定*strSource*中的基底字元辨識;如需詳細資訊，請參閱[setlocale](setlocale-wsetlocale.md)。 沒有 _l 尾碼的函式會使用目前的地區設定;**_strtoi64_l**和 **_wcstoi64_l**與對應的函式完全相同，但不含 **_l**尾碼，不同之處在于它們會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**Null**，則停止掃描的字元指標會儲存在*endptr*所指向的位置。 如果無法執行任何轉換（找不到任何有效的數位或指定了不正確基底），則*strSource*的值會儲存在*endptr*所指向的位置。

**_strtoi64**預期*strSource*會指向下列格式的字串：

> [*空格*][{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*數位*&#124;*字母*]

空白字元*可能是*由空格和定位字元所組成，這些字元會被忽略;*數位*是一或多個十進位數;*字母*是一個或多個字母 ' a ' 到 ' z ' （或 ' a ' 到 ' z '）。  不符合此格式的第一個字元會停止掃描。 如果*base*介於2到36之間，則會使用它做為數位的基底。 如果*base*為0，則會使用*strSource*所指向之字串的初始字元來判斷基底。 如果第一個字元為 0，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果*base*為0，而第一個掃描的字元是 ' 0 '，則假設為八進位整數，而 ' 8 ' 或 ' 9 ' 字元會停止掃描。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strtoi64**， **_strtoi64_l**|\<stdlib.h>|
|**_wcstoi64**， **_wcstoi64_l**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字串至數值函數](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
