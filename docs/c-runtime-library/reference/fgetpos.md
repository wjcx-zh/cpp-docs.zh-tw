---
title: "fgetpos | Microsoft Docs"
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
  - "fgetpos"
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
  - "fgetpos"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fgetpos 函式"
  - "資料流, 檔案位置指標"
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgetpos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得資料流的檔案位置指示器。  
  
## 語法  
  
```  
int fgetpos(   
   FILE *stream,  
   fpos_t *pos   
);  
```  
  
#### 參數  
 `stream`  
 目標資料流。  
  
 `pos`  
 位置指示器儲存區。  
  
## 傳回值  
 如果成功，`fgetpos` 會傳回 0。  如果失敗，則會傳回非零的值並將 `errno` 設定為下列資訊清單常數之一 \(定義於 STDIO.H\): `EBADF`，表示指定的資料流不是有效的檔案指標也無法存取則為 `EINVAL`，表示 `stream` 值或 `pos` 的值無效，例如，如果是 null 指標。  如果 `stream`或`pos`為 `NULL`指標，則函式叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
## 備註  
 `fgetpos` 函式在 `pos`上的物件取得 `stream` 引數的檔案位置指示器的目前值並儲存它。  在呼叫 `fgetpos` 時， `fsetpos` 函式可以在稍後使用 `pos` 中儲存的資訊重設 `stream` 引數的指標到它的位置。  `pos` 值在內部格式儲存和只供 `fgetpos` 和 `fsetpos`。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fgetpos`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fgetpos.c  
// This program uses fgetpos and fsetpos to  
// return to a location in a file.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE   *stream;  
   fpos_t pos;  
   char   buffer[20];  
  
   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {  
      perror( "Trouble opening file" );  
      return -1;  
   }  
  
   // Read some data and then save the position.   
   fread( buffer, sizeof( char ), 8, stream );  
   if( fgetpos( stream, &pos ) != 0 ) {  
      perror( "fgetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fgetpos: %.13s\n", buffer );  
  
   // Restore to old position and read data   
   if( fsetpos( stream, &pos ) != 0 ) {  
      perror( "fsetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fsetpos: %.13s\n", buffer );  
   fclose( stream );  
}  
```  
  
## 輸入:crt\_fgetpos.txt  
  
```  
fgetpos gets a stream's file-position indicator.  
```  
  
### 輸出 crt\_fgetpos.txt  
  
```  
after fgetpos: gets a stream  
after fsetpos: gets a stream  
```  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fsetpos](../../c-runtime-library/reference/fsetpos.md)