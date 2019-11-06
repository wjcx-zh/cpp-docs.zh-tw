---
title: _CrtSetDebugFillThreshold
description: 使用 _CrtSetDebugFillThreshold 函數來設定要填入安全 CRT 函式的最大緩衝區數量。
ms.date: 10/31/2019
api_name:
- _CrtSetDebugFillThreshold
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetDebugFillThreshold
- CrtSetDebugFillThreshold
helpviewer_keywords:
- debug, buffer-filling behavior
- CrtSetDebugFillThreshold function
- _CrtSetDebugFillThreshold function
- buffer-filling behavior
- 0xFE
ms.assetid: 6cb360e8-56ae-4248-b17f-e28aee3e0ed7
ms.openlocfilehash: 3fdf6646603a59e8a7a2387600060ab3a3556b37
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624401"
---
# <a name="_crtsetdebugfillthreshold"></a>_CrtSetDebugFillThreshold

擷取或修改控制偵錯函式中緩衝區填入行為的臨界值。

## <a name="syntax"></a>語法

```C
size_t _CrtSetDebugFillThreshold( size_t newThreshold );
```

### <a name="parameters"></a>參數

*newThreshold*<br/>
新的閾值大小（以位元組為單位）。

## <a name="return-value"></a>傳回值

先前的臨界值。

## <a name="remarks"></a>備註

某些安全性增強 CRT 函式的 debug 版本會以特殊字元（0xFE）填入傳遞給它們的緩衝區。 這個填滿字元有助於找出將錯誤大小傳遞給函式的情況。 可惜的是，它也會降低效能。 若要改善效能，請使用 **_CrtSetDebugFillThreshold**來停用大於*newThreshold*臨界值之緩衝區的緩衝區填滿。 *NewThreshold*值為0時，會將它停用於所有緩衝區。

預設閾值為**SIZE_T_MAX**。

以下是受影響的函式清單。

- [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)

- [_cgets_s、_cgetws_s](cgets-s-cgetws-s.md)

- [_ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)

- [_ecvt_s](ecvt-s.md)

- [_fcvt_s](fcvt-s.md)

- [_gcvt_s](gcvt-s.md)

- [_itoa_s、_ltoa_s、_ultoa_s、_i64toa_s、_ui64toa_s、_itow_s、_ltow_s、_ultow_s、_i64tow_s、_ui64tow_s](itoa-s-itow-s.md)

- [_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)

- [_mbsnbcat_s、_mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)

- [_mbsnbcpy_s、_mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)

- [_mbsnbset_s、_mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md)

- [_mktemp_s、_wmktemp_s](makepath-s-wmakepath-s.md)

- [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)

- [strcat_s、wcscat_s、_mbscat_s](strcat-s-wcscat-s-mbscat-s.md)

- [strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)

- [_strdate_s、_wstrdate_s](strdate-s-wstrdate-s.md)

- [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md)

- [_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)

- [strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)

- [strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)

- [_strnset_s、_strnset_s_l、_wcsnset_s、_wcsnset_s_l、_mbsnset_s、_mbsnset_s_l](strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md)

- [_strset_s、_strset_s_l、_wcsset_s、_wcsset_s_l、_mbsset_s、_mbsset_s_l](strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md)

- [_strtime_s、_wstrtime_s](strtime-s-wstrtime-s.md)

- [_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtSetDebugFillThreshold**|\<crtdbg.h>|

此函式是 Microsoft 特有的功能。 如需相容性的詳細資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限[C 執行時間程式庫](../../c-runtime-library/crt-library-features.md)的 Debug 版本。

## <a name="example"></a>範例

```C
// crt_crtsetdebugfillthreshold.c
// compile with: cl /MTd crt_crtsetdebugfillthreshold.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <crtdbg.h>

void Clear( char buff[], size_t size )
{
   for( int i=0; i<size; ++i )
      buff[i] = 0;
}

void Print( char buff[], size_t size )
{
   for( int i=0; i<size; ++i )
      printf( "%02x  %c\n", (unsigned char)buff[i], buff[i] );
}

int main( void )
{
   char buff[10];

   printf( "With buffer-filling on:\n" );
   strcpy_s( buff, _countof(buff), "howdy" );
   Print( buff, _countof(buff) );

   _CrtSetDebugFillThreshold( 0 );

   printf( "With buffer-filling off:\n" );
   Clear( buff, _countof(buff) );
   strcpy_s( buff, _countof(buff), "howdy" );
   Print( buff, _countof(buff) );
}
```

```Output
With buffer-filling on:
68  h
6f  o
77  w
64  d
79  y
00
fe  ■
fe  ■
fe  ■
fe  ■
With buffer-filling off:
68  h
6f  o
77  w
64  d
79  y
00
00
00
00
00
```

## <a name="see-also"></a>請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
