---
title: "_futime、_futime32、_futime64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- futime
- _futime
- futime64
- _futime64
dev_langs:
- C++
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: fe4ae59495ecea19dc14424bd4787db5decfac18
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="futime-futime32-futime64"></a>_futime、_futime32、_futime64
設定已開啟之檔案的修改時間。  
  
## <a name="syntax"></a>語法  
  
```  
int _futime(   
   int fd,  
   struct _utimbuf *filetime   
);  
int _futime32(   
   int fd,  
   struct __utimbuf32 *filetime   
);  
int _futime64(   
   int fd,  
   struct __utimbuf64 *filetime   
);  
```  
  
#### <a name="parameters"></a>參數  
 `fd`  
 已開啟之檔案的檔案描述元。  
  
 `filetime`  
 包含新修改日期之結構的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 0。 發生錯誤時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函數會傳回-1 和`errno`設`EBADF`，表示無效的檔案描述元，或`EINVAL`，指出不正確的參數。  
  
## <a name="remarks"></a>備註  
 `_futime`常式設定上開啟的檔案與相關聯的修改日期和存取時間`fd`。 `_futime` 等同於 [_utime](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)，不同之處在於其引數是開啟之檔案的檔案描述元，而不是檔案的名稱或檔案的路徑。 `_utimbuf` 結構包含新修改日期和存取時間的欄位。 這兩個欄位必須包含有效的值。 `_utimbuf32` 和 `_utimbuf64` 等於 `_utimbuf` 除了其分別使用 32 位元和 64 位元的階段類型。 `_futime` 和 `_utimbuf` 使用 64 位元的階段類型，而 `_futime` 的行為與 `_futime64` 完全相同。 如果您需要強制進行舊行為，請定義 `_USE_32BIT_TIME_T`。 如此一來，會導致 `_futime` 的行為與 `_futime32` 完全相同，並造成 `_utimbuf` 結構使用 32 位元的階段類型，使其相當於 `__utimbuf32`。  
  
 使用 `__utimbuf64` 結構的 `_futime64`，可以讀取和修改檔案日期至 3000 年 12 月 31 日 23:59:59 UTC，而呼叫 `_futime32` 時，如果檔案的日期晚於 2038 年 1 月 18 日 23:59:59 UTC 就會失敗。 1970 年 1 月 1 日午夜是這些函式的日期範圍下限。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|選擇性標頭|  
|--------------|---------------------|---------------------|  
|`_futime`|\<sys/utime.h>|\<errno.h>|  
|`_futime32`|\<sys/utime.h>|\<errno.h>|  
|`_futime64`|\<sys/utime.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_futime.c  
// This program uses _futime to set the  
// file-modification time to the current time.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <io.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/utime.h>  
#include <share.h>  
  
int main( void )  
{  
   int hFile;  
  
   // Show file time before and after.   
   system( "dir crt_futime.c_input" );  
  
   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );  
  
   if( _futime( hFile, NULL ) == -1 )  
      perror( "_futime failed\n" );  
   else  
      printf( "File time modified\n" );  
  
   _close (hFile);  
  
   system( "dir crt_futime.c_input" );  
}  
```  
  
## <a name="input-crtfutimecinput"></a>輸入︰crt_futime.c_input  
  
```  
Arbitrary file contents.  
```  
  
### <a name="sample-output"></a>範例輸出  
  
```  
Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:40 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
 Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:41 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
File time modified  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)
