---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: dbeaf04d34aa20e15de48e99082ed07edb6129ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320482"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol、wcstol、_strtol_l、_wcstol_l

將字串轉換為**長**整數值。

## <a name="syntax"></a>語法

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*字串*\
以 Null 終止的待轉換字串。

*end_ptr*\
輸出參數,設置為指向最後一個解釋字元之後的字元。 已忽略,如果**為 NULL**。

*基地*\
要使用的數字基底。

*現場*\
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtol、wcstol、_strtol_l**和 **_wcstol_l**返回*字串***wcstol****_strtol_l**中表示的值。 如果無法轉換,它們返回 0。 當表示形式會導致溢出時,它們會返回**LONG_MAX**或**LONG_MIN**。

如果發生溢出或下溢,**則 errno**設置為**ERANGE。** 如果*字串*為**NULL,** 則將其設定為**EINVAL。** 或者,如果*基是*非零和小於 2,或大於 36。 有關**ERANGE、EINVAL**和其他傳回程式碼的詳細資訊,請參閱[_doserrno、errno、_sys_errlist和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 **ERANGE**

## <a name="remarks"></a>備註

**_wcstol_l** strtol、wcstol、_strtol_l **_strtol_l**與_wcstol_l函數將*字串***long**轉換為**strtol****wcstol**長 。 它們停止讀取未識別為數位的第一個字元的*字串*。 它可以是終止空字元,也可以是第一個大於或等於*基*的字母數位字元。

**wcstol**和 **_wcstol_l**是大字版本的**斯特托爾**和 **_strtol_l。** 它們的*字串*參數是寬字元字串。 這些函數與**strstl**和 **_strtol_l**相同。 區域**設置LC_NUMERIC類別**設置確定*對字串*中的半徑字元(小數標記或小數點)的識別。 函數**strtol**和**wcstol**使用當前區域設置。 **_strtol_l,_wcstol_l**使用傳入區域設置 **_wcstol_l**。 關於詳細資訊,請參閱設定區域設定】[與區域設定](../../c-runtime-library/locale.md)。

當*end_ptr*為**NULL**時,它將被忽略。 否則,指向停止掃描的字元的指標存儲在*end_ptr*指向的位置。 如果未找到有效數位或指定無效基數,則無法轉換。 然後 *,字串*的值存儲在*end_ptr*指向的位置。

**strtol**希望*字串*指向以下形式的字串:

> [*空白 ]*[**+** **-**&#124; ][**0** ] **x** &#124; **x** [ ] =*字母數字*|

方括弧(`[ ]`) 環繞可選元素。 對於單個元素,捲曲大括弧和垂直`{ | }`條( ) 環繞替代。 *空白*可以由忽略的空格和制表符組成。 *字母數位*是十進位數位或字母"a"到"z"(或"A"到"Z")。 不適合此窗體的第一個字元將停止掃描。 如果*基在*2 和 36 之間,則用作數位的基數。 如果*基為*0,則用*字串*指向的字串的初始字元用於確定基。 如果第一個字元為 0,而第二個字元不是"x"或"X",則字串將解釋為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母"a"到"z"(或"A"到"Z")被分配值10到35。 掃描只允許值小於*基*的字母。 基底範圍外的第一個字元會停止掃描。 例如,假設*字串*以"01"開頭。 如果*基數*為 0,則掃描器假定它是八進位整數。 "8"或"9"字元停止掃描。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> 或 \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> 或 \<wchar.h>|

**_strtol_l** 和**_wcstol_l** 函數特定於 Microsoft,而不是標準 C 庫的一部分。 如需其他相容性資訊，請參閱 [相容性](../compatibility.md)。

## <a name="example"></a>範例

請參閱[strtod](strtod-strtod-l-wcstod-wcstod-l.md)的示例。

## <a name="see-also"></a>另請參閱

[資料轉換](../data-conversion.md)\
[現場](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[字串到數值函數](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
