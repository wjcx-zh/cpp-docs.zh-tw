---
title: isprint、iswprint、_isprint_l、_iswprint_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
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
- iswprint
- _istprint
- isprint
dev_langs:
- C++
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af7cd775c22d4d34d7a6512938a0f612c3708940
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401512"
---
# <a name="isprint-iswprint-isprintl-iswprintl"></a>isprint、iswprint、_isprint_l、_iswprint_l

判斷整數是否代表可列印字元。

## <a name="syntax"></a>語法

```C
int isprint(
   int c
);
int iswprint(
   wint_t c
);
int _isprint_l(
   int c,
   _locale_t locale
);
int _iswprint_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

每個這些常式傳回非零，如果*c*是可列印字元的特定表示法。 **isprint**傳回非零值，如果*c*是可列印的字元，包括空格字元 (0x20-0x7E)。 **iswprint**傳回非零值，如果*c*可列印的寬字元，這包括寬字元的空間。 這些常式都會傳回 0，如果*c*不符合測試條件。

這些函式的測試條件的結果會取決於**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 不需要這些函式的版本 **_l**針對任何地區設定相關行為的後置詞使用目前的地區設定; 沒有版本 **_l**尾碼是一樣的不同之處在於會使用改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

行為**isprint**和 **_isprint_l**是未定義的如果*c*不 EOF 或 0 到 0xFF，（含) 範圍中。 當使用 CRT 偵錯程式庫和*c*不是其中一個函式產生，這些值的判斷提示。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_unicode 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istprint**|**isprint**|[_ismbcprint](ismbcgraph-functions.md)|**iswprint**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**isprint**|\<ctype.h>|
|**iswprint**|\<ctype.h> 或 \<wchar.h>|
|**_isprint_l**|\<ctype.h>|
|**_iswprint_l**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
