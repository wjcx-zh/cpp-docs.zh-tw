---
title: atof、_atof_l、_wtof、_wtof_l
ms.date: 4/2/2020
api_name:
- _wtof_l
- atof
- _atof_l
- _wtof
- _o__atof_l
- _o__wtof
- _o__wtof_l
- _o_atof
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
ms.openlocfilehash: 8eee8db691b3b652768980237fc90bd675bac89b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232582"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof、_atof_l、_wtof、_wtof_l

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

*字串*<br/>
要轉換的字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

每個函式都會傳回將 **`double`** 輸入字元解讀為數字所產生的值。 如果輸入無法轉換成該類型的值，則傳回值為 0.0。

在所有超出範圍的情況下， **errno**會設定為**ERANGE**。 如果傳入的參數為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，並傳回0。

## <a name="remarks"></a>備註

這些函式會將字元字串轉換成雙精確度浮點值。

輸入字串是一串字元，可解譯為所指定類型的數值。 此函式會從無法辨識為數字一部分的第一個字元處停止讀取輸入字串。 此字元可能是終止字串的 Null 字元 ('\0' 或 L'\0')。

**Atof**和 **_wtof**的*str*引數具有下列格式：

[*空格*][*sign*][*數位*][__.__*數位*][{**e** &#124; **e** } [*sign*]*數位*]

空白字元*包含空格*或定位字元，這些字元會被忽略;*sign*為加號（+）或減號（-）;和*數位*是一或多個小數位數。 如果小數點前沒有數字，則在小數點後至少必須要有一個數字。 十進位數後面可能接著一個指數，其中包含一個開頭字母（**e**或**e**）和一個選擇性帶正負號的十進位整數。

這些函式的 UCRT 版本不支援轉換 Fortran 樣式（**d**或**d**）指數位母。 舊版 CRT 支援此非標準延伸模組，而且它可能是您程式碼的重大變更。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的*地區*設定參數，而不是目前的地區設定。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|------------------|---------------------|
|**atof**， **_atof_l**|C： \<math.h> 或 \<stdlib.h> c + +： \<cstdlib> 、 \<stdlib.h> \<cmath> 或\<math.h>|
|**_wtof**， **_wtof_l**|C： \<stdlib.h> 或 \<wchar.h> c + +： \<cstdlib> 、 \<stdlib.h> 或\<wchar.h>|

## <a name="example"></a>範例

此程式會顯示如何使用**atof**和 **_atof_l**函式，將儲存為字串的數位轉換為數值。

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
