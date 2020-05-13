---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
ms.openlocfilehash: 712313314c67d15987326e3e3a920cd5f1039239
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913882"
---
# <a name="_umask_s"></a>_umask_s

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

如果*模式*未指定有效的模式，或*POldMode*指標為**Null**，則會傳回錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*mode*|*pOldMode*|傳回值|*POldMode*的內容|
|------------|----------------|----------------------|--------------------------------|
|任意|**Null**|**EINVAL**|未修改|
|無效的模式|任意|**EINVAL**|未修改|

如果發生上述其中一種狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **_umask_s**會傳回**EINVAL** ，並將**errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**_Umask_s**函式會將目前進程的檔案許可權遮罩，設定為*模式*所指定的模式。 檔案許可權遮罩會修改 **_creat**、 **_open**或 **_sopen**所建立之新檔案的許可權設定。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。

整數運算式*pmode*包含下列其中一個或兩個在 SYS\STAT. 中定義的資訊清單常數。H

|*pmode*||
|-|-|
|**_S_IWRITE**|允許寫入。|
|**_S_IREAD**|允許讀取。|
|**_S_IREAD** \| **_S_IWRITE**|允許讀取和寫入。|

當同時指定兩個常數時，會使用位 OR 運算子（ **|** ）聯結。 如果 _S_IREAD*模式*引數 **_S_IREAD**，則不允許讀取（檔案為僅限寫入）。 如果 _S_IWRITE*模式*引數 **_S_IWRITE**，則不允許寫入（檔案是唯讀的）。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，使用 **_umask_s**設定讀取位不會影響檔案的模式。

如果*pmode*不是其中一個資訊清單常數的組合，或包含一組替代的常數，則此函式會直接忽略它們。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
