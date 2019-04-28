---
title: isascii、__isascii、iswascii
ms.date: 11/04/2016
apiname:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: d150e7bb335dc77ed86f445128eebf97b8be5ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287465"
---
# <a name="isascii-isascii-iswascii"></a>isascii、__isascii、iswascii

判斷特定字元是否為 ASCII 字元。

## <a name="syntax"></a>語法

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

## <a name="return-value"></a>傳回值

這些常式傳回非零值如果**c**表示特定的 ASCII 字元。 **__isascii**傳回非零值，如果**c**是 ASCII 字元 （0x00-0x7F 範圍）。 **iswascii**傳回非零值，如果**c**是 ASCII 字元的寬字元表示法。 這些常式都會傳回 0，如果**c**不符合測試條件。

## <a name="remarks"></a>備註

兩者 **__isascii**並**iswascii**除非已定義前置處理器巨集 _CTYPE_DISABLE_MACROS，否則，會實作為巨集。

回溯相容性， **isascii**實作為巨集才[ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md)未定義或定義為 0; 否則就是未定義。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**isascii**， **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> 或 \<ctype.h>|
|**iswascii**|C：\<wctype.h>、\<ctype.h>，或 \<wchar.h><br /><br /> C++：\<cwctype>、\<cctype >、\<wctype.h>、\<ctype.h> 或 \<wchar.h>|

**Isascii**， **__isascii**並**iswascii**函式是 Microsoft 專有的。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
