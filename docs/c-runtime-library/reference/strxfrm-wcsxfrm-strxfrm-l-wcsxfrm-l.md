---
title: strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
ms.date: 11/04/2016
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
ms.openlocfilehash: 4e4f5bb6639cbeee0f004f94f09177c08394d43e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258711"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l

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

*count*<br/>
要置於的字元數目上限*strDest*。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回已轉換字串的長度，不計入結束的 Null 字元。 傳回的值是否大於或等於*計數*，則內容*strDest*無法預期。 發生錯誤時，設定每個函式**errno** ，然後傳回**INT_MAX**。 無效的字元，如**errno**設為**EILSEQ**。

## <a name="remarks"></a>備註

**Strxfrm**所指向的字串的函式轉換*strSource*到新的定序中所儲存的格式*strDest*。 不能超過*計數*字元，包括 null 字元，轉換並放入結果字串。 使用的地區設定來進行轉換**LC_COLLATE**分類設定。 如需詳細資訊**LC_COLLATE**，請參閱[setlocale](setlocale-wsetlocale.md)。 **strxfrm**針對與其地區設定相關行為; 會使用目前的地區設定 **_strxfrm_l**完全相同，不同之處在於它會使用傳入，而不是目前的地區設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在轉換之後，呼叫**strcmp**具有兩個已轉換的字串會產生完全相同的呼叫結果**strcoll**套用至原始兩個字串。 如同**strcoll**並**stricoll**， **strxfrm**會自動處理為適當的多位元組字元字串。

**wcsxfrm**是寬字元版本的**strxfrm**; 的字串引數**wcsxfrm**是寬字元指標。 針對**wcsxfrm**之後，字串轉換，呼叫**wcscmp**使用兩個已轉換的字串會產生完全相同的呼叫結果**wcscoll**套用至原始的兩個字串。 **wcsxfrm**並**strxfrm**行為相同。 **wcsxfrm**針對與其地區設定相關行為; 會使用目前的地區設定 **_wcsxfrm_l**使用而不是目前的地區設定傳入的地區設定。

這些函式會驗證它們的參數。 如果*strSource*為 null 指標，或*strDest*會**NULL**指標 （除非計數為零），或如果*計數*大於**INT_MAX**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md) 。 如果允許繼續執行，這些函式會將**errno**要**EINVAL** ，並傳回**INT_MAX**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

在 "C" 地區設定中，字元集 (ASCII 字元集) 的字元順序與字元的詞典編纂順序相同。 不過，其他地區設定中，字元集的字元順序可能與詞典編纂字元順序不同。 比方說，某些歐洲的地區設定中的字元 'a' （值 0x61） 前面的字元 ' &\#x00E4;'（值 0xE4） 中的字元集，但字元 'ä' 前面的字元 'a' 依辭典編纂順序。

中的字元集和詞典編纂字元順序不同的地區設定，使用**strxfrm**對原始字串，然後**strcmp**上產生的字串，以產生詞典編纂字串根據目前的地區設定的比較**LC_COLLATE**分類設定。 因此，若要比較上述地區設定中，依辭典編纂順序的兩個字串，請使用**strxfrm**對原始字串，然後**strcmp**產生的字串。 或者，您可以使用**strcoll**而非**strcmp**對原始字串。

**strxfrm**基本上是一個包裝函式[LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa)具有**LCMAP_SORTKEY**。

下列運算式的值是陣列保留所需的大小**strxfrm**轉換來源字串：

`1 + strxfrm( NULL, string, 0 )`

在"C"地區設定中， **strxfrm**就相當於下列：

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
