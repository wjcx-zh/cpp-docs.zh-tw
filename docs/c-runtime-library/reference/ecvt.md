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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 227010fde5dc5ec82fc13c724c8d5a2f43788a8f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234194"
---
# <a name="_ecvt"></a>_ecvt

將 **`double`** 數位轉換為字串。 這個函式已有更安全的版本可用；請參閱 [_ecvt_s](ecvt-s.md)。

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

*計數*<br/>
儲存的位數。

*十進位*<br/>
儲存的小數點位置。

*簽署*<br/>
已轉換數字的正負號。

## <a name="return-value"></a>傳回值

**_ecvt**會傳回數位字串的指標;如果發生錯誤，則**為 Null** 。

## <a name="remarks"></a>備註

**_Ecvt**函式會將浮點數轉換成字元字串。 *Value*參數是要轉換的浮點數。 此函式會將*值*的*計數*數位儲存為字串，並附加 null 字元（' \ 0 '）。 如果*value*中的位數超過*count*，則會四捨五入低序位數位。 如果數位少於*計數*，字串會以零填補。

**_Ecvt**傳回的總位數不會超過 **_CVTBUFSIZE**。

字串中只能儲存數字。 在呼叫之後，可以從*dec*和*sign*取得小數點和*值*正負號的位置。 *Dec*參數會指向整數值，以提供相對於字串開頭的小數點位置。 0 或負整數值表示小數點位於第一位數字的左邊。 *Sign*參數會指向一個整數，表示已轉換數位的正負號。 如果整數值為 0，則數字為正數。 否則，數字為負數。

**_Ecvt**和 **_fcvt**之間的差異在於*count*參數的轉譯。 **_ecvt**會將*count*解讀為輸出字串中的總位數，而 **_fcvt**會將*count*解讀為小數點之後的位數。

**_ecvt**和 **_fcvt**使用單一靜態配置的緩衝區來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

這個函式會驗證它的參數。 如果*dec*或*sign*為**Null**，或*count*為0，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，並傳回**Null** 。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
