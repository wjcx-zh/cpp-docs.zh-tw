---
title: _mbbtype、_mbbtype_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbbtype
- _mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91b78b0dc57873810f96a793288da3f1457299de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404411"
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype、_mbbtype_l

根據上一個位元組傳回位元組類型。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

**_mbbtype**傳回字串中的位元組類型。 這項決策是即時的值所指定*類型*，這樣會提供控制項測試條件。 *型別*是一個位元組的字串中的型別。 下表中的資訊清單常數定義於 Mbctype.h。

|值*類型*|**_mbbtype**測試|傳回值|*C*|
|---------------------|--------------------------|------------------|---------|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_SINGLE** (0)|單一位元組 (0x20-0x7E、 0xA1-0xDF)|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_LEAD** (1)|多位元組字元的前導位元組 (0x81-0x9F、 0xE0-0xFC)|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_ILLEGAL**<br /><br /> ( -1)|無效的字元 (任何值除了 0x20-0x7E、 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|
|1|有效的後隨位元組|**_MBC_TRAIL** (2)|結尾的多位元組字元位元組 (0x40-0x7E、 0x80-0xFC)|
|1|有效的後隨位元組|**_MBC_ILLEGAL**<br /><br /> ( -1)|無效的字元 (任何值除了 0x20-0x7E、 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|

## <a name="remarks"></a>備註

**_Mbbtype**函式會判斷多位元組字元中的位元組類型。 如果值*類型*是 1，以外的任何值 **_mbbtype**有效的單一位元組或前導位元組的多位元組字元的測試。 如果值*類型*為 1， **_mbbtype**針對多位元組字元的有效的後隨位元組進行測試。

輸出值會影響的設定**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 **_Mbbtype**此函式版本會使用目前的地區設定針對此與地區設定相關行為; **_mbbtype_l**版本也一樣，只不過它會改用傳入的地區設定參數. 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在舊版中， **_mbbtype**命名為**chkctype**。 對於新的程式碼， **_mbbtype**改為。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 針對可作為傳回值使用之資訊清單常數的定義。

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
