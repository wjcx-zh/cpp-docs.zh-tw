---
title: ':::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::'
ms.date: 4/2/2020
api_name:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- '_o_:::no-loc(_strtol_l):::'
- '_o_:::no-loc(_wcstol_l):::'
- '_o_:::no-loc(strtol):::'
- '_o_:::no-loc(wcstol):::'
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
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(strtol):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_tcstol_l):::'
helpviewer_keywords:
- ':::no-loc(wcstol)::: function'
- :::no-loc(wcstol):::_l function
- ':::no-loc(_tcstol)::: function'
- string conversion, to integers
- tcstol function
- :::no-loc(strtol):::_l function
- ':::no-loc(_wcstol_l)::: function'
- ':::no-loc(_strtol_l)::: function'
- ':::no-loc(strtol)::: function'
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(LONG_MAX):::'
- ':::no-loc(LONG_MIN):::'
- ':::no-loc(errno):::'
- ':::no-loc(ERANGE):::'
- ':::no-loc(EINVAL):::'
- ':::no-loc(LC_NUMERIC):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(_tcstol_l):::'
- ':::no-loc(localeconv):::'
- ':::no-loc(setlocale):::'
- ':::no-loc(_wsetlocale):::'
- ':::no-loc(strtod):::'
- ':::no-loc(_strtod_l):::'
- ':::no-loc(wcstod):::'
- ':::no-loc(_wcstod_l):::'
- ':::no-loc(strtoll):::'
- ':::no-loc(_strtoll_l):::'
- ':::no-loc(wcstoll):::'
- ':::no-loc(_wcstoll_l):::'
- ':::no-loc(strtoul):::'
- ':::no-loc(_strtoul_l):::'
- ':::no-loc(wcstoul):::'
- ':::no-loc(_wcstoul_l):::'
- ':::no-loc(atof):::'
- ':::no-loc(_atof_l):::'
- ':::no-loc(_wtof):::'
- ':::no-loc(_wtof_l):::'
ms.openlocfilehash: a5265b434f14f299532d6f5ebb65c83d75ea63ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232400"
---
# <a name="no-locstrtol-no-locwcstol-no-loc_strtol_l-no-loc_wcstol_l"></a>:::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::

將字串轉換成 **`long`** 整數值。

## <a name="syntax"></a>語法

