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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2ca8a7fcd58e91ffa8982f30117b09af587d96cf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920190"
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

*計數*<br/>
小數點後的小數位數。

*十進位*<br/>
預存小數點位置的指標。

*簽訂*<br/>
預存正負號指標的指標。

## <a name="return-value"></a>傳回值

**_fcvt**會傳回數位字串的指標，錯誤則傳回**Null** 。

## <a name="remarks"></a>備註

**_Fcvt**函式會將浮點數轉換成以 null 結束的字元字串。 *Value*參數是要轉換的浮點數。 **_fcvt**將*值*的數位儲存為字串，並附加 null 字元（' \ 0 '）。 *Count*參數指定小數點之後要儲存的位數。 多餘的數位會四捨五入以*計算*位置。 如果精確度的位數少於*計數*，字串會以零填補。

**_Fcvt**傳回的總位數不會超過 **_CVTBUFSIZE**。

字串中只能儲存數字。 在呼叫之後，可以從*dec*和 sign 取得小數點和*值*正負號的位置。 *Dec*參數指向整數值;這個整數值會提供相對於字串開頭的小數點位置。 零或負整數值表示小數點位於第一位數字的左邊。 參數*正負號*指向表示*值*正負號的整數。 如果*值*為正數，則整數設定為0，如果*值*為負數，則設定為非零的數位。

**_Ecvt**和 **_fcvt**之間的差異在於*count*參數的轉譯。 **_ecvt**會將*count*解讀為輸出字串中的總位數，而 **_fcvt**會將*count*解讀為小數點之後的位數。

**_ecvt**和 **_fcvt**使用單一靜態配置的緩衝區來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

這個函式會驗證它的參數。 如果*dec*或*sign*為**Null**，或*count*為0，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，並傳回**Null** 。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
