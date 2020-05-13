---
title: _atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l
ms.date: 4/2/2020
api_name:
- _atoldbl
- _atoldbl_l
- _atodbl
- _atoflt
- _atoflt_l
- _atodbl_l
- _o__atodbl
- _o__atodbl_l
- _o__atoflt
- _o__atoflt_l
- _o__atoldbl
- _o__atoldbl_l
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
- _atoflt
- _atoflt_l
- atodbl_l
- atoflt_l
- _atoldbl
- _atoldbl_l
- atodbl
- _atodbl_l
- atoldbl
- atoflt
- atoldbl_l
- _atodbl
helpviewer_keywords:
- _atodbl function
- _atoldbl_l function
- atoflt function
- atoflt_l function
- atoldbl function
- _atoldbl function
- atodbl_l function
- _atoflt_l function
- atoldbl_l function
- atodbl function
- string conversion, to floating point values
- _atoflt function
- _atodbl_l function
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
ms.openlocfilehash: 1106a3882fd9c6a6c2e9d434a6f49221ff6d99d0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920052"
---
# <a name="_atodbl-_atodbl_l-_atoldbl-_atoldbl_l-_atoflt-_atoflt_l"></a>_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l

將字串轉換為雙精度浮點數（**_atodbl**）、long double （**_atoldbl**）或 float （**_atoflt**）。

## <a name="syntax"></a>語法

```C
int _atodbl( _CRT_DOUBLE * value, char * str );
int _atodbl_l ( _CRT_DOUBLE * value, char * str, locale_t locale );
int _atoldbl( _LDOUBLE * value, char * str );
int _atoldbl_l ( _LDOUBLE * value, char * str, locale_t locale );
int _atoflt( _CRT_FLOAT * value, const char * str );
int _atoflt_l( _CRT_FLOAT * value, const char * str, locale_t locale );
```

### <a name="parameters"></a>參數

*值*<br/>
將字串轉換成浮點值所產生的雙精度浮點數、長雙精度浮點數或浮點值。 這些值包裝在結構中。

*str*<br/>
要剖析以轉換成浮點值的字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

若成功，即傳回 0。 可能的錯誤碼為 **_UNDERFLOW**或 **_OVERFLOW**，其定義于標頭檔\<math. h> 中。

## <a name="remarks"></a>備註

這些函式會將字串轉換成浮點值。 這些函式與**atof**系列函式之間的差異在於，這些函式不會產生浮點程式碼，也不會造成硬體例外狀況。 相反地，錯誤狀況會回報為錯誤碼。

如果字串沒有有效的轉譯作為浮點值，則*值*會設定為零，且傳回值為零。

這些具有 **_l**尾碼的函式版本與沒有尾碼的版本相同，不同之處在于它們會使用傳入的*地區*設定參數，而不是目前的執行緒地區設定。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|--------------|---------------------|
|**_atodbl**、 **_atoldbl**、 **_atoflt**<br /><br /> **_atodbl_l**、 **_atoldbl_l**、 **_atoflt_l**|\<stdlib.h>|

## <a name="example"></a>範例

```C
// crt_atodbl.c
// Uses _atodbl to convert a string to a double precision
// floating point value.

#include <stdlib.h>
#include <stdio.h>

int main()
{
   char str1[256] = "3.141592654";
   char abc[256] = "abc";
   char oflow[256] = "1.0E+5000";
   _CRT_DOUBLE dblval;
   _CRT_FLOAT fltval;
   int retval;

   retval = _atodbl(&dblval, str1);

   printf("Double value: %lf\n", dblval.x);
   printf("Return value: %d\n\n", retval);

   retval = _atoflt(&fltval, str1);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // A non-floating point value: returns 0.
   retval = _atoflt(&fltval, abc);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // Overflow.
   retval = _atoflt(&fltval, oflow);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   return 0;
}
```

```Output
Double value: 3.141593
Return value: 0

Float value: 3.141593
Return value: 0

Float value: 0.000000
Return value: 0

Float value: inf
Return value: 3
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[語言](../../c-runtime-library/locale.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
