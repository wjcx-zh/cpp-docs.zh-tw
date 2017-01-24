---
title: "_tell、_telli64 | Microsoft Docs"
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
  - "_telli64"
  - "_tell"
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
  - "tell"
  - "telli64"
  - "_telli64"
  - "_tell"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tell 函式"
  - "_telli64 函式"
  - "檔案指標 [C++]"
  - "檔案指標 [C++], 取得"
  - "tell 函式"
  - "telli64 函式"
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _tell、_telli64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得檔案指標的位置。  
  
## 語法  
  
```  
long _tell(  
   int handle  
);  
__int64 _telli64(  
   int handle   
);  
```  
  
#### 參數  
 `handle`  
 參考開啟檔案的檔案描述項。  
  
## 傳回值  
 檔案指標目前的位置  在不能達到搜尋的裝置上，傳回值為未定義。  
  
 回傳值為 –1L 表示錯誤。  如果 `handle` 為無效檔案描述項，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EBADF`，並傳回 \-1L.。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `_tell` 函式取得檔案指標的目前位置 \(如果有的話\) 與 `handle` 引數。  這個位置是以從檔案的開頭開始的位元組數表示。  如需 `_telli64` 函式，這個值會表示為 64 位元整數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_tell`, `_telli64`|\<io.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_tell.c  
// This program uses _tell to tell the  
// file pointer position after a file read.  
//  
  
#include <io.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <share.h>  
#include <string.h>  
  
int main( void )  
{  
   int  fh;  
   char buffer[500];  
  
   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )  
   {  
      char buff[50];  
      _strerror_s( buff, sizeof(buff), NULL );  
      printf( buff );  
      exit( -1 );  
   }  
  
   if( _read( fh, buffer, 500 ) > 0 )  
      printf( "Current file position is: %d\n", _tell( fh ) );  
   _close( fh );  
}  
```  
  
## Input: crt\_tell.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Current file position is: 20  
```  
  
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [ftell、\_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)