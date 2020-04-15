---
title: strtoll、_strtoll_l、wcstoll、_wcstoll_l
ms.date: 4/2/2020
api_name:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
- _o__strtoll_l
- _o__wcstoll_l
- _o_strtoll
- _o_wcstoll
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: d5a0ce8cb2c1d5f88d5439b99047609b32c8d2ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365183"
---
# <a name="strtoll-_strtoll_l-wcstoll-_wcstoll_l"></a>strtoll、_strtoll_l、wcstoll、_wcstoll_l

將字串轉換為**長****長**值。

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

*端點*<br/>
停止掃描的字元指標。

*base*<br/>
要使用的數字基底。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtoll**傳回字串*strSource*中表示的值,除非表示形式將導致溢出時, 在這種情況下,它將返回**LLONG_MAX**或**LLONG_MIN**。 如果沒有任何轉換可執行，函式會傳回 0。 **wcstoll**返回值類似於**strto。**

**LLONG_MAX**和**LLONG_MIN**在「限制」中定義。H。

如果*strSource*為**NULL**或*基值*為非零,並且小於 2 或大於 36,**則 errno**設定為**EINVAL**。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**strt函數**將*strSource*轉換為**長****長**。 這兩個函數停止讀取字串*strSource*的第一個字元,他們無法識別為數位的一部分。 這可能是終止空字元,或者它可能是大於或等於*基*的第一個數位字元。 **wcstoll**是一個寬字元版本的**Strtoll;** 其*strSource*參數是寬字元字串。 除此之外，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**斯特托爾**|**斯特托爾**|**wc斯托爾**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

區域設置**LC_NUMERIC**類別設置決定了*strSource*中半徑字元的識別;有關詳細資訊,請參閱[設定區域設置,_wsetlocale](setlocale-wsetlocale.md)。 沒有 **_l**後綴的函數使用當前區域設置;但是,沒有_l後綴的函數使用當前區域設置。**_strtoll_l**和 **_wcstoll_l**與沒有後綴的相應函數相同,只不過它們使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*端點*不是**NULL,** 則指向停止掃描的字元的指標儲存在*端點指向*的位置。 如果無法執行轉換(未找到有效數位或指定了無效的基),*則 strSource*的值儲存在*endptr*指向的位置。

**strtoll**希望*strSource*指向以下形式的字串:

> [*空白 ]*[**+** **-**&#124; ][**0** ] **x** &#124; **x** [*]* 數字&#124;*字母**

*空格*可以由忽略的空格和制表符組成;*數位*是一個或多個十進位數位;*字母*是一個或多個字母"a"到"z"(或"A"到"Z")。 不符合此格式的第一個字元會停止掃描。 如果*基數*介於 2 和 36 之間,則用作數位的基數。 如果*基為*0,則*strSource*指向的字串的初始字元用於確定基。 如果第一個字元為 '0'，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如,如果*基為*0,掃描的第一個字元為"0",則假定八進位整數,並且「8」或「9」字元停止掃描。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**斯托爾 ,** **_strtoll_l**|\<stdlib.h>|
|**_wcstoll_l** **_wcstoll_l**|\<stdlib.h> 或 \<wchar.h>|

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
