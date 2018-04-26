---
title: _mbsbtype、_mbsbtype_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8108372cd40aba6770136908b177dc82a9ff25e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype、_mbsbtype_l

傳回字串中的位元組類型。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*mbstr*<br/>
多位元組字元序列的位址。

*count*<br/>
從字串開頭的位元組位移。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbsbtype**和 **_mbsbtype_l**傳回整數值，指出指定的位元組上測試的結果。 下表中的資訊清單常數定義於 Mbctype.h。

|傳回值|位元組類型|
|------------------|---------------|
|**_MBC_SINGLE** (0)|單一位元組字元。 例如，在字碼頁 932， **_mbsbtype**傳回 0，如果指定的位元組範圍之內 0x20-0x7E 或 0xA1-0xDF。|
|**_MBC_LEAD** (1)|多位元組字元的前導位元組。 例如，在字碼頁 932， **_mbsbtype**如果指定的位元組範圍 0x81-0x9F 或 0xE0-內 0xFC 時則傳回 1。|
|**_MBC_TRAIL** (2)|多位元組字元的後隨位元組。 例如，在字碼頁 932， **_mbsbtype**傳回 2，如果指定的位元組範圍之內 0x40-0x7E 或 0x80-0xFC。|
|**_MBC_ILLEGAL** (-1)|**NULL**字串、 無效的字元，或**NULL**位元組位移的位元組之前，找到*計數*中*mbstr*。|

## <a name="remarks"></a>備註

**_Mbsbtype**函式會判斷多位元組字元字串中的位元組類型。 此函式會檢查的位元組位移*計數*中*mbstr*，忽略指定的位元組之前的無效字元。

輸出值會影響的設定**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale](setlocale-wsetlocale.md)如需詳細資訊。 這個函數，而不需要的版本 **_l**後置詞會針對地區設定相關行為; 使用目前的地區設定的版本與 **_l**尾碼是完全相同，不同之處在於它會使用傳入的地區設定參數中改用。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果輸入的字串為**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式 **_MBC_ILLEGAL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 適用於作為傳回值使用的資訊清單常數。

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
