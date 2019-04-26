---
title: _umask
ms.date: 11/04/2016
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
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: 113bf97b0fe93204cd41de20bc36a8be080a88b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155416"
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

**_umask**會傳回先前的值*pmode*。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Umask**函式所指定的模式會設定目前的處理序的檔案權限遮罩*pmode*。 將檔案權限遮罩會修改所建立的新檔案的權限設定 **_creat**， **_open**，或 **_sopen**。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。

整數運算式*pmode*包含一或兩個下列資訊清單常數，SYS\STAT 中定義。H:

|*pmode*| |
|-|-|
| **_S_IWRITE** | 允許寫入 |
| **_S_IREAD** | 允許讀取。 |
| **_S_IREAD** &#124; **_S_IWRITE** | 允許讀取和寫入。 |

它們兩個常數指定時，會使用位元 OR 運算子結合 ( **&#124;** )。 如果*pmode*引數是 **_S_IREAD**，則不允許讀取 （此檔案是唯寫）。 如果*pmode*引數是 **_S_IWRITE**，則不允許寫入 （此檔案是唯讀）。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，設定讀取位元 **_umask**對檔案的模式沒有任何作用。

如果*pmode*不是其中一個資訊清單常數的組合或包含另一組常數，此函式只會忽略這些。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
