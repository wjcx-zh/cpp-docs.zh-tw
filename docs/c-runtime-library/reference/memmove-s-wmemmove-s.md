---
title: memmove_s、wmemmove_s
ms.date: 11/04/2016
api_name:
- wmemmove_s
- memmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: bc932bb0b13289349543d042e02ead884921d00a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951786"
---
# <a name="memmove_s-wmemmove_s"></a>memmove_s、wmemmove_s

將某個緩衝區移到另一個緩衝區。 這些是 [memmove、wmemmove](memmove-wmemmove.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t memmove_s(
   void *dest,
   size_t numberOfElements,
   const void *src,
   size_t count
);
errno_t wmemmove_s(
   wchar_t *dest,
   size_t numberOfElements,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>參數

*dest*<br/>
目的地物件。

*numberOfElements*<br/>
目的緩衝區大小。

*src*<br/>
來源物件。

*計數*<br/>
要複製的位元組數目（**memmove_s**）或字元數（**wmemmove_s**）。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼

### <a name="error-conditions"></a>錯誤狀況

|*dest*|*numberOfElements*|*src*|傳回值|*Dest*的內容|
|------------|------------------------|-----------|------------------|------------------------|
|**NULL**|any|any|**EINVAL**|未修改|
|any|any|**NULL**|**EINVAL**|未修改|
|any|< *計數*|any|**ERANGE**|未修改|

## <a name="remarks"></a>備註

將字元的*計數*位元組從*src*複製到*dest*。 如果來源區域與目的地的某些區域重迭， **memmove_s**會確保重迭區域中的原始來源位元組會在覆寫之前複製。

如果*dest*或*src*是 null 指標，或如果目的字串太小，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回**EINVAL** ，並將**Errno**設定為**EINVAL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**memmove_s**|\<string.h>|
|**wmemmove_s**|\<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_memmove_s.c
//
// The program demonstrates the
// memmove_s function which works as expected
// for moving overlapping regions.

#include <stdio.h>
#include <string.h>

int main()
{
   char str[] = "0123456789";

   printf("Before: %s\n", str);

   // Move six bytes from the start of the string
   // to a new position shifted by one byte. To protect against
   // buffer overrun, the secure version of memmove requires the
   // the length of the destination string to be specified.

   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);

   printf_s(" After: %s\n", str);
}
```

### <a name="output"></a>Output

```Output
Before: 0123456789
After: 0012345789
```

## <a name="see-also"></a>另請參閱

[緩衝區操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy、wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
