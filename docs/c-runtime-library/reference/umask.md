---
title: _umask
description: _Umask 的 API 參考;設定預設檔案許可權遮罩的。
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3735ecd7ba194009945d3717982d7828ecee3c1e
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554925"
---
# <a name="_umask"></a>_umask

設定預設檔案權限遮罩。 請參閱 [_umask_s](umask-s.md) ，以取得更安全的此函式版本。」

## <a name="syntax"></a>語法

```C
int _umask( int pmode );
```

### <a name="parameters"></a>參數

*pmode*<br/>
預設權限設定。

## <a name="return-value"></a>傳回值

**_umask** 傳回先前的 *pmode*值。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Umask**函式會將目前進程的檔案許可權遮罩設定為*pmode*所指定的模式。 檔案許可權遮罩會修改 **_creat**、 **_open**或 **_sopen**所建立之新檔案的許可權設定。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。

整數運算式 *pmode* 包含下列其中一個或兩個定義于 SYS\STAT. 中的資訊清單常數：H：

|*pmode*| |
|-|-|
| **_S_IWRITE** | 允許寫入。 |
| **_S_IREAD** | 允許讀取。 |
| **_S_IREAD** &#124; **_S_IWRITE** | 允許讀取和寫入。 |

當同時指定兩個常數時，它們會與位 OR 運算子聯結 ( **&#124;** ) 。 如果 _S_IREAD *pmode*引數 **_S_IREAD**，則不允許讀取 (檔案僅限寫入) 。 如果 _S_IWRITE *pmode*引數 **_S_IWRITE**，則不允許寫入 (檔案是唯讀) 。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，使用 **_umask** 設定讀取位不會影響檔案的模式。

如果 *pmode* 不是其中一個資訊清單常數的組合或包含另一組常數，則此函式只會忽略這些常數。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

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
[低層級 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
