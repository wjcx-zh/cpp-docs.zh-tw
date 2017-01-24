---
title: "clearerr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "clearerr"
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
  - "clearerr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "clearerr 函式"
  - "資料流的錯誤表指標"
  - "重設資料流錯誤指標"
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# clearerr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重設資料流的錯誤指示器。  這些函式已有更安全的版本可用，請參閱 [clearerr\_s](../../c-runtime-library/reference/clearerr-s.md)。  
  
## 語法  
  
```  
void clearerr(  
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 備註  
 `clearerr` 函式會將錯誤指示器和檔案結尾標記的 `stream`。  不會自動清除錯誤指示器;一次指定的資料流的錯誤指示器設定，該資料流的作業繼續之前傳回錯誤值，直到呼叫`clearerr`， `fseek`， `fsetpos`， `rewind`。  
  
 如果 `stream` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，則函式會回傳並將 `errno` 設定為 `EINVAL`。  如需 `errno` 和錯誤碼的詳細資訊，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。  
  
 這個函式更安全的版本可用;請參閱 [clearerr\_s](../../c-runtime-library/reference/clearerr-s.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`clearerr`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_clearerr.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      clearerr( stdin );  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      clearerr( stdin );  
   }  
   else  
      printf( "No read error\n" );  
}  
```  
  
  **`nnWrite` 錯誤:沒有錯誤**  
**輸入是否會造成錯誤?n**  
**沒有讀取錯誤。**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [錯誤處理](../../c-runtime-library/error-handling-crt.md)   
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)