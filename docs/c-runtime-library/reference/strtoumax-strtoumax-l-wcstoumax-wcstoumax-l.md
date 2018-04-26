---
title: strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
- wcstoumax
- _tcstoumax
- _strtoumax_l
- _wcstoumax_l
- _tcstoumax_l
- strtoumax
dev_langs:
- C++
helpviewer_keywords:
- _strtoumax_l function
- conversion functions
- wcstoumax function
- _wcstoumax_l function
- strtoumax function
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e57298c9f3c4d2ef20e679abf7d7da3c75f1ec52
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="strtoumax-strtoumaxl-wcstoumax-wcstoumaxl"></a>strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l

將字串轉換成最大的受支援不帶正負號整數類型的整數值。

## <a name="syntax"></a>語法

```C
uintmax_t strtoumax(
   const char *strSource,
   char **endptr,
   int base
);
uintmax_t _strtoumax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
uintmax_t wcstoumax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
uintmax_t _wcstoumax_l(
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

**strtoumax**的話，會傳回已轉換的值，或**UINTMAX_MAX**溢位。 **strtoumax**可以執行任何轉換，則傳回 0。 **wcstoumax**類似地，傳回值**strtoumax**。 對於這兩個函式， **errno**設**為 ERANGE**發生溢位或反向溢位。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式會將輸入的字串轉換*strSource*至**uintmax_t**整數值。

**strtoumax**停止讀取字串*strSource*無法辨識為數字部分的第一個字元。 這可能是結束的 null 字元，或者可能是大於或等於第一個數字字元*基底*。 **LC_NUMERIC**之地區設定分類設定決定中的基底字元辨識*strSource*。 如需詳細資訊，請參閱 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。 **strtoumax**和**wcstoumax**使用目前的地區設定;**_strtoumax_l**和 **_wcstoumax_l**完全相同，只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不**NULL**，停止掃描的字元指標所指向的位置儲存*endptr*。 如果可以不執行任何轉換 （找不到沒有有效的數字或指定無效的基底） 的值*strSource*所指向的位置會儲存*endptr*。

寬字元版本的**strtoumax**是**wcstoumax**; 其*strSource*引數是寬字元字串。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoumax**|**strtoumax**|**strtoumax**|**wcstoumax**|
|**_tcstoumax_l**|**strtoumax_l**|**_strtoumax_l**|**_wcstoumax_l**|

**strtoumax**預期*strSource*指向字串的格式如下：

> [*空白字元*] [{**+** &#124; **-**}] [**0** [{ **x**&#124; **X** }]] [*位數*&#124; *字母*]  

A*空白字元*可能空間和索引標籤，會忽略的字元所組成。 *數字*一或多個十進位數字。 *字母*是一或多個字母 'a' 到 'z' （或 'A' 到 'Z'）。 不符合此格式的第一個字元會停止掃描。 如果*基底*是介於 2 到 36，則會使用做為基底的數字。 如果*基底*為 0，指向之字串的初始字元*strSource*用來判斷基底。 如果第一個字元為 '0'，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 基底範圍外的第一個字元會停止掃描。 例如，如果*基底*為 0 和掃描的第一個字元是 '0'、 八進位整數會假設和 '8' 或 '9' 的字元則會停止掃描。 **strtoumax**允許一個加號 (**+**) 或減號 (**-**) 前置詞，前置負號，表示傳回的值是二的補數的已轉換字串的絕對值。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**strtoumax**|\<stdlib.h>|
|**wcstoumax**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoumax_l**|\<stdlib.h>|
|**_wcstoumax_l**|\<stdlib.h> 或 \<wchar.h>|

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
[strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l](strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll、_strtoll_l、wcstoll、_wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
