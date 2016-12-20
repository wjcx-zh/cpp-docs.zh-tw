---
title: "_futime、_futime32、_futime64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_futime64"
  - "_futime32"
  - "_futime"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "futime"
  - "_futime"
  - "futime64"
  - "_futime64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_futime 函式"
  - "futime32 函式"
  - "futime64 函式"
  - "檔案修改時間 [C++]"
  - "_futime64 函式"
  - "futime 函式"
  - "_futime32 函式"
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _futime、_futime32、_futime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定在開啟檔案的修改時間。  
  
## 語法  
  
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
  
#### 參數  
 `fd`  
 開啟檔案的檔案描述。  
  
 `filetime`  
 in 包含新的修改日期之結構的指標。  
  
## 傳回值  
 如果成功，則傳回 0。  如果錯誤發生， 則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續執行，函式會傳回– 1 並在 `errno` 設定為 `EBADF`，表示無效的檔案描述項，或者為 `EINVAL`\(表示無效的參數。  
  
## 備註  
 `_futime` 常式設定修改存取日期和時間在開啟檔案相關聯的 `fd`*。* `_futime` 與 [\_utime](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)相同，不同的是，其引數是開啟檔案的檔案描述項，而不是檔案或路徑名稱加入至檔案。  新的修改存取日期和時間的 `_utimbuf` 結構包含欄位。  兩個欄位必須包含有效的值。  `_utimbuf32` 和 `_utimbuf64` 與 `_utimbuf` 分別是弧形除了使用 32 位元和 64 位元時間型別。  `_futime` 和 `_utimbuf` 使用一個 64 位元時間型別，以及 `_futime` 相同的行為與 `_futime64`。  如果您需要強制舊版行為，請定義 `_USE_32BIT_TIME_T`。  這樣做會導致 `_futime` 相同的行為對 `_futime32` 會導致 `_utimbuf` 結構使用 32 位元時間型別，使它相當於 `__utimbuf32`。  
  
 `_futime64`，使用 `__utimbuf64` 結構中，藉由 23:59 讀取和修改檔案的日期: 59， 3000 年 12 月 31 日，， UTC;而對 `_futime32` 的呼叫失敗，如果上檔案的日期比 19:14 之後: 07 年 1 月 18 日 2038， UTC。  1970 年 1 月 1 日的午夜是這些函式的時間日期範圍的下界。  
  
## 需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_futime`|\<sys\/utime.h\>|\<errno.h\>|  
|`_futime32`|\<sys\/utime.h\>|\<errno.h\>|  
|`_futime64`|\<sys\/utime.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
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
  
## 輸入:crt\_futime.c\_input  
  
```  
Arbitrary file contents.  
```  
  
### 範例輸出  
  
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
  
## .NET Framework 對等用法  
  
-   [System::IO::File::SetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastaccesstime.aspx)  
  
-   [System::IO::File::SetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastwritetime.aspx)  
  
-   [System::IO::File::SetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.setcreationtime.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)