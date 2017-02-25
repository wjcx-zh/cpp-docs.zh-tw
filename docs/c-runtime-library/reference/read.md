---
title: "_read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_read"
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
  - "_read"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_read 函式"
  - "資料 [C++], 讀取"
  - "資料 [CRT]"
  - "檔案 [C++], 讀取"
  - "read 函式"
  - "讀取資料 [C++]"
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _read
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讀取檔案中的資料時。  
  
## 語法  
  
```  
  
      int _read(  
   int fd,  
   void *buffer,  
   unsigned int count   
);  
```  
  
#### 參數  
 `fd`  
 參考開啟檔案的檔案描述項。  
  
 *buffer*  
 資料儲存位置  
  
 *count*  
 最大位元組數。  
  
## 傳回值  
 \_**read** 傳回讀取的位元組數，可能小於 *計數*，如果少於檔案中的 *count* 位元組，或是檔案在文字模式開啟，在此情況下，每個托架傳回行摘要 \(CR\-LF\) 配對會被單一換行字元取代。  只有單一換行字元在傳回值中被計算。  取代不影響檔案指標。  
  
 如果函式嘗試讀取檔案的結尾，則會傳回 0。  如果 `fd` 無效，檔案進行讀取未開啟、或者檔案鎖定，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，此函式回傳 –1 並將`errno` 設置為 `EBADF`。  
  
 如果 *緩衝區* 是 **NULL**，則呼叫無效的參數處理常式。  如果執行允許繼續，函式會回傳\-1，並且`errno`會設定為 `EINVAL`。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `_read` 函式會讀取 *計數* 位元組數讀入 *緩衝區* 的最大值，從檔案相關聯的 `fd`。  讀入作業在檔案指標的目前位置開始 \(如果有的話\) 與特定檔案相關。  在讀取作業之後，檔案指標指向下一個未讀取的字元。  
  
 如果檔案在文字模式開啟，`_read` 遇到 CTRL\+Z 字元\(該字元被視為檔案結尾指示器\)時，讀取終止。  使用 [\_lseek](../../c-runtime-library/reference/lseek-lseeki64.md) 清除檔案結尾指示器。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_read`|\<io.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_read.c  
/* This program opens a file named crt_read.txt  
 * and tries to read 60,000 bytes from  
 * that file using _read. It then displays the  
 * actual number of bytes read.  
 */  
  
#include <fcntl.h>      /* Needed only for _O_RDWR definition */  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
char buffer[60000];  
  
int main( void )  
{  
   int fh;  
   unsigned int nbytes = 60000, bytesread;  
  
   /* Open file for input: */  
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
      perror( "open failed on input file" );  
      exit( 1 );  
   }  
  
   /* Read in input: */  
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )  
      perror( "Problem reading file" );  
   else  
      printf( "Read %u bytes from file\n", bytesread );  
  
   _close( fh );  
}  
```  
  
## 輸入：crt\_read.txt  
  
```  
Line one.  
Line two.  
```  
  
## Output  
  
```  
Read 19 bytes from file  
```  
  
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_write](../../c-runtime-library/reference/write.md)