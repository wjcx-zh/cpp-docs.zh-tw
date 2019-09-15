---
title: toupper、_toupper、towupper、_toupper_l、_towupper_l
ms.date: 11/04/2016
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
- towupper
- _toupper
- _totupper
- toupper
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
ms.openlocfilehash: e17f139789b2c37292764f2e4508b59cddd2c03e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957911"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper、_toupper、towupper、_toupper_l、_towupper_l

將字元轉換為大寫。

## <a name="syntax"></a>語法

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
要轉換的字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

每一個常式都會轉換*c*的複本（如果可能的話），並傳回結果。

如果*c*是寬字元，其中的**iswlower**為非零值，而且有對應的寬字元，而其[iswupper](isupper-isupper-l-iswupper-iswupper-l.md)為非零值，則**towupper**會傳回對應的寬字元;否則， **towupper**會傳回未變更的*c* 。

沒有表示錯誤的保留傳回值。

為了讓**toupper**提供預期的結果， [__isascii](isascii-isascii-iswascii.md)和[islower](islower-iswlower-islower-l-iswlower-l.md)都必須傳回非零值。

## <a name="remarks"></a>備註

這些常式都會將指定的小寫字母轉換為大寫字母 (如果可能且適當的話)。 **Towupper**的大小寫轉換是地區設定特有的。 只有與目前地區設定相關字元的大小寫會變更。 沒有 **_l**尾碼的函式會使用目前設定的地區設定。 這些具有 **_l**尾碼的函式版本採用地區設定作為參數，並使用它，而不是目前設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

為了讓**toupper**提供預期的結果， [__isascii](isascii-isascii-iswascii.md)和[isupper](isupper-isupper-l-iswupper-iswupper-l.md)都必須傳回非零值。

[資料轉換常式](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l**和 **_towupper_l**沒有地區設定相依性，因此不應該直接呼叫。 其提供供 **_totupper_l**內部使用。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [to 函式](../../c-runtime-library/to-functions.md)中的範例。

## <a name="see-also"></a>另請參閱

[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函式](../../c-runtime-library/to-functions.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
