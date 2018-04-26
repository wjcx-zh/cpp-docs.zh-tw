---
title: ispunct、iswpunct、_ispunct_l、_iswpunct_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
- iswpunct
- _istpunct
- ispunct
dev_langs:
- C++
helpviewer_keywords:
- _istpunct function
- _ispunct_l function
- iswpunct function
- ispunct function
- istpunct function
- ispunct_l function
- _iswpunct_l function
- iswpunct_l function
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22240d2d13781a77dd99afd215f5ee5677b62cc4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="ispunct-iswpunct-ispunctl-iswpunctl"></a>ispunct、iswpunct、_ispunct_l、_iswpunct_l

判斷整數是否代表標點符號字元。

## <a name="syntax"></a>語法

```C
int ispunct(
   int c
);
int iswpunct(
   wint_t c
);
int _ispunct_l(
   int c,
   _locale_t locale
);
int _iswpunct_l(
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

每個這些常式傳回非零，如果*c*是以標點符號字元的特定表示法。 **ispunct**傳回非零的值不是空格字元或字元的任何可列印字元**isalnum**為非零值。 **iswpunct**傳回非零值對於任何可列印的寬字元不空格寬字元和寬字元的**iswalnum**為非零值。 這些常式都會傳回 0，如果*c*不符合測試條件。

測試條件的結果**ispunct**函式取決於**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 不需要這些函式的版本 **_l**針對任何地區設定相關行為的後置詞使用目前的地區設定; 沒有版本 **_l**尾碼是一樣的不同之處在於會使用改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

行為**ispunct**和 **_ispunct_l**是未定義的如果*c*不 EOF 或 0 到 0xFF，（含) 範圍中。 當使用 CRT 偵錯程式庫和*c*不是其中一個函式產生，這些值的判斷提示。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**iswpunct**|\<ctype.h> 或 \<wchar.h>|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
