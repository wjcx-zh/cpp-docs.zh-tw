---
title: rename、_wrename
ms.date: 4/2/2020
api_name:
- rename
- _wrename
- _o__wrename
- _o_rename
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wrename
- _trename
- Rename
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
ms.openlocfilehash: 730458c5027f8f690e8238b29cbdb1056f09ed68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338109"
---
# <a name="rename-_wrename"></a>rename、_wrename

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

*新名稱*<br/>
新名稱的指標。

## <a name="return-value"></a>傳回值

如果成功，這些函式每個都會傳回 0。 在錯誤時,函數傳回非零值,並將**errno**設定到以下值之一:

|errno 值|條件|
|-|-|
| **EACCES** | *newname* 指定的檔案或目錄已經存在，或無法建立 (無效的路徑)；或 *oldname* 是目錄，且 *newname* 指定不同的路徑。 |
| **埃諾恩特** | 找不到 *oldname* 指定的檔案或路徑。 |
| **埃因瓦爾** | 名稱包含無效的字元。 |

如需其他可能的傳回值，請參閱 [_doserrno、_errno、syserrlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**rename** 函式會將由 *oldname* 指定的檔案或目錄重新命名為由 *newname* 指定的名稱。 舊名稱必須是現有的檔案或目錄的路徑。 新名稱不得是現有的檔案或目錄的名稱。 您可以使用 **rename** 將檔案從一個目錄或裝置移到另一個，方法是在 *newname* 引數中提供不同的路徑。 不過，您無法使用 **rename** 移動目錄。 目錄可以重新命名，但不能移動。

**_wrename**是 **_rename**的寬字元版本;要 **_wrename**的參數是寬字元字串。 **_wrename**和 **_rename**行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**重新命名**|**重新命名**|**_wrename**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**重新命名**|\<io.h> 或 \<stdio.h>|
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
