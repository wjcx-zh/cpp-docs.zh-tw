---
title: strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
ms.date: 4/2/2020
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
- _o__strxfrm_l
- _o__wcsxfrm_l
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: aabe7e7c2e44f558b936e0fd4c6fa4a85dc582f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362976"
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

*斯特德斯特*<br/>
目的字串。

*strSource*<br/>
來源字串。

*count*<br/>
要放置在*strD*中的最大字元數。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回已轉換字串的長度，不計入結束的 Null 字元。 如果返回值大於或等於*計數*,*則 strDest*的內容是不可預知的。 在錯誤時,每個函數設定**errno**並傳回**INT_MAX**。 對合法的字元 **,errno**設定為**EILSEQ**。

## <a name="remarks"></a>備註

**strxfrm**函數將*strSource*指向的字串轉換為存儲在*strD 中*的新整理形式。 不會超過*計數*字元(包括空字元)被轉換並放入生成的字串中。 轉換使用區域**設置LC_COLLATE類別**設置。 關於**LC_COLLATE**的詳細資訊,請參考[設定本地端設定](setlocale-wsetlocale.md)。 **strxfrm**使用當前區域設置作為其與區域設置相關的行為;**_strxfrm_l**是相同的,只不過它使用傳入區域設置而不是當前區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

轉換後,使用兩個轉換的字串進行**strcmp**的調用會產生與應用於原始兩個字串的**strcoll**調用的結果相同。 與**strcoll**和**stricoll**一樣 **,strxfrm**可根據需要自動處理多位元組位元串。

**wcsxfrm**是一個寬字元版本的**strxfrm**;**wcsxfrm**的字串參數是寬字元指標。 對於**wcsxfrm,** 在字串轉換後,使用兩個轉換的字串對**wcscmp**的調用會產生與應用於原始兩個字串的**wcscoll**調用的結果相同。 **wcsxfrm**和**strxfrm**行為相同。否則。 **wcsxfrm**使用當前區域設置來進行與區域設置相關的行為;**_wcsxfrm_l**使用傳入區域設置而不是當前區域設置。

這些函式會驗證它們的參數。 如果*strSource*是空指標,或者*strDest*是**NULL**指標(除非*計數*為零),或者計數大於**INT_MAX,** 則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**errno**設定為**EINVAL**並傳回**INT_MAX**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

在 "C" 地區設定中，字元集 (ASCII 字元集) 的字元順序與字元的詞典編纂順序相同。 不過，其他地區設定中，字元集的字元順序可能與詞典編纂字元順序不同。 例如,在某些歐洲區域設置中,字元"a"(值 0x61)位於字元"&\#x00E4;"字元集中(值 0xE4),但字元"*"在字元"a"的字典中前面。

在字串集和詞典字元順序不同的區域設定中,在原始字串上使用**strxfrm,** 然後在生成的字串上**strcmp**根據目前區域設定**LC_COLLATE**類別設置生成字典字串比較。 因此,要在上述區域設置中按字典方式比較兩個字串,請使用原始字串上的**strxfrm,** 然後在生成的字串上**串。** 或者,您可以使用**strcoll,** 而不是在原始字串上 **。**

**strxfrm**基本上是一個包裝圍繞[LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw)與**LCMAP_SORTKEY。**

以下表示式的值是儲存原始碼字串的**strxfrm**轉換所需的陣列的大小:

`1 + strxfrm( NULL, string, 0 )`

僅在「C」區域設定中 **,strxfrm**等效於以下內容:

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
[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
