---
title: memmove_s、wmemmove_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wmemmove_s
- memmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wmemmove_s
- memmove_s
dev_langs:
- C++
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39fde456dd2e45d38bdd1b6ba8d9d7eb9811dd05
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403891"
---
# <a name="memmoves-wmemmoves"></a>memmove_s、wmemmove_s

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

*count*<br/>
位元組數目 (**memmove_s**) 或字元 (**wmemmove_s**) 複製。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼

### <a name="error-conditions"></a>錯誤狀況

|*dest*|*numberOfElements*|*src*|傳回值|內容*目的地*|
|------------|------------------------|-----------|------------------|------------------------|
|**NULL**|任何|任何|**EINVAL**|未修改|
|任何|任何|**NULL**|**EINVAL**|未修改|
|任何|< *計數*|任何|**ERANGE**|未修改|

## <a name="remarks"></a>備註

複製*計數*位元組的字元從*src*至*目的地*。 如果來源區域和目的地的某些區域重疊， **memmove_s**可確保在重疊的區域中的原始來源位元組會複製之前遭到覆寫。

如果*目的地*或*src*為 null 指標，或如果目的字串太小，這些函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md) . 如果允許繼續執行，這些函數會傳回**EINVAL**並設定**errno**至**EINVAL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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

### <a name="output"></a>輸出

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
