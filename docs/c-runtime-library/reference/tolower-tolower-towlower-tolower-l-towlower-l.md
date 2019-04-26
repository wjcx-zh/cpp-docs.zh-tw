---
title: tolower、_tolower、towlower、_tolower_l、_towlower_l
ms.date: 11/04/2016
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
ms.openlocfilehash: f7d017235eddb19b08353dceb332a2721e7434aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155509"
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower、_tolower、towlower、_tolower_l、_towlower_l

將字元轉換為小寫。

## <a name="syntax"></a>語法

```C
int tolower(
   int c
);
int _tolower(
   int c
);
int towlower(
   wint_t c
);
int _tolower_l(
   int c,
   _locale_t locale
);
int _towlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
要轉換的字元。

*locale*<br/>
要用於地區設定特定翻譯的地區設定。

## <a name="return-value"></a>傳回值

這些常式都會將一份*c*至較低的情況下，如果轉換是可行的並傳回結果。 沒有表示錯誤的保留傳回值。

## <a name="remarks"></a>備註

這些常式都會將指定的大寫字母轉換為小寫字母 (如果可能且相關的話)。 大小寫轉換**towlower**地區設定而定。 只有與目前地區設定相關字元的大小寫會變更。 沒有函式 **_l**後置詞使用目前設定的地區設定。 有這些函式的版本 **_l**尾碼採用的地區設定做為參數，並使用，而不是目前設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

為了讓 **_tolower**預期的結果，提供給[__isascii](isascii-isascii-iswascii.md)並[isupper](isupper-isupper-l-iswupper-iswupper-l.md)必須都傳回非零值。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l**並 **_towlower_l**沒有任何地區設定相依性，不是直接呼叫。 它們專供內部使用 **_totlower_l**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [to 函式](../../c-runtime-library/to-functions.md)中的範例。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函式](../../c-runtime-library/to-functions.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
