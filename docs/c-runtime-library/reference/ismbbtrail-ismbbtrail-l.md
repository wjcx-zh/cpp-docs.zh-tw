---
title: _ismbbtrail、_ismbbtrail_l
ms.date: 11/04/2016
apiname:
- _ismbbtrail
- _ismbbtrail_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ismbbtrail
- ismbbtrail
- _ismbbtrail_l
- ismbbtrail_l
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
ms.openlocfilehash: 5c09884f013e878fca516388f1ad933a2a08b35a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545934"
---
# <a name="ismbbtrail-ismbbtraill"></a>_ismbbtrail、_ismbbtrail_l

判斷位元組是否為多位元組字元的尾端位元組。

## <a name="syntax"></a>語法

```C
int _ismbbtrail(
   unsigned int c
);
int _ismbbtrail_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
要測試的整數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_ismbbtrail**傳回非零值，如果整數*c*是多位元組字元的第二個位元組。 例如，僅限在字碼頁 932 中，有效範圍是 0x40 到 0x7E 以及 0x80 到 0xFC。

## <a name="remarks"></a>備註

**_ismbbtrail**會針對地區設定相關行為使用目前的地區設定。 **_ismbbtrail_l**完全相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<mbctype.h> 或 \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|
|**_ismbbtrail_l**|\<mbctype.h> 或 \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|

\* 針對此測試條件的資訊清單常數。

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
