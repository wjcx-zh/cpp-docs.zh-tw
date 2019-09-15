---
title: iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l
ms.date: 11/04/2016
api_name:
- iscntrl
- _iswcntrl_l
- _iscntrl_l
- iswcntrl
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
- _istcntrl_l
- _iswcntrl_l
- iswcntrl
- _iscntrl_l
- iscntrl
- _istcntrl
helpviewer_keywords:
- iscntrl function
- _iscntrl_l function
- _iswcntrl_l function
- _istcntrl function
- istcntrl function
- iswcntrl function
- _istcntrl_l function
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
ms.openlocfilehash: 302c357c054ad58043b00875d629ae70e5a23e0e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954439"
---
# <a name="iscntrl-iswcntrl-_iscntrl_l-_iswcntrl_l"></a>iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l

判斷整數是否代表控制字元。

## <a name="syntax"></a>語法

```C
int iscntrl(
   int c
);
int iswcntrl(
   wint_t c
);
int _iscntrl_l(
   int c,
   _locale_t locale
);
int _iswcntrl_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果*c*是特定的控制字元標記法，則每個常式都會傳回非零。 如果*c*是控制字元（0X00-0X1F 或0x7f）， **iscntrl**會傳回非零值。 如果*c*是控制寬字元，則**iswcntrl**會傳回非零值。 如果*c*不符合測試條件，這些常式都會傳回0。

這些具有 **_l**尾碼的函式版本會使用傳入的地區設定參數，而不是目前的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或範圍0到0xff （含），則**iscntrl**和 **_iscntrl_l**的行為是未定義的。 當使用 debug CRT 程式庫，而*c*不是其中一個值時，函數會引發判斷提示。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istcntrl**|**iscntrl**|**iscntrl**|**iswcntrl**|
|**_istcntrl_l**|**_iscntrl_l**|**_iscntrl_l**|**_iswcntrl_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**iscntrl**|\<ctype.h>|
|**iswcntrl**|\<ctype.h> 或 \<wchar.h>|
|**_iscntrl_l**|\<ctype.h>|
|**_iswcntrl_l**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
