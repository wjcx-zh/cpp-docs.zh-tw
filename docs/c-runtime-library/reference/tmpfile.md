---
title: "tmpfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "tmpfile"
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
  - "tmpfile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "暫存檔案"
  - "tmpfile 函式"
  - "暫存檔案，建立"
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# tmpfile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立暫存檔案。  因為更安全的版本，才能使用這個函式已被取代;請參閱 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)。  
  
## 語法  
  
```  
FILE *tmpfile( void );  
```  
  
## 傳回值  
 如果成功，則 `tmpfile` 會傳回資料流的指標。  否則會傳回 `NULL` 指標。  
  
## 備註  
 `tmpfile` 函式會建立暫存檔案並將指標傳回該資料流。  暫存檔案在根目錄中建立。  除了之外，要在該目錄中建立暫存檔案，請使用 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)搭配使用 [tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 或 [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 。  
  
 如果無法開啟檔案， `tmpfile` 會傳回 `NULL` 指標。  這個暫存檔自動刪除時，只有在檔案關閉，也就是說，當程式通常時結束，或者，呼叫 `_rmtmp` 時，會假設，在目前的工作目錄不會變更。  暫存檔案在 `w+b` \(二進位\) 讀取\/寫入模式下開啟。  
  
 失敗，則會發生您比更 TMP\_MAX 嘗試衍生 \(請參閱 STDIO.H\) 與 `tmpfile`的呼叫。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`tmpfile`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
> [!NOTE]
>  您必須擁有系統管理員權限，才能在 Windows Vista 中執行本範例。  
  
```  
// crt_tmpfile.c  
// compile with: /W3  
// This program uses tmpfile to create a  
// temporary file, then deletes this file with _rmtmp.  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int  i;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      if( (stream = tmpfile()) == NULL ) // C4996  
      // Note: tmpfile is deprecated; consider using tmpfile_s instead  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
  **暫存檔案 1 建立**  
**暫存檔案 2 建立**  
**暫存檔案 3 建立**  
**刪除的 3 個暫存檔**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_rmtmp](../../c-runtime-library/reference/rmtmp.md)   
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)