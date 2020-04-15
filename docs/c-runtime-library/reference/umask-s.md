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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362184"
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

*模式*<br/>
預設權限設定。

*pOldMode*<br/>
權限設定的先前值。

## <a name="return-value"></a>傳回值

如果*模式*未指定有效模式或*pOldMode*指標為**NULL,** 則傳回錯誤程式碼。

### <a name="error-conditions"></a>錯誤狀況

|*模式*|*pOldMode*|傳回值|*pOldMode*的內容|
|------------|----------------|----------------------|--------------------------------|
|任意|**空**|**埃因瓦爾**|未修改|
|無效的模式|任意|**埃因瓦爾**|未修改|

如果發生上述其中一種狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,_umask_s**傳回**EINVAL**並將**errno**設定到**EINVAL**。

## <a name="remarks"></a>備註

**_umask_s**函數將目前進程的檔案許可權掩碼設定為*模式*指定的模式。 檔案許可權掩碼修改由 **_creat、_open**或 **_sopen**創建 **_open**的新檔案的許可權設置。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。

整數運算式*pmode*包含以下一個或兩個清單常量,在 SYS_STAT 中定義。H:

|*pmode*||
|-|-|
|**_S_IWRITE**|允許寫入。|
|**_S_IREAD**|允許讀取。|
|**_S_IREAD** \| _S_IREAD_S_IWRITE **_S_IWRITE**|允許讀取和寫入。|

當兩個常量都給出時,它們與位-OR 運算符 ()**|** 聯接。 如果*模式*參數**為_S_IREAD,** 則不允許讀取(該檔僅寫入)。 如果*模式*參數**是_S_IWRITE,** 則不允許寫入(該檔是唯讀的)。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此,使用 **_umask_s**設置讀取位對檔模式沒有影響。

如果*pmode*不是清單常量之一的組合,或者合併了一組備用常量,則函數將忽略這些常量。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
