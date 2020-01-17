---
title: strtol、 wcstol、 _strtol_l、 _wcstol_l
ms.date: 01/14/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
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
ms.openlocfilehash: 83054e1b31b56fda96bdea198ab34d65d633f335
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123925"
---
# <a name="opno-locstrtol-opno-locwcstol-opno-loc_strtol_l-opno-loc_wcstol_l"></a>strtol、 wcstol、 _strtol_l、 _wcstol_l

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

*string*\
以 Null 終止的待轉換字串。

*end_ptr*\
輸出參數，設定為指向最後一個解讀字元之後的字元。 已忽略，如果**為 Null**。

*base*\
要使用的數字基底。

*地區*設定\
要使用的地區設定。

## <a name="return-value"></a>傳回值

**strtol** 、 **wcstol** 、 **_strtol_l** 和 **_wcstol_l** 會傳回以*字串*表示的值。 如果無法轉換，則會傳回0。 當表示會造成溢位時，它們會傳回 **LONG_MAX** 或 **LONG_MIN** 。

如果發生溢位或下溢， **errno** 會設定為 **ERANGE** 。 如果*string*為**Null**，則會設定為 **EINVAL** 。 或者，如果*base*為非零且小於2，或大於36。 如需 **ERANGE** 、 **EINVAL** 及其他傳回碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**strtol** 、 **wcstol** 、 **_strtol_l** 和 **_wcstol_l** 函數會將*字串*轉換為**long**。 它們會在不被辨識為數字一部分的第一個字元處停止讀取*字串*。 它可能是終止-null 字元，或大於或等於*基底*的第一個英數位元字元。

**wcstol** 和 **_wcstol_l** 是 **strtol** 和 **_strtol_l** 的寬字元版本。 其*字串*引數是寬字元字串。 這些函式的行為與 **strtol** 相同，否則 **_strtol_l** 。 地區設定的 **LC_NUMERIC** 類別目錄設定會決定*字串*中的基數位符（小數標記或小數點）辨識。 函數 **strtol** 和 **wcstol** 使用目前的地區設定。 **_strtol_l** 和 **_wcstol_l** 改用傳入的地區設定。 如需詳細資訊，請參閱 [setlocale] 和[地區](../../c-runtime-library/locale.md)設定。

當*end_ptr*為**Null**時，會忽略它。 否則，停止掃描的字元指標會儲存在*end_ptr*所指向的位置。 如果找不到有效的數位，或指定了不正確基底，則不可能進行轉換。 然後，*字串*的值會儲存在*end_ptr*所指向的位置。

**strtol** 預期*字串*必須指向下列格式的字串：

> [*空格*][{ **+** &#124; **-** }][**0** [{ **x** &#124; **}]** ] [英*數位*元]

方括弧（`[ ]`）會括住選擇性元素。 大括弧和分隔號（`{ | }`）會括住單一元素的替代專案。 空白字元可能是由空格和定位字元所組成，這些*字元會被*忽略。 英*數位元是十進位*數或字母 ' a ' 到 ' z ' （或 ' a ' 到 ' z '）。 不符合此表單的第一個字元會停止掃描。 如果*base*介於2到36之間，則會用來作為數位的基底。 如果*base*為0，則會使用*string*所指向之字串的初始字元來判斷基底。 如果第一個字元為0，而第二個字元不是 ' x ' 或 ' X '，則字串會解讀為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 ' a ' 到 ' z ' （或 ' A ' 到 ' Z '）被指派值10到35。 掃描只允許其值小於*基底*的字母。 基底範圍外的第一個字元會停止掃描。 例如，假設*字串*的開頭為 "01"。 如果*base*為0，掃描器會假設它是八進位整數。 ' 8 ' 或 ' 9 ' 字元會停止掃描。

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

**_strtol_l** 和 **_wcstol_l** 函式是 Microsoft 特有的，而不是標準 C 程式庫的一部分。 如需相容性的詳細資訊，請參閱[相容性](../compatibility.md)。

## <a name="example"></a>範例

請參閱[strtod](strtod-strtod-l-wcstod-wcstod-l.md)的範例。

## <a name="see-also"></a>請參閱

[資料轉換](../data-conversion.md)\
[Locale](../locale.md)\
[localeconv](localeconv.md)\
[setlocale，_wsetlocale](setlocale-wsetlocale.md)\
[字串至數值函數](../string-to-numeric-value-functions.md)\
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll、_strtoll_l、wcstoll、_wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)
