---
title: strtoul、_strtoul_l、wcstoul、_wcstoul_l
ms.date: 4/2/2020
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
- _o__strtoul_l
- _o__wcstoul_l
- _o_strtoul
- _o_wcstoul
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 60ae432fb11c5a29da2c4830c2a85305c6eaa46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365620"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul、_strtoul_l、wcstoul、_wcstoul_l

將字串轉換為不帶正負號的長整數值。

## <a name="syntax"></a>語法

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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

**strtoul**傳回轉換的值(如果有)或**溢出時ULONG_MAX。** 如果無法執行轉換 **,則strtoul**返回0。 **wcstoul**返回類似於**strtoul**的值。 對於這兩個函數,如果發生溢出或下溢 **,errno**設置為**ERANGE。**

有關此代碼和其他返回代碼的詳細資訊[,請參閱_doserrno、errno、_sys_errlist 和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>備註

每個函數都會將輸入字串*strSource*轉換為**未簽署****的長**。

**strtoul**停止讀取字串*strSource*的第一個字元,它不能識別為數位的一部分。 這可能是終止空字元,也可以是第一個數位字元大於或等於*基*。 區域設置**的LC_NUMERIC**類別設置決定了*strSource*中半徑字元的識別;有關詳細資訊,請參閱[設定區域設定](setlocale-wsetlocale.md)。 **斯特圖爾**和**wcstoul**使用當前區域設置;**_strtoul_l**和 **_wcstoul_l**是相同的,只是它們使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*端點*不是**NULL,** 則指向停止掃描的字元的指標儲存在*端點指向*的位置。 如果無法執行轉換(未找到有效數位或指定了無效的基),*則 strSource*的值儲存在*endptr*指向的位置。

**wcstoul**是一個寬字元版本的**斯特圖爾**;其*strSource*參數是寬字元字串。 否則，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**斯特圖爾**期望*strSource*指向以下形式的字串:

> [*空白 ]*[**+** **-**&#124; ][**0** ] **x** &#124; **x** [*]* 數字&#124;*字母**

*空白*可以由忽略的空格和制表符組成。 *數位*是一個或多個十進位數位。 *字母*是一個或多個字母"a"到"z"(或"A"到"Z")。 不符合此格式的第一個字元會停止掃描。 如果*基數*介於 2 和 36 之間,則用作數位的基數。 如果*基為*0,*則 strSource*指向的字串的初始字元用於確定基。 如果第一個字元為 0，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如,如果*基為*0,並且掃描的第一個字元為"0",則假定八進位整數,並且「8」或「9」字元將停止掃描。 **strtoul**允許**+** 加**-**( ) 或減 ( ) 符號前綴;前導減號表示返回值為否定。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> 或 \<wchar.h>|

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
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
