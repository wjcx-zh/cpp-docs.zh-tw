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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 8dcdff4cf6f3eff191dc126583c1ca8290133e02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365135"
---
# <a name="_strtoi64-_wcstoi64-_strtoi64_l-_wcstoi64_l"></a>_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l

將字串轉換為 **__int64**值。

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

*端點*<br/>
停止掃描的字元指標。

*base*<br/>
要使用的數字基底。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_strtoi64**傳回字串*strSource*中表示的值,除非表示形式將導致溢出,在這種情況下,它將返回 **_I64_MAX**或 **_I64_MIN**。 如果沒有任何轉換可執行，函式會傳回 0。 **_wcstoi64**傳回的值類似於**strtoi64**。

**_I64_MAX**和 **_I64_MIN**在"限制"中定義。H。

如果*strSource*為**NULL**或*基值*為非零,並且小於 2 或大於 36,**則 errno**設定為**EINVAL**。

有關這些代碼和其他返回代碼的詳細資訊[,請參閱_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>備註

**_strtoi64**函數將*strSource*轉換為 **__int64**。 這兩個函數停止讀取字串*strSource*的第一個字元,他們無法識別為數位的一部分。 這可能是終止空字元,也可以是第一個數位字元大於或等於*基*。 **_wcstoi64**是 **_strtoi64**的寬字元版本;其*strSource*參數是寬字元字串。 除此之外，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoi64**|**_strtoi64**|**_strtoi64**|**_wcstoi64**|
|**_tcstoi64_l**|**_strtoi64_l**|**_strtoi64_l**|**_wcstoi64_l**|

區域設置**LC_NUMERIC**類別設置決定了*strSource*中半徑字元的識別;有關詳細資訊,請參閱[設定區域設定](setlocale-wsetlocale.md)。 沒有_l後綴的函數使用當前區域設置;**_strtoi64_l**和 **_wcstoi64_l**與沒有 **_l**後綴的相應函數相同,只是它們使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*端點*不是**NULL,** 則指向停止掃描的字元的指標儲存在*端點指向*的位置。 如果無法執行轉換(未找到有效數位或指定了無效的基),*則 strSource*的值儲存在*endptr*指向的位置。

**_strtoi64**希望*strSource*指向以下形式的字串:

> [*空白 ]*[**+** **-**&#124; ][**0** ] **x** &#124; **x** [*]* 數字&#124;*字母**

*空格*可以由忽略的空格和制表符組成;*數位*是一個或多個十進位數位;*字母*是一個或多個字母"a"到"z"(或"A"到"Z")。  不符合此格式的第一個字元會停止掃描。 如果*基數*介於 2 和 36 之間,則用作數位的基數。 如果*基為*0,*則 strSource*指向的字串的初始字元用於確定基。 如果第一個字元為 0，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如,如果*基為*0,並且掃描的第一個字元為"0",則假定八進位整數,並且「8」或「9」字元將停止掃描。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strtoi64**, **_strtoi64_l**|\<stdlib.h>|
|**_wcstoi64**, **_wcstoi64_l**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
