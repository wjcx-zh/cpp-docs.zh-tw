---
title: "_locking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_locking"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_locking"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_locking 函式"
  - "位元組 [C++], 鎖定檔案"
  - "檔案 [C++], 鎖定"
  - "檔案 [C++], 鎖定位元組"
  - "locking 函式"
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _locking
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

鎖定或解除鎖定檔案的位元組。  
  
## 語法  
  
```  
  
      int _locking(  
   int fd,  
   int mode,  
   long nbytes   
);  
```  
  
#### 參數  
 `fd`  
 檔案描述項。  
  
 *mode*  
 要執行的鎖定動作。  
  
 *nbytes*  
 要鎖定的位元組數目。  
  
## 傳回值  
 如果成功，`_locking` 會傳回 0。  回傳 \-1 表示失敗，在此情況下 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 會被設置為以下之一的值。  
  
 `EACCES`  
 鎖定被拒 \(檔案已鎖定或已解除鎖定\) 。  
  
 `EBADF`  
 無效的檔案描述項。  
  
 `EDEADLOCK`  
 鎖定被拒。  當 `_LK_LOCK` 或 `_LK_RLCK` 旗標被指定且檔案無法在 10 次嘗試內被鎖定時回傳。  
  
 `EINVAL`  
 給予 `_locking` 無效的參數。  
  
 如果因為不正確的參數導致失敗，例如無效的檔案描述項，無效參數處理常式會被調用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  
  
## 備註  
 `_locking` 函式鎖定或解除鎖定 `fd` 指定的檔案的 *nbytes* 個位元組。  檔案裏的鎖定位元組阻止其他處理程序存取那些位元組。  所有鎖定或解除鎖定從目前的檔案指標位置開始並持續至接下來的 *nbytes* 個位元組。  鎖定位元組超過檔案結尾是可能的。  
  
 *mode* 必須是下列定義於 Locking.h 的表示常值之一。  
  
 `_LK_LOCK`  
 鎖定指定的位元組。  如果位元組無法鎖定，程式會在 1 秒後立即再試一次。  如果在 10 次嘗試之後，位元組無法被鎖定，此常值回傳一個錯誤。  
  
 `_LK_NBLCK`  
 鎖定指定的位元組。  如果位元組無法被鎖定，此常值回傳一個錯誤。  
  
 `_LK_NBRLCK`  
 與 `_LK_NBLCK` 相同。  
  
 `_LK_RLCK`  
 與 `_LK_LOCK` 相同。  
  
 `_LK_UNLCK`  
 解除指定位元組的鎖定，它們必須是曾於之前被鎖定的。  
  
 檔案中多個不重疊的區域是可以被鎖定的。  被解除鎖定的區域必須是之前曾被鎖定的。  `_locking` 不會合併相連接的區域，如果兩個被鎖定的區域相連接，每個區域必須分別被解除鎖定。  區域應該只被短暫地鎖定且在關閉檔案或結束應用程式前解除鎖定。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_locking`|\<io.h\> and \<sys\/locking.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_locking.c  
/* This program opens a file with sharing. It locks  
 * some bytes before reading them, then unlocks them. Note that the  
 * program works correctly only if the file exists.  
 */  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/locking.h>  
#include <share.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
  
int main( void )  
{  
   int  fh, numread;  
   char buffer[40];  
  
   /* Quit if can't open file or system doesn't   
    * support sharing.   
    */  
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,   
                          _S_IREAD | _S_IWRITE );  
   printf( "%d %d\n", err, fh );  
   if( err != 0 )  
      exit( 1 );  
  
   /* Lock some bytes and read them. Then unlock. */  
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )  
   {  
      long lseek_ret;  
      printf( "No one can change these bytes while I'm reading them\n" );  
      numread = _read( fh, buffer, 30 );  
      buffer[30] = '\0';  
      printf( "%d bytes read: %.30s\n", numread, buffer );  
      lseek_ret = _lseek( fh, 0L, SEEK_SET );  
      _locking( fh, LK_UNLCK, 30L );  
      printf( "Now I'm done. Do what you will with them\n" );  
   }  
   else  
      perror( "Locking failed\n" );  
  
   _close( fh );  
}  
```  
  
## Input: crt\_locking.txt  
  
```  
The first thirty bytes of this file will be locked.  
```  
  
## 範例輸出  
  
```  
No one can change these bytes while I'm reading them  
30 bytes read: The first thirty bytes of this  
Now I'm done. Do what you will with them  
```  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)