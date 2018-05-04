---
title: remove、_wremove | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wremove
- remove
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
- remove
- _wremove
- _tremove
dev_langs:
- C++
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36cdc09107a66067b358cb2fd72ec9bd1b2b30a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="remove-wremove"></a>remove0、_wremove

刪除檔案。

## <a name="syntax"></a>語法

```C
int remove(
   const char *path
);
int _wremove(
   const wchar_t *path
);
```

### <a name="parameters"></a>參數

*path*<br/>
要移除之檔案的路徑。

## <a name="return-value"></a>傳回值

如果已成功刪除檔案，這些函式每個都會傳回 0。 否則，它會傳回-1，並設定**errno**至**EACCES**指示路徑指定唯讀檔案或檔案已經開啟，或**ENOENT**表示找不到檔案名稱或路徑，或路徑指定的目錄。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**remove** 函式會刪除 *path* 指定的檔案。 **_wremove**是寬字元版本的**移除 （_r)**;*路徑*引數 **_wremove**是寬字元字串。 **_wremove**和**移除 （_r)** 除此之外的行為相同。 必須先關閉檔案的所有處理常式，才能刪除它。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tremove**|**remove**|**remove**|**_wremove**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**remove**|\<stdio.h> 或 \<io.h>|
|**_wremove**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_remove.c
/* This program uses remove to delete crt_remove.txt */

#include <stdio.h>

int main( void )
{
   if( remove( "crt_remove.txt" ) == -1 )
      perror( "Could not delete 'CRT_REMOVE.TXT'" );
   else
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );
}
```

### <a name="input-crtremovetxt"></a>輸入︰crt_remove.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>範例輸出

```Output
Deleted 'CRT_REMOVE.TXT'
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_unlink、_wunlink](unlink-wunlink.md)<br/>