```C
long :::no-loc(strtol):::(
   const char *string,
   char **end_ptr,
   int base
);
long :::no-loc(wcstol):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long :::no-loc(_strtol_l):::(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long :::no-loc(_wcstol_l):::(
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
輸出參數，設定為指向最後一個解讀字元之後的字元。 已忽略，如果**為 Null**。

*群體*\
要使用的數字基底。

*語言*\
要使用的地區設定。

## <a name="return-value"></a>傳回值

**:::no-loc(strtol):::**、 **:::no-loc(wcstol):::** 、 **:::no-loc(_strtol_l):::** 和會傳回 **:::no-loc(_wcstol_l):::** 以*字串*表示的值。 如果無法轉換，則會傳回0。 當標記法會造成溢位時，它們會傳回 **:::no-loc(LONG_MAX):::** 或 **:::no-loc(LONG_MIN):::** 。

**:::no-loc(errno):::****:::no-loc(ERANGE):::** 如果發生溢位或下溢，則設定為。 **:::no-loc(EINVAL):::** 如果*String*為**Null**，則會設為。 或者，如果*base*為非零且小於2，或大於36。 如需 **:::no-loc(ERANGE):::** 、和其他傳回碼的詳細資訊 **:::no-loc(EINVAL):::** ，請參閱[_dos :::no-loc(errno)::: 、 :::no-loc(errno)::: 、_sys_errlist 和 _sys_nerr](../../c-runtime-library/:::no-loc(errno):::-dos:::no-loc(errno):::-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**:::no-loc(strtol):::**、、和函式會 **:::no-loc(wcstol):::** **:::no-loc(_strtol_l):::** **:::no-loc(_wcstol_l):::** 將*字串*轉換為 **`long`** 。 它們會在不被辨識為數字一部分的第一個字元處停止讀取*字串*。 它可能是終止-null 字元，或大於或等於*基底*的第一個英數位元字元。

**:::no-loc(wcstol):::** 和 **:::no-loc(_wcstol_l):::** 是寬字元版本的 **:::no-loc(strtol):::** 和 **:::no-loc(_strtol_l):::** 。 其*字串*引數是寬字元字串。 這些函式的行為與相同 **:::no-loc(strtol):::** ， **:::no-loc(_strtol_l):::** 否則為。 地區設定的 **:::no-loc(LC_NUMERIC):::** 類別設定會決定*字串*中的基數位符（小數標記或小數點）辨識。 函數 **:::no-loc(strtol):::** 和 **:::no-loc(wcstol):::** 使用目前的地區設定。 **:::no-loc(_strtol_l):::** 和會 **:::no-loc(_wcstol_l):::** 改為使用傳入的地區設定。 如需詳細資訊，請參閱 [ :::no-loc(setlocale)::: ] 和[地區](../../c-runtime-library/locale.md)設定。

當*end_ptr*為**Null**時，會忽略它。 否則，停止掃描的字元指標會儲存在*end_ptr*所指向的位置。 如果找不到有效的數位，或指定了不正確基底，則不可能進行轉換。 然後，*字串*的值會儲存在*end_ptr*所指向的位置。

**:::no-loc(strtol):::** 需要*字串*以指向下列格式的字串：

> [*空格*][{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [英*數位*元]

方括弧（ `[ ]` ）會環繞選擇性元素。 大括弧和分隔號（ `{ | }` ）括住單一元素的替代專案。 空白字元可能是由空格和定位字元所組成，這些*字元會被*忽略。 英*數位元是十進位*數或字母 ' a ' 到 ' z ' （或 ' a ' 到 ' z '）。 不符合此表單的第一個字元會停止掃描。 如果*base*介於2到36之間，則會用來作為數位的基底。 如果*base*為0，則會使用*string*所指向之字串的初始字元來判斷基底。 如果第一個字元為0，而第二個字元不是 ' x ' 或 ' X '，則字串會解讀為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 ' a ' 到 ' z ' （或 ' A ' 到 ' Z '）被指派值10到35。 掃描只允許其值小於*基底*的字母。 基底範圍外的第一個字元會停止掃描。 例如，假設*字串*的開頭為 "01"。 如果*base*為0，掃描器會假設它是八進位整數。 ' 8 ' 或 ' 9 ' 字元會停止掃描。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**:::no-loc(_tcstol):::**|**:::no-loc(strtol):::**|**:::no-loc(strtol):::**|**:::no-loc(wcstol):::**|
|**:::no-loc(_tcstol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_wcstol_l):::**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**:::no-loc(strtol):::**|\<stdlib.h>|
|**:::no-loc(wcstol):::**|\<stdlib.h> 或 \<wchar.h>|
|**:::no-loc(_strtol_l):::**|\<stdlib.h>|
|**:::no-loc(_wcstol_l):::**|\<stdlib.h> 或 \<wchar.h>|

**:::no-loc(_strtol_l):::** 和函 **:::no-loc(_wcstol_l):::** 式是 Microsoft 特有的，而不是標準 C 程式庫的一部分。 如需其他相容性資訊，請參閱 [相容性](../compatibility.md)。

## <a name="example"></a>範例

請參閱的範例 [:::no-loc(strtod):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md) 。

## <a name="see-also"></a>另請參閱

[資料轉換](../data-conversion.md)\
[語言](../locale.md)\
[:::no-loc(localeconv):::](:::no-loc(localeconv):::.md)\
[:::no-loc(setlocale):::, :::no-loc(_wsetlocale):::](:::no-loc(setlocale):::-w:::no-loc(setlocale):::.md)\
[字串至數值函數](../string-to-numeric-value-functions.md)\
[:::no-loc(strtod):::, :::no-loc(_strtod_l):::, :::no-loc(wcstod):::, :::no-loc(_wcstod_l):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md)\
[:::no-loc(strtoll):::, :::no-loc(_strtoll_l):::, :::no-loc(wcstoll):::, :::no-loc(_wcstoll_l):::](:::no-loc(strtoll):::-:::no-loc(strtoll):::-l-:::no-loc(wcstoll):::-:::no-loc(wcstoll):::-l.md)\
[:::no-loc(strtoul):::, :::no-loc(_strtoul_l):::, :::no-loc(wcstoul):::, :::no-loc(_wcstoul_l):::](:::no-loc(strtoul):::-:::no-loc(strtoul):::-l-:::no-loc(wcstoul):::-:::no-loc(wcstoul):::-l.md)\
[:::no-loc(atof):::, :::no-loc(_atof_l):::, :::no-loc(_wtof):::, :::no-loc(_wtof_l):::](:::no-loc(atof):::-:::no-loc(atof):::-l-wtof-wtof-l.md)
