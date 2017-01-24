---
title: "_chsize | Microsoft Docs"
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
  - "_chsize"
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
  - "_chsize"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chsize 函式"
  - "chsize 函式"
  - "檔案 [C++], 變更大小"
  - "大小"
  - "大小, 變更檔案"
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chsize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

改變檔案大小。   更多可用更安全版本，請參閱[\_chsize\_s](../../c-runtime-library/reference/chsize-s.md)。  
  
## 語法  
  
```  
int _chsize(   
   int fd,  
   long size   
);  
```  
  
#### 參數  
 `fd`  
 參考開啟檔案的檔案描述項。  
  
 `size`  
 新檔案的長度，以位元組為單位。  
  
## 傳回值  
 如果成功變更檔案大小，`_chsize`會傳回值 0。  傳回值\-1表示錯誤: 如果指定的檔案鎖定物件的存取，`errno`設定 `EACCES`，如果指定的檔案是唯讀或描述項無效，如果裝置沒有多餘空間或`EINVAL`，則為 `EBADF`，如果`size`小於零，則為 `ENOSPC`。  
  
 如需有關這些回傳碼和其他回傳碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_chsize`函式擴充或截斷與 `fd` 相關聯之檔案至 `size`的指定長度。  檔案必須開啟允許寫入模式。  如果檔案已擴充，附加 null 字元 \('\\0'\)。  如果檔案已截斷，從縮短的檔案結尾至檔案的原始長度的任何資料將遺失。  
  
 這個函式會驗證它的參數。  如果 `size` 小於零或 `fd` 是錯誤的檔案描述項，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_chsize`|\<io.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_chsize.c  
// This program uses _filelength to report the size  
// of a file before and after modifying it with _chsize.  
  
#include <io.h>  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <share.h>  
  
int main( void )  
{  
   int fh, result;  
   unsigned int nbytes = BUFSIZ;  
  
   // Open a file   
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,  
                 _S_IREAD | _S_IWRITE ) == 0 )  
   {  
      printf( "File length before: %ld\n", _filelength( fh ) );  
      if( ( result = _chsize( fh, 329678 ) ) == 0 )  
         printf( "Size successfully changed\n" );  
      else  
         printf( "Problem in changing the size\n" );  
      printf( "File length after:  %ld\n", _filelength( fh ) );  
      _close( fh );  
   }  
}  
```  
  
  **先前檔案長度:0**  
**已成功變更的大小。**  
**之後檔案長度:329678**   
## .NET Framework 對等用法  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_sopen、\_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)