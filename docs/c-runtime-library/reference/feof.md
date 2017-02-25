---
title: "feof | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "feof"
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
  - "feof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案結尾, 測試"
  - "feof 函式"
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# feof
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

測試串流的檔案結尾。  
  
## 語法  
  
```  
int feof(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 `feof` 函式在讀入運算嘗試在檔案結尾後讀入時回傳一非零值，否則回傳零。  如果串流指標是 `NULL` ，函式叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `errno` 會被設置為 `EINVAL` 且 `feof` 會回傳零。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `feof` 常式 \(會實作為函式和巨集\) 判斷是否已經過 `stream` 結尾。  已經過檔案結尾時，讀取作業將回傳檔案結尾指示，直到關閉串流或呼叫 `rewind` 、 `fsetpos` 、 `fseek` 或 `clearerr` 為止。  
  
 例如，一個當案包含 10 個位元組，而您從它讀取了 10 個位元組， `feof` 會回傳 0 ，因為即使檔案指標已經位於檔案的結尾，但是你並沒有再次嘗試去讀取它。  只有在您嘗試讀取第 11 個位元組時， `feof` 才會傳回非零的值。  
  
## 需求  
  
|Function|必要的標頭檔|  
|--------------|------------|  
|`feof`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_feof.c  
// This program uses feof to indicate when  
// it reaches the end of the file CRT_FEOF.TXT. It also  
// checks for errors with ferror.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int  count, total = 0;  
   char buffer[100];  
   FILE *stream;  
  
   fopen_s( &stream, "crt_feof.txt", "r" );  
   if( stream == NULL )  
      exit( 1 );  
  
   // Cycle until end of file reached:  
   while( !feof( stream ) )  
   {  
      // Attempt to read in 100 bytes:  
      count = fread( buffer, sizeof( char ), 100, stream );  
      if( ferror( stream ) )      {  
         perror( "Read error" );  
         break;  
      }  
  
      // Total up actual bytes read  
      total += count;  
   }  
   printf( "Number of bytes read = %d\n", total );  
   fclose( stream );  
}  
```  
  
## Input: crt\_feof.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Number of bytes read = 19  
```  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需更多的資訊，請參閱 [平台調用範例 \(Platform Invoke Examples\)](../Topic/Platform%20Invoke%20Examples.md) 。  
  
## 請參閱  
 [錯誤處理](../../c-runtime-library/error-handling-crt.md)   
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)