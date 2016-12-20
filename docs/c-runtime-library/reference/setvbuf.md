---
title: "setvbuf | Microsoft Docs"
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
  - "setvbuf"
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
  - "setvbuf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "控制資料流緩衝"
  - "setvbuf 函式"
  - "資料流緩衝"
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setvbuf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制流程緩衝區和緩衝區大小。  
  
## 語法  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
 `buffer`  
 使用者配置的緩衝區。  
  
 `mode`  
 緩衝模式。  
  
 `size`  
 緩衝區的大小，以位元組為單位。  允許的範圍:2\<\= `size` \< \= INT\_MAX \(2147483647\)。  在內部提供 `size` 的值會四捨五入至最接近 2 的倍數。.  
  
## 傳回值  
 如果成功則傳回 0。  
  
 如果 `stream` 是 `NULL`，或者如果 `mode` 或 `size` 不是有效的變更，則無效的參數處理會被叫用處理，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `errno`，並將 `EINVAL` 設為 \-1。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `setvbuf` 函式可讓程式控制緩衝區、緩衝區大小的 `stream`。  當他開啟時，`stream` 必須參考未執行 I\/O 作業的開啟檔案。  `buffer`所指向的陣列當做緩衝區，除非它是`NULL`，在 `setvbuf` 中使用自動配置的長度 `size`\/2 \* 2 位元組的緩衝區。  
  
 模式必須是`_IOFBF`, `_IOLBF`, or `_IONBF`。  如果 `mode` 是 `_IOFBF` 或 `_IOLBF`，則 `size` 當做緩衝區的大小。  如果 `mode` 是 `_IONBF`，則資料流是無緩衝區的，且 `size` 和 `buffer` 會被忽略。  `mode` 的值及其意義如下:  
  
 `_IOFBF`  
 完整的緩衝區；換句話說，當 `buffer` 被當作緩衝區和 `size` 當做緩衝區的大小。  如果 `buffer` 是 `NULL`，則使用自動配置的緩衝區 `size` 位元組長。  
  
 `_IOLBF`  
 對於某些系統，這提供行的緩衝區。  不過，對於 Win32，行為與 `_IOFBF` 相同\-充分的緩衝區。  
  
 `_IONBF`  
 不論 `buffer` 或 `size`，都沒有使用緩衝區。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`setvbuf`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
  **「stream1 」現在有 1024 位元組緩衝區。**  
**「stream2」目前沒有任何緩衝區**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)