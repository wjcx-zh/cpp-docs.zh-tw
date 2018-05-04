---
title: _unlink、_wunlink | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _unlink
- _wunlink
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tunlink
- _unlink
- wunlink
- _wunlink
dev_langs:
- C++
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ace694452467d6d559f8820216be71ecd85b54e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="unlink-wunlink"></a>_unlink、_wunlink

刪除檔案。

## <a name="syntax"></a>語法

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>參數

*filename*<br/>
要移除之檔案的名稱。

## <a name="return-value"></a>傳回值

如果成功，所有這些函式都會傳回 0。 否則，此函數會傳回-1 和集合**errno**至**EACCES**，這表示路徑指定唯讀的檔案，或**ENOENT**，這表示檔案或路徑找不到或指定目錄的路徑。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Unlink**函式會刪除所指定的檔案*filename*。 **_wunlink**是寬字元版本的 **_unlink**; *filename*引數 **_wunlink**是寬字元字串。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_unlink**|\<io.h> 和 \<stdio.h>|
|**_wunlink**|\<io.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="code-example"></a>程式碼範例

此程式會使用 _unlink 來刪除 CRT_UNLINK.TXT。

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crtunlinktxt"></a>輸入︰crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>範例輸出

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove0、_wremove](remove-wremove.md)<br/>
