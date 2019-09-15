---
title: isblank、iswblank、_isblank_l、_iswblank_l
ms.date: 11/04/2016
api_name:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: 022eba0335facc597f0608d63cfb58e0146e0f23
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954510"
---
# <a name="isblank-iswblank-_isblank_l-_iswblank_l"></a>isblank、iswblank、_isblank_l、_iswblank_l

判斷整數是否代表空白字元。

## <a name="syntax"></a>語法

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
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

如果*c*是特定的空格或水準索引標籤字元的標記法，則每個常式都會傳回非零，或者是用來分隔文字行內之單字的地區設定特定字元集之一。 如果*c*是空白字元（0x20）或水準定位字元（0x09）， **isblank**會傳回非零值。 **Isblank**函式測試條件的結果取決於地區設定的**LC_CTYPE**分類設定;如需詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md)。 這些沒有 **_l**尾碼的函式版本，會針對任何與地區設定相關的行為使用目前的地區設定;具有 **_l**尾碼的版本是相同的，不同之處在于它們會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*c*是對應至標準空格或水準定位字元的寬字元，則**iswblank**會傳回非零值。

如果*c*不是 EOF 或範圍0到0xff （含），則**isblank**和 **_isblank_l**的行為是未定義的。 當使用 debug CRT 程式庫，而*c*不是其中一個值時，函數會引發判斷提示。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<ctype.h> 或 \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
