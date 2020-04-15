---
title: _strninc、_wcsninc、_mbsninc、_mbsninc_l
ms.date: 4/2/2020
api_name:
- _mbsninc
- _mbsninc_l
- _wcsninc
- _strninc
- _o__mbsninc
- _o__mbsninc_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strninc
- wcsninc
- mbsninc_l
- _strninc
- _tcsninc
- mbsninc
- _mbsninc_l
- _ftcsninc
- _wcsninc
- _mbsninc
helpviewer_keywords:
- _mbsninc_l function
- mbsninc function
- _strninc function
- tcsninc function
- wcsninc function
- _mbsninc function
- strninc function
- _wcsninc function
- mbsninc_l function
- _tcsninc function
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
ms.openlocfilehash: 297d2fdf940ab81a3d636d4726e6e6a345ce5c02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364485"
---
# <a name="_strninc-_wcsninc-_mbsninc-_mbsninc_l"></a>_strninc、_wcsninc、_mbsninc、_mbsninc_l

將字串指標前進為**n**個字元。

> [!IMPORTANT]
> **_mbsninc****和_mbsninc_l**不能在Windows運行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *_strninc(
   const char *str,
   size_t count
);
wchar_t *_wcsninc(
   const wchar_t *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*Str*<br/>
來源字串。

*count*<br/>
字串指標要遞增的字元數。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果提供的指標為**NULL,** 則每個例程在*str*以*計數*字元或**NULL**增量後傳回一個指向*str 的*指標。 如果*計數*大於或等於*str*中的字元數,則結果未定義。

## <a name="remarks"></a>備註

**_mbsninc**函數按*計數*多位元位元元組 *。* **_mbsninc**根據當前使用的[多位元組代碼頁](../../c-runtime-library/code-pages.md)識別多位元組字串序列。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsninc**|**_strninc**|**_mbsninc**|**_wcsninc**|

**_strninc**與 **_wcsninc**是單位元位元串和寬字元字串版本 **_mbsninc**。 **_wcsninc**和 **_strninc**僅為此映射提供,否則不應使用。 如需詳細資訊，請參閱[使用泛型文字對應](../../c-runtime-library/using-generic-text-mappings.md)以及[泛型文字對應](../../c-runtime-library/generic-text-mappings.md)。

**_mbsninc_l**是相同的,只是它使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsninc**|\<mbstring.h>|
|**_mbsninc_l**|\<mbstring.h>|
|**_strninc**|\<tchar.h>|
|**_wcsninc**|\<tchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec、_wcsdec、_mbsdec、_mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc、_wcsinc、_mbsinc、_mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
