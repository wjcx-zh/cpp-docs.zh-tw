---
title: _ismbbkpunct、_ismbbkpunct_l
ms.date: 4/2/2020
api_name:
- _ismbbkpunct_l
- _ismbbkpunct
- _o__ismbbkpunct
- _o__ismbbkpunct_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbbkpunct_l
- _ismbbkpunct_l
- ismbbkpunct
- _ismbbkpunct
helpviewer_keywords:
- _ismbbkpunct_l function
- ismbbkpunct_l function
- ismbbkpunct function
- _ismbbkpunct function
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
ms.openlocfilehash: 8cf2d0d38466c370d0110b71a302471679e64657
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915686"
---
# <a name="_ismbbkpunct-_ismbbkpunct_l"></a>_ismbbkpunct、_ismbbkpunct_l

檢查多位元組字元是否為標點符號字元。

## <a name="syntax"></a>語法

```C
int _ismbbkpunct(
   unsigned int c
);
int _ismbbkpunct_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*c*<br/>
待測試整數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果整數*c*是非 ASCII 標點符號， **_ismbbkpunct**會傳回非零值; 如果不是，則傳回0。 例如，僅在字碼頁 932， **_ismbbkpunct** 會測試片假名標點符號。 **_ismbbkpunct**會針對任何地區設定相關的字元設定使用目前的地區設定。 **_ismbbkpunct_l**是相同的，不同之處在于它會使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="remarks"></a>備註

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_ismbbkpunct**|\<mbctype.h>|
|**_ismbbkpunct_l**|\<mbctype.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
