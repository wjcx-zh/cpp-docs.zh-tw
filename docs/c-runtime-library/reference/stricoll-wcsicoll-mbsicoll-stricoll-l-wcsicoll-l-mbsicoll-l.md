---
title: _stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
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
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
dev_langs:
- C++
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f90f6a25c6ecf6796ba3d4d94b6d2f5722eabf9d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416368"
---
# <a name="stricoll-wcsicoll-mbsicoll-stricolll-wcsicolll-mbsicolll"></a>_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l

使用地區設定特定資訊，以比較字串。

> [!IMPORTANT]
> **_mbsicoll**和 **_mbsicoll_l**不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _stricoll(
   const char *string1,
   const char *string2
);
int _wcsicoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*string1*， *string2*<br/>
以 Null 結束的待比較字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

所有這些函式傳回值，指出關聯性的*string1*至*string2*、，如下所示。

|傳回值|string1 與 string2 的關係|
|------------------|----------------------------------------|
|< 0|*string1*小於*string2*|
|0|*string1*等於*string2*|
|> 0|*string1*大於*string2*|
|**_NLSCMPERROR**|發生錯誤。|

所有這些函式傳回 **_NLSCMPERROR**。 若要使用 **_NLSCMPERROR**，包含\<h > 或\<m >。 **_wcsicoll**就會失敗可能是*string1*或*string2*包含定序順序之網域外部的寬字元碼。 發生錯誤時， **_wcsicoll**可能設定**errno**至**EINVAL**。 若要檢查是否有錯誤的呼叫上 **_wcsicoll**，將**errno**設為 0，然後檢查**errno**之後呼叫 **_wcsicoll**。

## <a name="remarks"></a>備註

所有這些函式執行不區分大小寫的比較*string1*和*string2*根據目前使用中的字碼頁。 只有在字元集順序與目前字碼頁中的字典編纂字元順序不同時，以及字串比較注意這項差異時，才應該使用這些函式。

**_stricmp**不同於 **_stricoll**在於 **_stricmp**比較會受到**LC_CTYPE**，而 **_stricoll**比較根據**LC_CTYPE**和**LC_COLLATE**之地區設定的類別。 如需有關**LC_COLLATE**類別目錄，請參閱[setlocale](setlocale-wsetlocale.md)和[地區設定分類](../../c-runtime-library/locale-categories.md)。 這些功能，但不包含新版 **_l**後置詞使用目前的地區設定; 具有版本 **_l**尾碼是一樣的只不過它們改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

這些函式全都會驗證它們的參數。 如果有任一個*string1*或*string2*是**NULL**無效參數處理常式的指標，會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md). 如果允許繼續執行，這些函數會傳回 **_NLSCMPERROR**並設定**errno**至**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_stricoll**， **_stricoll_l**|\<string.h>|
|**_wcsicoll**， **_wcsicoll_l**|\<wchar.h>、\<string.h>|
|**_mbsicoll**， **_mbsicoll_l**|\<mbstring.h>|

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
