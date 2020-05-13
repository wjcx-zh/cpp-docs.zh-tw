---
title: _ismbblead、_ismbblead_l
description: 描述 Microsoft C 執行時間程式庫（CRT） _ismbblead 和 _ismbblead_l 函數。
ms.date: 4/2/2020
api_name:
- _ismbblead_l
- _ismbblead
- _o__ismbblead
- _o__ismbblead_l
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: 7680793b71c4535ed75433ac98167e52a39896ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918673"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead、_ismbblead_l

測試字元，以判斷它是否為多位元組字元的前導位元組。

## <a name="syntax"></a>語法

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*c*\
待測試整數。

*語言*\
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果整數*c*是多位元組字元的第一個位元組，則會傳回非零值。

## <a name="remarks"></a>備註

多位元組字元是由一個前導位元組，後面接著一個後置位元組所組成。 前導位元組會以所處指定字元集的特定範圍來識別。 例如，僅限字碼頁932，前導位元組範圍從 0x81-0x9F 和 0xE0-0xFC。

**_ismbblead**會針對與地區設定相關的行為使用目前的地區設定。 **_ismbblead_l**是相同的，不同之處在于它會改為使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

當地區設定為 UTF-8 時， **_ismbblead**和 **_ismbblead_l**一律會傳回0（false），不論*c*是否為前導位元組。

**_ismbblead**和 **_ismbblead_l**是 Microsoft 特有的，而不是標準 C 程式庫的一部分。 我們不建議您在想要可攜的程式碼的地方使用它們。 針對標準 C 相容性，請改用**mbrlen** 。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>泛型文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|一律傳回 false|**_ismbblead**|一律傳回 false|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h> 或 \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|
|**_ismbblead_l**|\<mbctype.h> 或 \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|

\* 針對此測試條件的資訊清單常數。

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)\
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
