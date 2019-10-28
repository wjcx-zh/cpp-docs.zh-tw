---
title: _strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l
ms.date: 11/04/2016
api_name:
- _strncoll
- _mbsncoll_l
- _wcsncoll
- _wcsncoll_l
- _mbsncoll
- _strncoll_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: e5120b37cd06266752194ec826a173474f6902fd
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947268"
---
# <a name="_strncoll-_wcsncoll-_mbsncoll-_strncoll_l-_wcsncoll_l-_mbsncoll_l"></a>_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l

使用地區設定特定資訊，以比較字串。

> [!IMPORTANT]
> **_mbsncoll**和 **_mbsncoll_l**不能在 Windows 執行階段中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*string1*、 *string2*<br/>
以 Null 結束的待比較字串。

*計數*<br/>
要比較的字元數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回一個值，指出*string1*和*string2*子字串的關聯性，如下所示。

|傳回值|string1 與 string2 的關係|
|------------------|----------------------------------------|
|< 0|*string1*小於*string2*。|
|0|*string1*與*string2*相同。|
|> 0|*string1*大於*string2*。|

所有這些函式都會傳回 **_NLSCMPERROR**。 若要使用 **_NLSCMPERROR**，請包含字串 .H 或 g。 如果*string1*或*string2*包含定序順序之網域以外的寬字元碼，則 **_wcsncoll**可能會失敗。 發生錯誤時， **_wcsncoll**可能會將**Errno**設定為**EINVAL**。 若要在呼叫 **_wcsncoll**時檢查是否發生錯誤，請將**errno**設定為0，然後在呼叫 **_wcsncoll**之後檢查**errno** 。

## <a name="remarks"></a>備註

所有這些函式都會根據目前使用中的字碼頁，對*string1*和*string2*中的第一個*計數*字元執行區分大小寫的比較。 只有在字元集順序與字碼頁中的字典編撰字元順序不同時，以及字串比較注意這項差異時，才使用這些函式。 字元集順序是地區設定相關。 這些沒有 **_l**尾碼的函式版本會使用目前的地區設定，但具有 **_l**尾碼的版本會使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

這些函式全都會驗證它們的參數。 如果*string1*或*string2*是 null 指標，或*count*大於**INT_MAX**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 **_NLSCMPERROR** ，並將**Errno**設定為**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccoll**|**_strncoll**|**_mbsncoll**|**_wcsncoll**|
|**_tcsncoll**|**_strncoll**|[_mbsnbcoll](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|**_wcsncoll**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strncoll**、 **_strncoll_l**|\<string.h>|
|**_wcsncoll**、 **_wcsncoll_l**|\<wchar.h> 或 \<string.h>|
|**_mbsncoll**、 **_mbsncoll_l**|\<mbstring.h>|

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
