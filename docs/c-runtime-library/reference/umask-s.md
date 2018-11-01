---
title: _umask_s
ms.date: 11/04/2016
apiname:
- _umask_s
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
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: 878a22cb2884c36e792ff8dead1453582addb5b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480662"
---
# <a name="umasks"></a>_umask_s

設定預設檔案權限遮罩。 這是 [_umask](umask.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>參數

*mode*<br/>
預設權限設定。

*pOldMode*<br/>
權限設定的先前值。

## <a name="return-value"></a>傳回值

如果傳回的錯誤碼*模式*未指定有效的模式或*pOldMode*指標**NULL**。

### <a name="error-conditions"></a>錯誤狀況

|*mode*|*pOldMode*|傳回值|內容*pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|any|**NULL**|**EINVAL**|未修改|
|無效的模式|any|**EINVAL**|未修改|

如果發生上述其中一種狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續，請執行 **_umask_s**會傳回**EINVAL**並設定**errno**至**EINVAL**。

## <a name="remarks"></a>備註

**_Umask_s**函式所指定的模式會設定目前的處理序的檔案權限遮罩*模式*。 將檔案權限遮罩會修改所建立的新檔案的權限設定 **_creat**， **_open**，或 **_sopen**。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。

整數運算式*pmode*包含一或兩個下列資訊清單常數，SYS\STAT 中定義。H:

|*pmode*||
|-|-|
|**_S_IWRITE**|允許寫入|
|**_S_IREAD**|允許讀取。|
|**_S_IREAD** \| **_S_IWRITE**|允許讀取和寫入。|

它們兩個常數指定時，會使用位元 OR 運算子結合 ( **|** )。 如果*模式*引數是 **_S_IREAD**，則不允許讀取 （此檔案是唯寫）。 如果*模式*引數是 **_S_IWRITE**，則不允許寫入 （此檔案是唯讀）。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，設定讀取位元 **_umask_s**對檔案的模式沒有任何作用。

如果*pmode*不是其中一個資訊清單常數的組合或包含另一組常數，此函式只會忽略這些。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_umask_s**|\<io.h> 和 \<sys/stat.h> 和 \<sys/types.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
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
[_umask](umask.md)<br/>
