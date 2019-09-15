---
title: strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l
ms.date: 11/04/2016
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
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
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: 7519b8f41d77ed668bb7da1e8ced18ee13c0a5bf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957885"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l

使用目前的地區設定或指定的 LC_COLLATE 轉換狀態分類來比較字串。

> [!IMPORTANT]
> **_mbscoll**和 **_mbscoll_l**不能在 Windows 執行階段中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*string1*、 *string2*<br/>
以 Null 結束的待比較字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回一個值，指出*string1*到*string2*的關聯性，如下所示。

|傳回值|string1 與 string2 的關係|
|------------------|----------------------------------------|
|< 0|*string1*小於*string2*|
|0|*string1*與*string2*相同|
|> 0|*string1*大於*string2*|

這些函式每一個都會在發生錯誤時傳回 **_NLSCMPERROR** 。 若要使用 **_NLSCMPERROR**，請包含其中一個字串。H 或 G.。H. 如果*string1*或*string2*是**Null** ，或包含定序順序之網域以外的寬字元碼，則**wcscoll**可能會失敗。 發生錯誤時， **wcscoll**可能會將**Errno**設定為**EINVAL**。 若要在呼叫**wcscoll**時檢查是否發生錯誤，請將**errno**設定為0，然後在呼叫**wcscoll**之後檢查**errno** 。

## <a name="remarks"></a>備註

所有這些函式都會根據目前使用中的字碼頁，執行*string1*和*string2*的區分大小寫比較。 只有在字元集順序與目前字碼頁中的字典編纂字元順序不同時，以及字串比較注意這項差異時，才應該使用這些函式。

這些函式全都會驗證它們的參數。 如果*string1*或*string2*是 null 指標，或*count*大於**INT_MAX**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 **_NLSCMPERROR** ，並將**Errno**設定為**EINVAL**。

這兩個字串的比較是與地區設定相關的作業，因為每個地區設定都有不同的字元排序規則。 這些沒有 **_l**尾碼的函式版本，會針對此與地區設定相關的行為使用目前線程的地區設定;具有 **_l**後置字元的版本與對應的函式完全相同，但不含尾碼，不同之處在于它們會使用當做參數傳入的地區設定，而不是目前的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<wchar.h>、\<string.h>|
|**_mbscoll**、 **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>、\<string.h>|

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
