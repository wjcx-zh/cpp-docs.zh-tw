---
title: _ecvt
ms.date: 04/05/2018
apiname:
- _ecvt
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
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 36c9cb2e8cd9eb4dd67bb91e9e4dbd36d8d1fc8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288668"
---
# <a name="ecvt"></a>_ecvt

將轉換**double**數字的字串。 這個函式已有更安全的版本可用；請參閱 [_ecvt_s](ecvt-s.md)。

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

*value*<br/>
要轉換的數字。

*count*<br/>
儲存的位數。

*dec*<br/>
儲存的小數點位置。

*簽署*<br/>
已轉換數字的正負號。

## <a name="return-value"></a>傳回值

**_ecvt**字串的數字，傳回的指標**NULL**如果發生錯誤。

## <a name="remarks"></a>備註

**_Ecvt**函式會將浮點數轉換為字元字串。 *值*參數是要轉換的浮點數。 此函式會儲存最多*計數*位數*值*做為字串和結尾處附加 null 字元 ('\0')。 如果在中的位數*值*超過*計數*，低位數四捨五入。 如果少於*計數*以零填補數字的字串。

所傳回的位數總數 **_ecvt**將不會超過 **_CVTBUFSIZE**。

字串中只能儲存數字。 小數點和的正負號的位置*值*可以取自*dec*並*登*之後呼叫。 *Dec*參數指向整數值，並提供字串的開頭小數點的位置。 0 或負整數值表示小數點位於第一位數字的左邊。 *號*參數指向表示已轉換的數字的正負號的整數。 如果整數值為 0，則數字為正數。 否則，數字為負數。

之間的差異 **_ecvt**並 **_fcvt**中的解譯*計數*參數。 **_ecvt**解譯*計數*做為輸出字串中的位數總數而 **_fcvt**解譯*計數*後的位數數字小數點。

**_ecvt**並 **_fcvt**使用單一靜態配置的緩衝區來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

這個函式會驗證它的參數。 如果*dec*或是*登*會**NULL**，或*計數*為 0 時，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**並**NULL**會傳回。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
