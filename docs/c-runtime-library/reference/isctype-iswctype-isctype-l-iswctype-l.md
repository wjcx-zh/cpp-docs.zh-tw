---
title: _isctype、iswctype、_isctype_l、_iswctype_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
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
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
dev_langs:
- C++
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 25df7ddaaea8c1f4df0907ebd92827f2a4865007
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="isctype-iswctype-isctypel-iswctypel"></a>_isctype、iswctype、_isctype_l、_iswctype_l

測試*c* ctype 屬性所指定*desc*引數。 針對每一個有效值的*desc*，沒有對等的寬字元分類常式。

## <a name="syntax"></a>語法

```C
int _isctype(
   int c,
   _ctype_t desc
);
int _isctype_l(
   int c,
   _ctype_t desc,
   _locale_t locale
);
int iswctype(
   wint_t c,
   wctype_t desc
);
int _iswctype_l(
   wint_t c,
   wctype_t desc,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

*desc*<br/>
需要測試的屬性。 這通常使用 ctype 或 [wctype](wctype.md) 擷取。

*locale*<br/>
針對任何地區設定相關測試所使用的地區設定。

## <a name="return-value"></a>傳回值

**_isctype**和**iswctype**傳回非零值，如果*c*具有所指定的屬性*desc*中目前的地區設定或 0，如果不存在。 這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳入的地區設定而不是目前的地區設定的地區設定相關的行為。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

行為 **_isctype**和 **_isctype_l**是未定義的如果*c*不 EOF 或 0 到 0xFF，（含) 範圍中。 當使用 CRT 偵錯程式庫和*c*不是其中一個函式產生，這些值的判斷提示。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|N/A|**_isctype**|N/A|**_iswctype**|
|N/A|**_isctype_l**|N/A|**_iswctype_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_isctype**|\<ctype.h>|
|**iswctype**|\<ctype.h> 或 \<wchar.h>|
|**_isctype_l**|\<ctype.h>|
|**_iswctype_l**|\<ctype.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
