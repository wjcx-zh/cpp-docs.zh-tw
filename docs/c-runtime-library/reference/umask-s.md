---
title: _umask_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _umask_s
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
dev_langs: C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71279b111e50c40bb974d9a5da68b575aecc1ebc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="umasks"></a>_umask_s
設定預設檔案權限遮罩。 這是 [_umask](../../c-runtime-library/reference/umask.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _umask_s(  
   int mode,  
   int * pOldMode  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `mode`  
 預設權限設定。  
  
 [輸出] `oldMode`  
 權限設定的先前值。  
  
## <a name="return-value"></a>傳回值  
 如果 `Mode` 未指定有效的模式或 `pOldMode` 指標是 `NULL`，則傳回錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`mode`|`pOldMode`|**傳回值**|`oldMode` **的內容**。|  
|------------|----------------|----------------------|--------------------------------|  
|any|`NULL`|`EINVAL`|未修改|  
|無效的模式|any|`EINVAL`|未修改|  
  
 如果發生上述其中一種狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`_umask_s` 會傳回 `EINVAL`，且 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_umask_s`函式所指定的模式會將目前的處理序的檔案權限遮罩`mode`。 檔案權限遮罩會修改 `_creat`、`_open` 或 `_sopen` 所建立之新檔案的權限設定。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。  
  
 整數運算式 `pmode` 包含 SYS\STAT.H 中所定義的下列其中一或兩個資訊清單常數：  
  
 `_S_IWRITE`  
 允許寫入  
  
 `_S_IREAD`  
 允許讀取。  
  
 `_S_IREAD | _S_IWRITE`  
 允許讀取和寫入。  
  
 指定兩個常數時，會使用位元 OR 運算子加以結合 ( `|`)。 如果 `mode` 引數是 `_S_IREAD`，則不允許讀取 (此檔案是唯寫)。 如果 `mode` 引數是 `_S_IWRITE`，則不允許寫入 (此檔案是唯讀)。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，使用 `_umask_s` 設定讀取位元對於檔案的模式沒有作用。  
  
 如果 `pmode` 不是其中一個資訊清單常數的組合或包含另一組常數，則此函式只會忽略這些項目。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_umask_s`|\<io.h> 和 \<sys/stat.h> 和 \<sys/types.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [低層級 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_umask](../../c-runtime-library/reference/umask.md)