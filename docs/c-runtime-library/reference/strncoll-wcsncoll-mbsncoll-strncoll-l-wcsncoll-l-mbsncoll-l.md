---
title: _strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l
ms.date: 11/04/2016
apiname:
- _strncoll
- _mbsncoll_l
- _wcsncoll
- _wcsncoll_l
- _mbsncoll
- _strncoll_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsncoll_l
- strncoll
- _wcsncoll
- _tcsnccoll
- _ftcsnccoll
- wcsncoll
- _mbsncoll
- wcsncoll_l
- strncoll_l
- _ftcsncoll
- _strncoll
- _tcsncoll
- mbsncoll
helpviewer_keywords:
- _strncoll_l function
- code pages, using for string comparisons
- _strncoll function
- _mbsncoll function
- ftcsncoll function
- strncoll function
- _ftcsncoll function
- strncoll_l function
- wcsncoll function
- mbsncoll function
- _tcsncoll function
- _tcsnccoll function
- wcsncoll_l function
- tcsnccoll function
- mbsncoll_l function
- _mbsncoll_l function
- tcsncoll function
- _wcsncoll function
- strings [C++], comparing by code page
- _ftcsnccoll function
- ftcsnccoll function
- _wcsncoll_l function
ms.assetid: e659a5a4-8afe-4033-8e72-17ffd4bdd8e9
ms.openlocfilehash: fe6c3283c9379b370911cc63184535e813b96d8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658532"
---
# <a name="strncoll-wcsncoll-mbsncoll-strncolll-wcsncolll-mbsncolll"></a>_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l

使用地區設定特定資訊，以比較字串。

> [!IMPORTANT]
> **_mbsncoll**並 **_mbsncoll_l**不能在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _strncoll(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsncoll(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strncoll_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsncoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsncoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*string1*， *string2*<br/>
以 Null 結束的待比較字串。

*count*<br/>
要比較的字元數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回值，指出子字串的關聯性*string1*並*string2*、，如下所示。

|傳回值|string1 與 string2 的關係|
|------------------|----------------------------------------|
|< 0|*string1*是小於*string2*。|
|0|*string1*等同於*string2*。|
|> 0|*string1*大於*string2*。|

每一種函式都會傳回 **_NLSCMPERROR**。 若要使用 **_NLSCMPERROR**，包括 STRING.h 或 MBSTRING.h。 **_wcsncoll**可能會失敗，如果有任一*string1*或*string2*包含之網域外部的定序順序的寬字元碼。 發生錯誤時， **_wcsncoll**可能設定**errno**來**EINVAL**。 若要檢查是否發生錯誤，在呼叫 **_wcsncoll**，將**errno**設為 0，然後再檢查**errno**呼叫之後 **_wcsncoll**。

## <a name="remarks"></a>備註

所有這些函式都會執行區分大小寫比較的第一個*計數*中的字元*string1*並*string2*，根據在目前的字碼頁使用。 只有在字元集順序與字碼頁中的字典編撰字元順序不同時，以及字串比較注意這項差異時，才使用這些函式。 字元集順序是地區設定相關。 不需要這些函式的版本 **_l**後置詞使用目前的地區設定，但具有 **_l**後置詞使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

這些函式全都會驗證它們的參數。 如果有任一*string1*或*string2*為 null 指標，或*計數*大於**INT_MAX**，會叫用無效參數處理常式，中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則這些函式會傳回 **_NLSCMPERROR**並設定**errno**來**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccoll**|**_strncoll**|**_mbsncoll**|**_wcsncoll**|
|**_tcsncoll**|**_strncoll**|[_mbsnbcoll](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|**_wcsncoll**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strncoll**， **_strncoll_l**|\<string.h>|
|**_wcsncoll**， **_wcsncoll_l**|\<wchar.h> 或 \<string.h>|
|**_mbsncoll**， **_mbsncoll_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md)<br/>
[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
