---
title: _fcvt
ms.date: 4/2/2020
api_name:
- _fcvt
- _o__fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a017ed58b962520793d5b10b088793dbc9b8a83d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347420"
---
# <a name="_fcvt"></a>_fcvt

將浮點數轉換為字串。 這個函式目前有更安全的版本，請參閱 [_fcvt_s](fcvt-s.md)。

## <a name="syntax"></a>語法

```C
char *_fcvt(
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
小數點後的小數位數。

*12 月*<br/>
預存小數點位置的指標。

*標誌*<br/>
預存正負號指標的指標。

## <a name="return-value"></a>傳回值

**_fcvt**傳回指向數位字串的指標,在錯誤時**傳回 NULL。**

## <a name="remarks"></a>備註

**_fcvt**函數將浮點數轉換為 null 連接端的字串。 *值*參數是要轉換的浮點數。 **_fcvt**將*值*的數位存儲為字串並附加空字元 ("\0")。 *計數*參數指定在小數點之後要儲存的數字數。 多餘的數位四捨五入以*計數*地點。 如果精度數位少於*計數*數位,則字串將用零填充。

**_fcvt**返回的總數不會超過 **_CVTBUFSIZE。**

字串中只能儲存數字。 小數點的位置和*值*符號可以從調用後的*dec*和 sign 獲得。 *dec*參數指向整數值;此整數值給出小數點相對於字串開頭的位置。 零或負整數值表示小數點位於第一位數字的左邊。 參數*符號*指向指示*值*符號的整數。 如果*值*為正,則整數設置為 0,如果*值*為負值,則將設置為非零數。

**_ecvt**和 **_fcvt**的區別在於對*計數*參數的解釋。 **_ecvt**將*計數*解釋為輸出字串中的總位數,而 **_fcvt**將*計數*解釋為小數點之後的位數。

**_ecvt**和 **_fcvt**使用單個靜態分配的緩衝區進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

這個函式會驗證它的參數。 如果*de*或*符號*為**NULL**,或者*計數*為 0,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則**errno**設定為**EINVAL**並返回**NULL。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
