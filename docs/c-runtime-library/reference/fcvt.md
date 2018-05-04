---
title: _fcvt | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fcvt
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
- _fcvt
dev_langs:
- C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fefe9bbfc1904847af5594a4d663b1eb8299fc9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="fcvt"></a>_fcvt

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

*dec*<br/>
預存小數點位置的指標。

*簽署*<br/>
預存正負號指標的指標。

## <a name="return-value"></a>傳回值

**_fcvt**傳回數字的字串，發生錯誤的 NULL 指標。

## <a name="remarks"></a>備註

**_Fcvt**函式會將浮點數轉換成以 null 結束的字元字串。 *值*參數是要轉換的浮點數。 **_fcvt**儲存的位數*值*做為字串，並將 null 字元 ('\0')。 *計數*參數會指定要儲存在小數點後面的位數。 過多的數字四捨五入至*計數*放置。 如果有少於*計數*位有效位數，此字串以零填補。

所傳回的數字總數 **_fcvt**將不超過 **_CVTBUFSIZE**。

字串中只能儲存數字。 小數點和的正負號的位置*值*可以取自*dec*並在呼叫之後的登入。 *Dec*參數指向整數值，這個整數值會提供對於字串開頭的小數點的位置。 零或負整數值表示小數點位於第一位數字的左邊。 參數*登*點表示的正負號的整數到*值*。 如果整數設定為 0*值*是正面的且設定為非零的數字如果*值*是負數。

之間的差異 **_ecvt**和 **_fcvt**中的解譯*計數*參數。 **_ecvt**解譯*計數*做為輸出字串中的位數總數而 **_fcvt**解譯*計數*之後位數的數目小數點。

**_ecvt**和 **_fcvt**使用單一靜態配置的緩衝區來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

這個函式會驗證它的參數。 如果*dec*或*登*是 NULL，或*計數*為 0、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL** ，而且會傳回 NULL。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
