---
title: strtof、_strtof_l、wcstof、_wcstof_l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
dev_langs:
- C++
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95db2a75d04454289b01f96680df6c5b5ab89e78
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof、_strtof_l、wcstof、_wcstof_l

將字串轉換為單精確度浮點數值。

## <a name="syntax"></a>語法

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>參數

*strSource*<br/>
以 Null 終止的待轉換字串。

*endptr*<br/>
停止掃描的字元指標。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**當 strtof**傳回值的浮點數，除了當表示法會造成溢位，情況為函式傳回 + /-**HUGE_VALF**。 正負號**HUGE_VALF**符合無法表示的值的正負號。 **當 strtof**若可以執行任何轉換，或反向溢位，則傳回 0。

**wcstof**類似地，傳回值**strtof**。 對於這兩個函式， **errno**設**為 ERANGE**如果發生溢位或反向溢位，而且無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個函式會將輸入的字串轉換*strSource*至**float**。 **Strtof**函式會將轉換*strSource*單精確度值。 **當 strtof**停止讀取字串*strSource*無法辨識為數字部分的第一個字元。 這可能是終止的 Null 字元。 **wcstof**是寬字元版本的**strtof**; 其*strSource*引數是寬字元字串。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

**LC_NUMERIC**目前的地區設定分類設定決定中的基底字元辨識*strSource*; 如需詳細資訊，請參閱[setlocale、 _wsetlocale](setlocale-wsetlocale.md). 不需要的函式 **_l**後置詞使用目前的地區設定; 具有後置詞的項目完全相同，只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不**NULL**，停止掃描的字元指標所指向的位置儲存*endptr*。 如果可以不執行任何轉換 （找不到沒有有效的數字或指定無效的基底） 的值*strSource*所指向的位置會儲存*endptr*。

**當 strtof**預期*strSource*指向字串的格式如下：

[*空白字元*] [*登*] [*位數*] [__。__*位數*] [{**e** &#124; **E**} [*登*]*位數*]

A*空白字元*可能包含空格和定位字元字元，會被忽略;*登*是加上 (**+**) 或減號 (**-**); 和*位數*一或多個十進位數字。 如果基底字元前沒有任何數字，則在基底字元後至少必須要有一個數字。 十進位數字後面可以接著指數，其中包含一個字母，簡介 (**e**或**E**) 和選擇性帶正負號的整數。 如果沒有出現指數部分也沒有出現基底字元，基底字元假設會跟在字串的最後一位數的後面。 不符合此格式的第一個字元會停止掃描。

這些函式的 UCRT 版本不支援 Fortran 樣式的轉換 (**d**或**D**) 指數的字母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**當 strtof**， **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> 或 \<stdlib.h>|
|**wcstof**， **_wcstof_l**|C:\<stdlib.h> 或 \<wchar.h> C++: &lt;cstdlib>、\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[字串轉換為數值函式](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
