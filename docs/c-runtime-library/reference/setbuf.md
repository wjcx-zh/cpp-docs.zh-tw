---
title: "setbuf | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "setbuf"
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
  - "setbuf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "setbuf 函式"
  - "資料流緩衝"
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setbuf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制資料流緩衝。  這個函式已被取代；請改用 [setvbuf](../../c-runtime-library/reference/setvbuf.md) 。  
  
## 語法  
  
```  
void setbuf(  
   FILE *stream,  
   char *buffer   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
 `buffer`  
 使用者配置的緩衝區。  
  
## 備註  
 緩衝區為 `stream`的 `setbuf` 控制項的函式。  `stream` 引數必須參考未讀取或未寫入的檔案。  如果 `buffer` 引數為 `NULL`，資料流是無緩衝區的。  否則，緩衝區必須指向一字元陣列長度 `BUFSIZ`，`BUFSIZ` 為緩衝區大小，如 STDIO.H. 定義。  使用者指定的緩衝區，而不是指定資料流的預設系統配置緩衝區，為 I\/O 緩衝區。  預設為 `stderr` 資料流是無緩衝區的，不過，您可以使用 `setbuf` 指派緩衝區給 `stderr`。  
  
 `setbuf` 已由 [setvbuf](../../c-runtime-library/reference/setvbuf.md) 取代，為新的程式碼較好的常式。  `setbuf` 是為了保持與現有的程式碼的相容性。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`setbuf`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_setbuf.c  
// compile with: /W3  
// This program first opens files named DATA1 and  
// DATA2. Then it uses setbuf to give DATA1 a user-assigned  
// buffer and to change DATA2 so that it has no buffer.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[BUFSIZ];  
   FILE *stream1, *stream2;  
  
   fopen_s( &stream1, "data1", "a" );  
   fopen_s( &stream2, "data2", "w" );  
  
   if( (stream1 != NULL) && (stream2 != NULL) )  
   {  
      // "stream1" uses user-assigned buffer:  
      setbuf( stream1, buf ); // C4996  
      // Note: setbuf is deprecated; consider using setvbuf instead  
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );  
  
      // "stream2" is unbuffered  
      setbuf( stream2, NULL ); // C4996  
      printf( "stream2 buffering disabled\n" );  
      _fcloseall();  
   }  
}  
```  
  
  **stream1 set to user\-defined buffer at: 0012FCDC**  
**stream2 緩衝停用**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)