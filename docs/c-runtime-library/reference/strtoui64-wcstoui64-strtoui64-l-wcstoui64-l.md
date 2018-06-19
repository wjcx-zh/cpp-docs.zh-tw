---
title: _strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
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
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
dev_langs:
- C++
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab70c1d74c0db837ba3d8e453988ca441f6fc06d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417878"
---
# <a name="strtoui64-wcstoui64-strtoui64l-wcstoui64l"></a>_strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l

將字串轉換成不帶正負號 **__int64**值。

## <a name="syntax"></a>語法

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
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

**_strtoui64**傳回代表字串中的值*strSource*時表示法可能會造成溢位在此情況下它傳回之外， **_UI64_MAX**。 **_strtoui64**可以執行任何轉換，則傳回 0。

**_UI64_MAX**定義限制。H.

如果*strSource*是**NULL**或*基底*為非零值，可能是小於 2 或大於 36， **errno**設為**EINVAL**.

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Strtoui64**函式會將轉換*strSource*至**不帶正負號** **__int64**。 **_wcstoui64**是寬字元版本的 **_strtoui64**; 其*strSource*引數是寬字元字串。 否則，這些函式的行為相同。

這兩個函式停止讀取字串*strSource*它們無法辨識的數字的第一個字元。 這可能是結束的 null 字元，或者可能是大於或等於第一個數字字元*基底*。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

目前的地區設定**LC_NUMERIC**類別目錄設定會決定中的基底字元辨識*strSource*; 如需詳細資訊，請參閱[setlocale](setlocale-wsetlocale.md)。 不含 _l 尾碼的函式會使用目前的地區設定;**_strtoui64_l**和 **_wcstoui64_l**與對應的功能，但不包含 **_l**後置詞，只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不**NULL**，停止掃描的字元指標所指向的位置儲存*endptr*。 如果可以不執行任何轉換 （找不到沒有有效的數字或指定無效的基底） 的值*strSource*儲存在所指位置*endptr*。

**_strtoui64**預期*strSource*指向字串的格式如下：

> [*空白字元*] [{**+** &#124; **-**}] [**0** [{ **x**&#124; **X** }]] [*位數*&#124; *字母*]  

A*空白字元*可能空間和索引標籤，會忽略的字元所組成。 *數字*一或多個十進位數字。 *字母*是一或多個字母 'a' 到 'z' （或 'A' 到 'Z'）。 不符合此格式的第一個字元會停止掃描。 如果*基底*是介於 2 到 36，則會使用做為基底的數字。 如果*基底*為 0，起始的字元字串所指向的*strSource*用來判斷基底。 如果第一個字元為 0，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果*基底*為 0 和掃描的第一個字元是 '0'、 八進位整數會假設和 '8' 或 '9' 的字元將會停止掃描。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
