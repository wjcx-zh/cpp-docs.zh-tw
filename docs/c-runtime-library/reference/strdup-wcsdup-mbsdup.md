---
title: _strdup、_wcsdup、_mbsdup
ms.date: 11/04/2016
api_name:
- _strdup
- _mbsdup
- _wcsdup
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
- _tcsdup
- mbsdup
- _mbsdup
- _strdup
- _ftcsdup
- _wcsdup
helpviewer_keywords:
- wcsdup function
- ftcsdup function
- _ftcsdup function
- mbsdup function
- strdup function
- _strdup function
- _wcsdup function
- copying strings
- duplicating strings
- strings [C++], copying
- _mbsdup function
- strings [C++], duplicating
- tcsdup function
- _tcsdup function
ms.assetid: 8604f8bb-95e9-45d3-93ef-20397ebf247a
ms.openlocfilehash: c96e0a8f9f72b811f891217deabe758626b03186
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958185"
---
# <a name="_strdup-_wcsdup-_mbsdup"></a>_strdup、_wcsdup、_mbsdup

重複字串。

> [!IMPORTANT]
> **_mbsdup**無法在 Windows 執行階段中執行的應用程式中使用。 如需詳細資訊，請參閱[通用 Windows 平臺應用程式中不支援的 CRT](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)函式。

## <a name="syntax"></a>語法

```C
char *_strdup(
   const char *strSource
);
wchar_t *_wcsdup(
   const wchar_t *strSource
);
unsigned char *_mbsdup(
   const unsigned char *strSource
);
```

### <a name="parameters"></a>參數

*strSource*<br/>
以 Null 結束的來源字串。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回所複製字串之儲存位置的指標，如果無法配置儲存區，則傳回**Null** 。

## <a name="remarks"></a>備註

**_Strdup**函數會呼叫[Malloc](malloc.md)來配置*strSource*複本的儲存空間，然後將*strSource*複製到已配置的空間。

**_wcsdup**和 **_mbsdup**是 **_strdup**的寬字元和多位元組字元版本。 **_Wcsdup**的引數和傳回值是寬字元字串; **_mbsdup**的是多位元組字元字串。 除此之外，這三個函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup**|**_strdup**|**_mbsdup**|**_wcsdup**|

由於 **_strdup**會呼叫**Malloc**來配置*strSource*複本的儲存空間，因此最好一律在呼叫 **_strdup**所傳回的指標上呼叫[free](free.md)常式來釋放這個記憶體。

如果已定義 **_debug**和 **_CRTDBG_MAP_ALLOC** ，則 **_strdup**和 **_wcsdup**會被呼叫 **_strdup_dbg**和 **_wcsdup_dbg**取代，以允許進行記憶體配置的偵測。 如需詳細資訊，請參閱 [_strdup_dbg, _wcsdup_dbg](strdup-dbg-wcsdup-dbg.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strdup**|\<string.h>|
|**_wcsdup**|\<string.h> 或 \<wchar.h>|
|**_mbsdup**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strdup.c

#include <string.h>
#include <stdio.h>

int main( void )
{
   char buffer[] = "This is the buffer text";
   char *newstring;
   printf( "Original: %s\n", buffer );
   newstring = _strdup( buffer );
   printf( "Copy:     %s\n", newstring );
   free( newstring );
}
```

```Output
Original: This is the buffer text
Copy:     This is the buffer text
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
