---
title: _stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l
ms.date: 4/2/2020
api_name:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
- _o__mbsicoll
- _o__mbsicoll_l
- _o__stricoll
- _o__stricoll_l
- _o__wcsicoll
- _o__wcsicoll_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: d726d2d33f8f775d09e6197dfeda6abb91106a53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355332"
---
# <a name="_stricoll-_wcsicoll-_mbsicoll-_stricoll_l-_wcsicoll_l-_mbsicoll_l"></a>_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l

使用地區設定特定資訊，以比較字串。

> [!IMPORTANT]
> **_mbsicoll**和 **_mbsicoll_l**不能在 Windows 運行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*字串1*,*字串2*<br/>
以 Null 結束的待比較字串。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

每個函數返回一個值,指示*string1*到*string2*的關係,如下所示。

|傳回值|string1 與 string2 的關係|
|------------------|----------------------------------------|
|< 0|*字串1*小於*字串2*|
|0|*字串1*與*字串2*相同|
|> 0|*字串1*大於*字串2*|
|**_NLSCMPERROR**|發生錯誤。|

這些函數中的每一個都**傳回_NLSCMPERROR**。 要使用 **_NLSCMPERROR**\<,請包括 string.h \<> 或 mbstring.h>。 如果*string1*或*string2*在整理序列的域之外包含寬字元代碼,**則_wcsicoll**可能會失敗。 發生錯誤時 **,_wcsicoll**可能會將**errno**設定為**EINVAL**。 要檢查呼叫 **_wcsicoll**時的錯誤,請將**errno**設置為0,然後在調用 **_wcsicoll**後檢查**errno。**

## <a name="remarks"></a>備註

根據當前使用的代碼頁,每個函數都執行對*string1*和*string2*不區分大小寫的比較。 只有在字元集順序與目前字碼頁中的字典編纂字元順序不同時，以及字串比較注意這項差異時，才應該使用這些函式。

**_stricmp_stricoll****_stricoll**不同 **,_stricmp**比較受**LC_CTYPE**影響,而 **_stricoll**比較則根據區域設置**LC_CTYPE**和**LC_COLLATE**類別。 關於**LC_COLLATE**類別的詳細資訊,請參考[設定區域設定](setlocale-wsetlocale.md)[與區域設定類別](../../c-runtime-library/locale-categories.md)。 沒有 **_l**後綴的這些函數的版本使用當前區域設置;具有 **_l**後綴的版本是相同的,只是它們使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

這些函式全都會驗證它們的參數。 如果*string1*或*string2*是**NULL**指標,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**傳回_NLSCMPERROR**並將**errno**設定為**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_stricoll**, **_stricoll_l**|\<string.h>|
|**_wcsicoll**, **_wcsicoll_l**|\<wchar.h>、\<string.h>|
|**_mbsicoll**, **_mbsicoll_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md)<br/>
[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
