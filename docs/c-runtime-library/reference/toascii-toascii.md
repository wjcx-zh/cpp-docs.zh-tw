---
title: toascii、__toascii
ms.date: 11/04/2016
api_name:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 09df829511b38b87cb41e32a59bee9f38a9b8f32
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957465"
---
# <a name="toascii-__toascii"></a>toascii、__toascii

透過截斷將字元轉換成 7 位元 ASCII 字元。

## <a name="syntax"></a>語法

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>參數

*C*<br/>
要轉換的字元。

## <a name="return-value"></a>傳回值

**__toascii**會將*c*的值轉換為7位 ASCII 範圍，並傳回結果。 沒有表示錯誤的保留傳回值。

## <a name="remarks"></a>備註

**__Toascii**常式會將指定的字元轉換成 ASCII 字元，方法是將它截斷為低序位7位。 不會套用任何其他轉換。

除非已定義預處理器宏 _CTYPE_DISABLE_MACROS，否則 **__toascii**常式會定義為宏。 針對回溯相容性，只有在[ &#95; &#95;STDC&#95; ](../../preprocessor/predefined-macros.md)未定義或定義為0時， **toascii**才會定義為宏。否則，它會是未定義的。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**toascii**、 **__toascii**|C: \<ctype.h><br /><br /> C++: \<cctype> 或 \<ctype.h>|

**Toascii**宏是 posix 延伸模組，而 **__toascii**是 Posix 延伸模組的 Microsoft 特定執行。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函式](../../c-runtime-library/to-functions.md)<br/>
