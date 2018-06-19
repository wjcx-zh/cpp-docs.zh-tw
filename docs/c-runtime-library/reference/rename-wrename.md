---
title: rename、 _wrename | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rename
- _wrename
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
- _wrename
- _trename
- Rename
dev_langs:
- C++
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f02829b394649b86dfda9baad7c5792853fce746
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407469"
---
# <a name="rename-wrename"></a>rename、_wrename

重新命名檔案或目錄。

## <a name="syntax"></a>語法

```C
int rename(
   const char *oldname,
   const char *newname
);
int _wrename(
   const wchar_t *oldname,
   const wchar_t *newname
);
```

### <a name="parameters"></a>參數

*oldname*<br/>
舊名稱的指標。

*newname*<br/>
新名稱的指標。

## <a name="return-value"></a>傳回值

如果成功，這些函式每個都會傳回 0。 發生錯誤時，此函數會傳回非零值，並設定**errno**至下列值之一：

|errno 值|條件|
|-|-|
**EACCES**|*newname* 指定的檔案或目錄已經存在，或無法建立 (無效的路徑)；或 *oldname* 是目錄，且 *newname* 指定不同的路徑。
**ENOENT**|找不到 *oldname* 指定的檔案或路徑。
**EINVAL**|名稱包含無效的字元。

如需其他可能的傳回值，請參閱 [_doserrno、_errno、syserrlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**rename** 函式會將由 *oldname* 指定的檔案或目錄重新命名為由 *newname* 指定的名稱。 舊名稱必須是現有的檔案或目錄的路徑。 新名稱不得是現有的檔案或目錄的名稱。 您可以使用 **rename** 將檔案從一個目錄或裝置移到另一個，方法是在 *newname* 引數中提供不同的路徑。 不過，您無法使用 **rename** 移動目錄。 目錄可以重新命名，但不能移動。

**_wrename**是寬字元版本的 **_rename**; 的引數 **_wrename**是寬字元字串。 **_wrename**和 **_rename**除此之外的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**rename**|**rename**|**_wrename**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**rename**|\<io.h> 或 \<stdio.h>|
|**_wrename**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_renamer.c
/* This program attempts to rename a file named
* CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation
* to succeed, a file named CRT_RENAMER.OBJ must exist and
* a file named CRT_RENAMER.JBO must not exist.
*/

#include <stdio.h>

int main( void )
{
   int  result;
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";

   /* Attempt to rename file: */
   result = rename( old, new );
   if( result != 0 )
      printf( "Could not rename '%s'\n", old );
   else
      printf( "File '%s' renamed to '%s'\n", old, new );
}
```

### <a name="output"></a>輸出

```Output
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
