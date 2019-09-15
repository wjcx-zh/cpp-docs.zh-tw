---
title: strcat、wcscat、_mbscat
ms.date: 11/04/2016
api_name:
- _mbscat
- wcscat
- strcat
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscat
- _ftcscat
- _tcscat
- strcat
- wcscat
helpviewer_keywords:
- concatenating strings
- mbscat function
- _ftcscat function
- _tcscat function
- ftcscat function
- strcat function
- strings [C++], appending
- _mbscat function
- tcscat function
- strings [C++], concatenating
- appending strings
- wcscat function
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
ms.openlocfilehash: 973c54c18e941b29526cb3e9b1cadb98f6582c4a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958267"
---
# <a name="strcat-wcscat-_mbscat"></a>strcat、wcscat、_mbscat

附加字串。 這些函式已有更安全的版本可供使用，請參閱 [strcat_s、wcscat_s、_mbscat_s](strcat-s-wcscat-s-mbscat-s.md)。

> [!IMPORTANT]
> **_mbscat_s**無法在 Windows 執行階段中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *strcat(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscat(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscat(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcat(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscat(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscat(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>參數

*strDestination*<br/>
以 Null 終止的目的地字串。

*strSource*<br/>
以 Null 結束的來源字串。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回目的地字串（*strDestination*）。 未保留表示錯誤的傳回值。

## <a name="remarks"></a>備註

**Strcat**函數會將*StrSource*附加至*strDestination* ，並以 null 字元終止產生的字串。 *StrSource*的初始字元會覆寫*strDestination*的終止 null 字元。 如果來源和目的字串重迭，則**strcat**的行為是未定義的。

> [!IMPORTANT]
> 因為**strcat**在附加*strSource*之前，不會在*strDestination*中檢查是否有足夠的空間，所以可能會造成緩衝區溢位。 請考慮改用 [strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)。

**wcscat**和 **_mbscat**是**strcat**的寬字元和多位元組字元版本。 **Wcscat**的引數和傳回值是寬字元字串; **_mbscat**的是多位元組字元字串。 除此之外，這三個函式的行為相同。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat**|**strcat**|**_mbscat**|**wcscat**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strcat**|\<string.h>|
|**wcscat**|\<string.h> 或 \<wchar.h>|
|**_mbscat**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [strcpy](strcpy-wcscpy-mbscpy.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
