---
title: _strdup、_wcsdup、_mbsdup
ms.date: 4/2/2020
api_name:
- _strdup
- _mbsdup
- _wcsdup
- _o__strdup
- _o__wcsdup
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
ms.openlocfilehash: 7ad28633844c49ce5b86c8f71f4502c62eba1216
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359697"
---
# <a name="_strdup-_wcsdup-_mbsdup"></a>_strdup、_wcsdup、_mbsdup

重複字串。

> [!IMPORTANT]
> **_mbsdup**不能在 Windows 運行時中執行的應用程式中使用。 有關詳細資訊,請參閱通用[Windows 平台應用中不支援的 CRT 功能](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

如果無法分配存儲,則每個函數都會返回指向複製字串的儲存位置的指標或**NULL。**

## <a name="remarks"></a>備註

**_strdup**函數調用[malloc](malloc.md)為*strSource*的副本分配存儲空間,然後將*strSource*複製到分配的空間。

**_wcsdup**和 **_mbsdup**是寬字元和多位元組字元版本的 **_strdup。** **_wcsdup**的參數和返回值是寬字元字串;**_mbsdup**字串是多位元位元串。 除此之外，這三個函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup**|**_strdup**|**_mbsdup**|**_wcsdup**|

由於 **_strdup**調用**malloc**為*strSource*的副本分配存儲空間,因此最好始終通過在調用 **_strdup**返回的指標上調用[空閒](free.md)例程來釋放此記憶體。

如果定義了 **_DEBUG**和 **_CRTDBG_MAP_ALLOC,****則_strdup**和 **_wcsdup**將替換為對 **_strdup_dbg**和 **_wcsdup_dbg**的調用,以允許調試記憶體分配。 如需詳細資訊，請參閱 [_strdup_dbg、_wcsdup_dbg](strdup-dbg-wcsdup-dbg.md)。

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

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
