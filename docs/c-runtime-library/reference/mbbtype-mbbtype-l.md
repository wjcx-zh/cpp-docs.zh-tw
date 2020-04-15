---
title: _mbbtype、_mbbtype_l
ms.date: 4/2/2020
api_name:
- _mbbtype
- _mbbtype_l
- _o__mbbtype
- _o__mbbtype_l
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 7e2e818ed70ec393e4f81008f76ca9efe9cfa7e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341403"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype、_mbbtype_l

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

*型別*<br/>
要測試的位元組類型。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbbtype**返回字串中的位元組類型。 此決策對上下文敏感,由*類型的值*指定,該值提供控制件測試條件。 *類型*是字串中前一個字節的類型。 下表中的資訊清單常數定義於 Mbctype.h。

|*型態*值|**_mbbtype**測試|傳回值|*C*|
|---------------------|--------------------------|------------------|---------|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_SINGLE** (0)|單位元組 (0x20 - 0x7E, 0xA1 - 0xDF)|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_LEAD** (1)|多位元組字元的引線位元組 (0x81 - 0x9F, 0xE0 - 0xFC)|
|1 以外的任何值|有效的單一位元組或前導位元|**_MBC_ILLEGAL**<br /><br /> ( -1)|無效字元(除 0x20 - 0x7E、0xA1 - 0xDF、0x81 - 0x9F、0xE0 - 0xFC 外的任何值|
|1|有效的後隨位元組|**_MBC_TRAIL** (2)|多位元組字元的尾隨位元組 (0x40 - 0x7E, 0x80 - 0xFC)|
|1|有效的後隨位元組|**_MBC_ILLEGAL**<br /><br /> ( -1)|無效字元(除 0x20 - 0x7E、0xA1 - 0xDF、0x81 - 0x9F、0xE0 - 0xFC 外的任何值|

## <a name="remarks"></a>備註

**_mbbtype**函數確定多位元組位元符中的位元組類型。 如果*類型*的值是除 1 以外的任何值,**則_mbbtype**測試多位元位元元的有效單位元組或引線位元組。 如果*類型*的值為 1,**則_mbbtype**測試多位元組位元元的有效跟蹤位元組。

輸出值受區域設置**LC_CTYPE**類別設置的影響;有關詳細資訊[,請參閱集本地設置_wsetlocale。](setlocale-wsetlocale.md) 此函數**的_mbbtype**版本使用此與區域設置相關的行為的當前區域設置;**_mbbtype_l**版本相同,只是它使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在早期版本中 **,_mbbtype**被命名為**chkctype**。 對於新代碼,請使用 **_mbbtype。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 針對可作為傳回值使用之資訊清單常數的定義。

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
