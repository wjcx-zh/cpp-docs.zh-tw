---
title: _umask | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: f2ad9c75caa5f3816ab4791dc4e67cb7937bfad4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="umask"></a>_umask
設定預設檔案權限遮罩。 目前有比這個函式更安全的版本；請參閱 [_umask_s](../../c-runtime-library/reference/umask-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
int _umask(  
   int pmode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `pmode`  
 預設權限設定。  
  
## <a name="return-value"></a>傳回值  
 `_umask` 會傳回 `pmode` 的先前值。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 `_umask`函式所指定的模式會將目前的處理序的檔案權限遮罩`pmode`。 檔案權限遮罩會修改 `_creat`、`_open` 或 `_sopen` 所建立之新檔案的權限設定。 如果遮罩中的位元為 1，則會將檔案的要求權限值中的對應位元設定為 0 (不允許)。 如果遮罩中的位元為 0，對應的位元會保持不變。 新檔案的權限設定要一直到第一次關閉檔案時才會設定。  
  
 整數運算式 `pmode` 包含 SYS\STAT.H 中所定義的下列其中一或兩個資訊清單常數：  
  
 `_S_IWRITE`  
 允許寫入。  
  
 `_S_IREAD`  
 允許讀取。  
  
 `_S_IREAD | _S_IWRITE`  
 允許讀取和寫入。  
  
 指定兩個常數時，會使用位元 OR 運算子加以結合 ( `|`)。 如果 `pmode` 引數是 `_S_IREAD`，則不允許讀取 (此檔案是唯寫)。 如果 `pmode` 引數是 `_S_IWRITE`，則不允許寫入 (此檔案是唯讀)。 比方說，如果遮罩中設定了寫入位元，任何新的檔案將會是唯讀。 請注意，在 MS-DOS 和 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，使用 `_umask` 設定讀取位元對於檔案的模式沒有作用。  
  
 如果 `pmode` 不是其中一個資訊清單常數的組合或包含另一組常數，則此函式只會忽略這些項目。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_umask`|\<io.h>、\<sys/stat.h>、\<sys/types.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
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
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [低層級 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)
