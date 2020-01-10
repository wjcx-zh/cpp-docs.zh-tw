---
title: _mbbtype、_mbbtype_l
ms.date: 11/04/2016
api_name:
- _mbbtype
- _mbbtype_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: ba4311921a0924d3f447feb1929a81ae1d816604
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952728"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype、_mbbtype_l

根據上一個位元組傳回位元組類型。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
要測試的字元。

*type*<br/>
要測試的位元組類型。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbbtype**會傳回字串中的位元組類型。 這項決定是由*類型*的值所指定，以提供控制項測試條件，這是內容相關的。 *類型*是字串中前一個位元組的類型。 下表中的資訊清單常數定義於 Mbctype.h。

|*類型*的值|**_mbbtype**測試|傳回值|*C*|
|---------------------|--------------------------|------------------|---------|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_SINGLE** (0)|單一位元組（0x20-0x7E，0xA1-0xDF）|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_LEAD**SHA-1|多位元組字元的前導位元組（0x81-0x9F、0xE0-0xFC）|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_ILLEGAL**<br /><br /> ( -1)|不正確字元（除了 0x20-0x7E、0xA1-0xDF、0x81-0x9F、0xE0-0xFC 以外的任何值|
|1|有效的後隨位元組|**_MBC_TRAIL**2|多位元組字元的尾端位元組（0x40-0x7E、0x80-0xFC）|
|1|有效的後隨位元組|**_MBC_ILLEGAL**<br /><br /> ( -1)|不正確字元（除了 0x20-0x7E、0xA1-0xDF、0x81-0x9F、0xE0-0xFC 以外的任何值|

## <a name="remarks"></a>備註

**_Mbbtype**函數會判斷多位元組字元中的位元組類型。 如果*類型*的值是1以外的任何值， **_mbbtype**會測試多位元組字元的有效單一位元組或前導位元組。 如果*類型*的值為1，則 **_mbbtype**會測試多位元組字元的有效後隨位元組。

輸出值會受到地區設定的**LC_CTYPE**分類設定影響;如需詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 此函式的 **_mbbtype**版本會針對此與地區設定相關的行為使用目前的地區設定; **_mbbtype_l**版本相同，不同之處在于它會改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在舊版中， **_mbbtype**的名稱為**chkctype**。 針對新的程式碼，請改用 **_mbbtype** 。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 針對可作為傳回值使用之資訊清單常數的定義。

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
