---
title: atof、_atof_l、_wtof、_wtof_l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wtof_l
- atof
- _atof_l
- _wtof
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
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
dev_langs:
- C++
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1897cc64c79a8593ade221ba24ecad6c037d3586
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="atof-atofl-wtof-wtofl"></a>atof、_atof_l、_wtof、_wtof_l

將字串轉換成雙精度浮點數。

## <a name="syntax"></a>語法

```C
double atof(
   const char *str
);
double _atof_l(
   const char *str,
   _locale_t locale
);
double _wtof(
   const wchar_t *str
);
double _wtof_l(
   const wchar_t *str,
   _locale_t locale
);
```

## <a name="parameters"></a>參數

*str*<br/>
要轉換的字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

每個函式會傳回**double**產生的輸入的字元解譯為數字值。 如果輸入無法轉換成該類型的值，則傳回值為 0.0。

在超出範圍的情況下， **errno**設**為 ERANGE**。 如果傳入的參數是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回 0。

## <a name="remarks"></a>備註

這些函式會將字元字串轉換成雙精確度浮點值。

輸入字串是一串字元，可解譯為所指定類型的數值。 此函式會從無法辨識為數字一部分的第一個字元處停止讀取輸入字串。 此字元可能是終止字串的 Null 字元 ('\0' 或 L'\0')。

*Str*引數**atof**和 **_wtof**具有下列格式：

[*空白字元*] [*登*] [*位數*] [__。__*位數*] [{**e** &#124; **E** } [*登*]*位數*]

A*空白字元*包含空格或定位字元，都會被忽略;*登*是加號 （+） 或減號 （-）; 和*位數*一或多個十進位數字。 如果小數點前沒有數字，則在小數點後至少必須要有一個數字。 十進位數字後面可能接著指數，其中包含一個字母，簡介 (**e**，或**E**) 和選擇性帶正負號的十進位整數。

這些函式的 UCRT 版本不支援 Fortran 樣式的轉換 (**d**或**D**) 指數的字母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用*地區設定*參數中傳遞而不是目前的地區設定。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|------------------|---------------------|
|**atof**， **_atof_l**|C：\<math.h> 或 \<stdlib.h> C++：\<cstdlib>、\<stdlib.h>、\<cmath> 或 \<math.h>|
|**_wtof**， **_wtof_l**|C:\<stdlib.h> 或 \<wchar.h> C++: \<cstdlib>、\<stdlib.h> 或 \<wchar.h>|

## <a name="example"></a>範例

此程式會顯示如何以字串的形式儲存的數字可以轉換成數值資料，請使用**atof**和 **_atof_l**函式。

```C
// crt_atof.c
//
// This program shows how numbers stored as
// strings can be converted to numeric
// values using the atof and _atof_l functions.

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function
    // using leading and training spaces.
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function
    // using the 'E' exponential formatting keyword.
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions
    // using the 'e' exponential formatting keyword
    // and showing different decimal point interpretations.
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}
```

```Output
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
