---
title: isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l
ms.date: 11/04/2016
api_name:
- _iswxdigit_l
- iswxdigit
- isxdigit
- _isxdigit_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswxdigit
- isxdigit
- _istxdigit
helpviewer_keywords:
- isxdigit function
- istxdigit function
- _iswxdigit_l function
- _istxdigit function
- _isxdigit_l function
- iswxdigit_l function
- isxdigit_l function
- hexadecimal characters
- iswxdigit function
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
ms.openlocfilehash: 18f360e66583dfbf5033f813deed0b56abc71260
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953582"
---
# <a name="isxdigit-iswxdigit-_isxdigit_l-_iswxdigit_l"></a>isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l

判斷整數是否為代表十六進位數字的字元。

## <a name="syntax"></a>語法

```C
int isxdigit(
   int c
);
int iswxdigit(
   wint_t c
);
int _isxdigit_l(
   int c,
   _locale_t locale
);
int _iswxdigit_l(
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

如果*c*是十六進位數位的特定標記法，則每個常式都會傳回非零。 如果*c*是十六進位數位（a-f、a-f 或 0-9）， **isxdigit**會傳回非零值。 如果*c*是對應至十六進位數位字元的寬字元，則**iswxdigit**會傳回非零值。 如果*c*不符合測試條件，這些常式都會傳回0。

對於 "C" 地區設定， **iswxdigit**函數不支援 Unicode 全形十六進位字元。

這些具有 **_l**尾碼的函式版本，會使用傳入的地區設定，而不是與地區設定相關行為的目前地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或範圍0到0xff （含），則**isxdigit**和 **_isxdigit_l**的行為是未定義的。 當使用 debug CRT 程式庫，而*c*不是其中一個值時，函數會引發判斷提示。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istxdigit**|**isxdigit**|**isxdigit**|**iswxdigit**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**isxdigit**|\<ctype.h>|
|**iswxdigit**|\<ctype.h> 或 \<wchar.h>|
|**_isxdigit_l**|\<ctype.h>|
|**_iswxdigit_l**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
