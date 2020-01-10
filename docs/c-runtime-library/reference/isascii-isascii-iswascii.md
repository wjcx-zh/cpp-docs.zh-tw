---
title: isascii、__isascii、iswascii
ms.date: 11/04/2016
api_name:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: b7677819a4b138b08ed4ff97de38c091ce0e94fd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857784"
---
# <a name="isascii-__isascii-iswascii"></a>isascii、__isascii、iswascii

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

*c*<br/>
待測試整數。

## <a name="return-value"></a>傳回值

如果**c**是 ASCII 字元的特定標記法，則每個常式都會傳回非零。 如果**c**是 ASCII 字元（在 0X00-0x7f 範圍內）， **__isascii**會傳回非零值。 如果**c**是 ASCII 字元的寬字元標記法，則**iswascii**會傳回非零值。 如果**c**不符合測試條件，這些常式都會傳回0。

## <a name="remarks"></a>備註

除非已定義預處理器宏 _CTYPE_DISABLE_MACROS，否則 **__isascii**和**iswascii**都會實作為宏。

為了回溯相容性，只有在[ &#95; &#95;STDC&#95; ](../../preprocessor/predefined-macros.md)未定義或定義為0時， **isascii**才會實作為宏。否則，它會是未定義的。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**isascii**， **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> 或 \<ctype.h>|
|**iswascii**|C：\<wctype.h>、\<ctype.h>，或 \<wchar.h><br /><br /> C++：\<cwctype>、\<cctype >、\<wctype.h>、\<ctype.h> 或 \<wchar.h>|

**Isascii**、 **__isascii**和**iswascii**函式是 Microsoft 特有的功能。 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
