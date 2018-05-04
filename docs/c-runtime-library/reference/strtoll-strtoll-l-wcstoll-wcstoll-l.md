---
title: strtoll、_strtoll_l、wcstoll、_wcstoll_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
dev_langs:
- C++
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd469bcab9e64de070484ce6774e7449eda8d167
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="strtoll-strtolll-wcstoll-wcstolll"></a>strtoll、_strtoll_l、wcstoll、_wcstoll_l

將字串轉換成**長****長**值。

## <a name="syntax"></a>語法

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
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

**strtoll**傳回字串中的值，表示*strSource*，除了當表示法會造成溢位 — 在此情況下，它會傳回**LLONG_MAX**或**LLONG_MIN**。 如果沒有任何轉換可執行，函式會傳回 0。 **wcstoll**類似地，傳回值**strtoll**。

**LLONG_MAX**和**LLONG_MIN**限制中所定義。H.

如果*strSource*是**NULL**或*基底*為非零值，可能是小於 2 或大於 36， **errno**設為**EINVAL**.

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Strtoll**函式會將轉換*strSource*至**長****長**。 這兩個函式停止讀取字串*strSource*它們無法辨識的數字的第一個字元。 這可能是結束的 null 字元，或者可能是大於或等於第一個數字字元*基底*。 **wcstoll**是寬字元版本的**strtoll**; 其*strSource*引數是寬字元字串。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

地區設定的**LC_NUMERIC**類別目錄設定會決定中的基底字元辨識*strSource*; 如需詳細資訊，請參閱[setlocale、 _wsetlocale](setlocale-wsetlocale.md)。 不需要的函式 **_l**後置詞使用目前的地區設定;**_strtoll_l**和 **_wcstoll_l**會與對應的函式沒有後置的相同，只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不**NULL**，停止掃描的字元指標所指向的位置儲存*endptr*。 如果可以不執行任何轉換 （找不到沒有有效的數字或指定無效的基底） 的值*strSource*所指向的位置會儲存*endptr*。

**strtoll**預期*strSource*指向字串的格式如下：

> [*空白字元*] [{**+** &#124; **-**}] [**0** [{ **x**&#124; **X** }]] [*位數*&#124; *字母*]  

A*空白字元*可能包含空格和定位字元字元，會被忽略;*位數*一或多個十進位數字;*字母*是一或多個字母 'a' 到 'z' （或 'A' 到 'Z'）。 不符合此格式的第一個字元會停止掃描。 如果*基底*是介於 2 到 36，則會使用做為基底的數字。 如果*基底*為 0，指向之字串的初始字元*strSource*用來判斷基底。 如果第一個字元為 '0'，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果*基底*為 0 和掃描的第一個字元是 '0'、 八進位整數會假設和 '8' 或 '9' 的字元會停止掃描。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**strtoll**， **_strtoll_l**|\<stdlib.h>|
|**wcstoll**， **_wcstoll_l**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
