---
title: strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
ms.date: 11/04/2016
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: 411fe3a5a6f66614f0a22e0f623b73685a6e0844
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957612"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l

根據地區設定特定資訊轉換字串。

## <a name="syntax"></a>語法

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*strDest*<br/>
目的字串。

*strSource*<br/>
來源字串。

*計數*<br/>
要放在*strDest*中的最大字元數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回已轉換字串的長度，不計入結束的 Null 字元。 如果傳回值大於或等於*count*， *strDest*的內容就會無法預測。 發生錯誤時，每個函式都會設定**errno** ，並傳回**INT_MAX**。 若為不正確字元， **errno**會設為**EILSEQ**。

## <a name="remarks"></a>備註

**Strxfrm**函式會將*strSource*所指向的字串轉換成儲存在*strDest*中的新分頁格式。 不超過*計數*字元（包含 null 字元）會轉換並放入結果字串中。 轉換是使用地區設定的**LC_COLLATE**類別設定進行。 如需**LC_COLLATE**的詳細資訊，請參閱[setlocale](setlocale-wsetlocale.md)。 **strxfrm**會針對其地區設定相關的行為使用目前的地區設定; **_strxfrm_l**是相同的，不同之處在于它會使用傳入的地區設定，而不是目前的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

轉換之後，使用兩個已轉換字串呼叫**strcmp** ，會產生與套用至原始兩個字串的**strcoll**呼叫相同的結果。 如同**strcoll**和**stricoll**， **strxfrm**會視需要自動處理多位元組字元字串。

**wcsxfrm**是寬字元版本的**strxfrm**;**wcsxfrm**的字串引數是寬字元指標。 針對**wcsxfrm**，在字串轉換之後，以兩個已轉換字串呼叫**wcscmp** ，會產生與套用至原始兩個字串的**wcscoll**呼叫相同的結果。 相反地， **wcsxfrm**和**strxfrm**的行為相同。 **wcsxfrm**會針對其地區設定相關的行為使用目前的地區設定; **_wcsxfrm_l**會使用傳入的地區設定，而不是目前的地區設定。

這些函式會驗證它們的參數。 如果*strSource*為 null 指標，或*strDest*為**null**指標（除非 count 為零），或如果*count*大於**INT_MAX**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，並傳回**INT_MAX**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

在 "C" 地區設定中，字元集 (ASCII 字元集) 的字元順序與字元的詞典編纂順序相同。 不過，其他地區設定中，字元集的字元順序可能與詞典編纂字元順序不同。 例如，在某些歐洲地區設定中，字元 ' a ' （值0x61）在字元 ' &\#x00E4; ' 之前（值0xE4）在字元集中，但字元 ' ä ' 在字元 ' a ' 詞典編纂之前。

在字元集和詞典編纂字元順序不同的地區設定中，對原始字串使用**strxfrm** ，然後在產生的字串上**strcmp** ，以根據目前地區設定來產生詞典編纂字串比較**LC_COLLATE**類別設定。 因此，若要比較上述地區設定中詞典編纂的兩個字串，請在原始字串上使用**strxfrm** ，然後在產生的字串上**strcmp** 。 或者，您可以在原始字串上使用**strcoll** ，而不是**strcmp** 。

**strxfrm**基本上是使用**LCMAP_SORTKEY** [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw)的包裝函式。

下列運算式的值是保存來源字串之**strxfrm**轉換所需的陣列大小：

`1 + strxfrm( NULL, string, 0 )`

只有在 "C" 地區設定中， **strxfrm**相當於下列內容：

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> 或 \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
