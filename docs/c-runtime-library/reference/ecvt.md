---
title: _ecvt | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8383abd1b45d1e13e4e42a334baa7f08c4bf10f2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*值*<br/>
要轉換的數字。

*count*<br/>
儲存的位數。

*dec*<br/>
儲存的小數點位置。

*簽署*<br/>
已轉換數字的正負號。

## <a name="return-value"></a>傳回值

**_ecvt**傳回的數字，字串的指標如果發生錯誤，則為 NULL。

## <a name="remarks"></a>備註

**_Ecvt**函式會將浮點數轉換為字元字串。 *值*參數是要轉換的浮點數。 此函式會儲存最多*計數*位數*值*做為字串，並將 null 字元 ('\0')。 如果數字位數中*值*超過*計數*，低序位字會捨入。 如果有少於*計數*以零填補數字的字串。

所傳回的數字總數 **_ecvt**將不超過 **_CVTBUFSIZE**。

字串中只能儲存數字。 小數點和的正負號的位置*值*可以取自*dec*和*登*呼叫之後。 *Dec*參數會指向提供字串的開頭與小數點的位置的整數值。 0 或負整數值表示小數點位於第一位數字的左邊。 *登*參數指向表示已轉換的數字的正負號的整數。 如果整數值為 0，則數字為正數。 否則，數字為負數。

之間的差異 **_ecvt**和 **_fcvt**中的解譯*計數*參數。 **_ecvt**解譯*計數*做為輸出字串中的位數總數而 **_fcvt**解譯*計數*之後位數的數目小數點。

**_ecvt**和 **_fcvt**使用單一靜態配置的緩衝區來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

這個函式會驗證它的參數。 如果*dec*或*登*是 NULL，或*計數*為 0、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL** ，而且會傳回 NULL。

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
