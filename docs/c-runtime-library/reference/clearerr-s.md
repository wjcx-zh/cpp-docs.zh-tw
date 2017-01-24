---
title: "clearerr_s | Microsoft Docs"
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
  - "clearerr_s"
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
  - "clearerr_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "clearerr_s 函式"
  - "資料流的錯誤表指標"
  - "重設資料流錯誤指標"
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# clearerr_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重設資料流的錯誤指示器。  這是 [clearerr](../../c-runtime-library/reference/clearerr.md) 的安全性強化版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 語法  
  
```  
errno_t clearerr_s(  
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標  
  
## 傳回值  
 零，如果成功; `EINVAL` ，如果 `stream` 是空的。  
  
## 備註  
 `clearerr_s` 函式會將錯誤指示器和檔案結尾標記的 `stream`。  不會自動清除錯誤指示器;一次指定的資料流的錯誤指示器設定，該資料流的作業繼續之前傳回 `clearerr_s`， `clearerr`， `fseek`， `fsetpos`的錯誤值，或者呼叫 `rewind` 。  
  
 如果 `stream` 為 NULL，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`clearerr_s`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_clearerr_s.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   errno_t err;  
  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
}  
```  
  
  **`nnWrite` 錯誤:錯誤的檔案描述項**  
**輸入是否會造成錯誤?n**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [錯誤處理](../../c-runtime-library/error-handling-crt.md)   
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)