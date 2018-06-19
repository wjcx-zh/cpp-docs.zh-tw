---
title: _umask | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _umask
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
- _umask
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3053bfb19cc81dff15d41d1b5bc6d405da619f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412611"
---
# <a name="umask"></a>_umask

設定預設檔案權限遮罩。 目前有比這個函式更安全的版本；請參閱 [_umask_s](umask-s.md)。

## <a name="syntax"></a>語法

```C
int _umask( int pmode );
```

### <a name="parameters"></a>參數

*pmode*<br/>
預設權限設定。

## <a name="return-value"></a>傳回值

**_umask**傳回先前的值*pmode*。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Umask**函式所指定的模式會將目前的處理序的檔案權限遮罩*pmode*。 建立的新檔案的權限設定會修改檔案權限遮罩 **_creat**， **_open**，或 **_sopen**。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。

整數運算式*pmode*包含一或兩個下列資訊清單常數，SYS\STAT 中定義。H:

|*pmode*||
|-|-|
**_S_IWRITE**|允許寫入
**_S_IREAD**|允許讀取。
**_S_IREAD** \| **_S_IWRITE**|允許讀取和寫入。

當兩個常數時，其是否加入位元 OR 運算子 ( **|** )。 如果*pmode*引數是 **_S_IREAD**，不允許讀取 （檔案是唯寫）。 如果*pmode*引數是 **_S_IWRITE**，不允許寫入 （檔案是唯讀的）。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，會設定位元讀取 **_umask**不有任何影響檔案的模式。

如果*pmode*不是組合資訊清單常數之一，或納入另外組的常數，此函式會直接略過這些。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_umask**|\<io.h>、\<sys/stat.h>、\<sys/types.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
