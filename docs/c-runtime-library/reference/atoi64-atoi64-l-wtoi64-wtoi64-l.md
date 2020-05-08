---
title: _atoi64、_atoi64_l、_wtoi64、_wtoi64_l
ms.date: 4/2/2020
api_name:
- _atoi64_l
- _wtoi64
- _atoi64
- _wtoi64_l
- _o__atoi64
- _o__atoi64_l
- _o__wtoi64
- _o__wtoi64_l
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
- _atoi64
- _tstoi64
- _ttoi64
- wtoi64
- _tstoi64_l
- atoi64
- _wtoi64_l
- _wtoi64
- wtoi64_l
- _atoi64_l
- atoi64_l
helpviewer_keywords:
- tstoi64 function
- wtoi64 function
- atoi64_l function
- _ttoi64 function
- string conversion, to integers
- wtoi64_l function
- atoi64 function
- _tstoi64 function
- _atoi64_l function
- _wtoi64_l function
- ttoi64 function
- _wtoi64 function
- _atoi64 function
ms.assetid: 2c3e30fd-545d-4222-8364-0c5905df9526
ms.openlocfilehash: 555cd27e87324141f21bdd7ef12f9ff8ea1a4e09
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913574"
---
# <a name="_atoi64-_atoi64_l-_wtoi64-_wtoi64_l"></a>_atoi64、_atoi64_l、_wtoi64、_wtoi64_l

將字串轉換成 64 位元整數。

## <a name="syntax"></a>語法

```C
__int64 _atoi64(
   const char *str
);
__int64 _wtoi64(
   const wchar_t *str
);
__int64 _atoi64_l(
   const char *str,
   _locale_t locale
);
__int64 _wtoi64_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*str*<br/>
要轉換的字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

每個函式都會傳回將輸入字元解讀為數字所產生的 **__int64**值。 如果輸入無法轉換成該類型的值，則 **_atoi64**的傳回值為0。

如果溢位具有大型正整數值， **_atoi64**會在溢位的情況下，傳回具有大型負整數值的**I64_MAX**和**I64_MIN** 。

在所有超出範圍的情況下， **errno**會設定為**ERANGE**。 如果傳入的參數為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，並傳回0。

## <a name="remarks"></a>備註

這些函式會將字元字串轉換成 64 位元整數值。

輸入字串是一串字元，可解譯為所指定類型的數值。 此函式會從無法辨識為數字一部分的第一個字元處停止讀取輸入字串。 此字元可能是終止字串的 Null 字元 ('\0' 或 L'\0')。

**_Atoi64**的*str*引數具有下列格式：

> [*空格*][*sign*][*數位*]

空白字元*包含空格*或定位字元，這些字元會被忽略;*sign*為加號（+）或減號（-）;和*數位*是一或多個數位。

**_wtoi64**與 **_atoi64**相同，不同之處在于它會接受寬字元字串做為參數。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoi64**|**_atoi64**|**_atoi64**|**_wtoi64**|
|**_ttoi64**|**_atoi64**|**_atoi64**|**_wtoi64**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|--------------|---------------------|
|**_atoi64**， **_atoi64_l**|\<stdlib.h>|
|**_wtoi64**， **_wtoi64_l**|\<stdlib.h> 或 \<wchar.h>|

## <a name="example"></a>範例

此程式會顯示如何使用 **_atoi64**函式將儲存為字串的數位轉換為數值。

```C
// crt_atoi64.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the _atoi64 functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    __int64 value = 0;

    // An example of the _atoi64 function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: _atoi64( "  -2309 " ) = -2309
Function: _atoi64( "314127.64" ) = 314127
Function: _atoi64( "3336402735171707160320" ) = -1
Overflow condition occurred.
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[語言](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
