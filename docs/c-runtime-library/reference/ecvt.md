---
title: _ecvt
ms.date: 4/2/2020
api_name:
- _ecvt
- _o__ecvt
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 5e1760d5c68e650f6fbf44866d4e368b9d6233b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348017"
---
# <a name="_ecvt"></a>_ecvt

將**雙**數轉換為字串。 這個函式已有更安全的版本可用；請參閱 [_ecvt_s](ecvt-s.md)。

## <a name="syntax"></a>語法

```C
char *_ecvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>參數

*值*<br/>
要轉換的數字。

*count*<br/>
儲存的位數。

*12 月*<br/>
儲存的小數點位置。

*標誌*<br/>
已轉換數字的正負號。

## <a name="return-value"></a>傳回值

**_ecvt**返回指向數字字串的指標;如果發生錯誤,**則為 NULL。**

## <a name="remarks"></a>備註

**_ecvt**函數將浮點數轉換為字串。 *值*參數是要轉換的浮點數。 此函數將*值*的數位*儲存*起來為字串,並追加空字元 ("\0")。 如果*值*中的位數超過*計數*,則低階數位將四捨五入。 如果*數位少於計數*數位,則字串將用零填充。

**_ecvt**返回的總數不會超過 **_CVTBUFSIZE。**

字串中只能儲存數字。 小數點的位置和*值*符號可以從調用後的*dec*和*sign*獲得。 *dec*參數指向一個整數值,該值給出相對於字串開頭的小數點的位置。 0 或負整數值表示小數點位於第一位數字的左邊。 *符號*參數指向指示轉換數位符號的整數。 如果整數值為 0，則數字為正數。 否則，數字為負數。

**_ecvt**和 **_fcvt**的區別在於對*計數*參數的解釋。 **_ecvt**將*計數*解釋為輸出字串中的總位數,而 **_fcvt**將*計數*解釋為小數點之後的位數。

**_ecvt**和 **_fcvt**使用單個靜態分配的緩衝區進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

這個函式會驗證它的參數。 如果*de*或*符號*為**NULL**,或者*計數*為 0,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則**errno**設定為**EINVAL**並返回**NULL。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
