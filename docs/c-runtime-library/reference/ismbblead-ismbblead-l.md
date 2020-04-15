---
title: _ismbblead、_ismbblead_l
description: 描述 Microsoft C 執行時庫 (CRT) _ismbblead和_ismbblead_l功能。
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ee3085d49a27f2f3c97c6578463cf3a0598b73c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343583"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead、_ismbblead_l

測試字元以確定它是否是多位元組字元的引線位元組。

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

*C*\
待測試整數。

*現場*\
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果整數*c*是多位元組位元元的第一個字節,則返回非零值。

## <a name="remarks"></a>備註

多位元組字元是由一個前導位元組，後面接著一個後置位元組所組成。 前導位元組會以所處指定字元集的特定範圍來識別。 例如,僅在代碼頁 932 中,潛在顧客位元組的範圍範圍為 0x81 - 0x9F 和 0xE0 - 0xFC。

**_ismbblead**使用當前區域設置進行與區域設置相關的行為。 **_ismbblead_l**是相同的,只是它使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

當區域設置為 UTF-8 時 **,_ismbblead**和 **_ismbblead_l**始終返回 0(false),無論*c*是否為引線位元組。

**_ismbblead**和 **_ismbblead_l**是特定於 Microsoft 的,而不是標準 C 庫的一部分。 我們不建議您在需要便攜式代碼的地方使用它們。 對於標準 C 相容性,請使用**mbrlen。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>通用文字例程對應

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

[位元組類別](../../c-runtime-library/byte-classification.md)\
[_ismbb例程](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
