---
title: "fseek、_fseeki64 | Microsoft Docs"
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
  - "_fseeki64"
  - "fseek"
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
apitype: "DLLExport"
f1_keywords: 
  - "fseek"
  - "_fseeki64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fseeki64 函式"
  - "檔案指標 [C++]"
  - "檔案指標 [C++], 移動"
  - "fseek 函式"
  - "fseeki64 函式"
  - "搜尋檔案指標"
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fseek、_fseeki64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移動檔案指標至指定的位置。  
  
## 語法  
  
```  
int fseek(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
 `offset`  
 `origin` 的位元組數。  
  
 `origin`  
 初始位置。  
  
## 傳回值  
 如果成功，`fseek` 及 `_fseeki64` 則傳回 true。  否則，會傳回非零的值。  在不能達到搜尋的裝置上，傳回值為未定義。  如果 `stream` 為 null 指標，或是，如果 `origin` 不是以下其中一個允許的值， `fseek` 和 `_fseeki64` 叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 \-1。  
  
## 備註  
 `fseek` 和 `_fseeki64` 函式移動與 `stream` 關連的檔案指標 \(如果有的話\) 至從 `origin` 位移 `offset` 位元組的新位置。在資料流的下一個作業會在新位置時發生。  在資料流開啟更新時，下一個作業可能會讀取或寫入。  origin 引數必須是下列其中一個定義於 STDIO.H 的常數:  
  
 `SEEK_CUR`  
 檔案指標目前的位置。  
  
 `SEEK_END`  
 檔案結尾。  
  
 `SEEK_SET`  
 檔案的開頭。  
  
 您可以使用 `fseek` 和 `_fseeki64` 重新定位指標至檔案的任何位置。  指標也可以在檔案結尾之外放置。  `fseek` 和 `_fseeki64`清除檔案結尾標記和忽略任何先前對 `stream` 的 `ungetc` 呼叫。  
  
 當檔案為附加資料開啟時，目前的檔案位置取決於最後一個 I\/O 作業，而不是寫入將發生的位置。  如果在為附加開啟的檔案未發生 I\/O 作業，檔案位置是檔案的開頭。  
  
 文字模式下開啟的資料流，因為回車符轉譯會導致 `fseek` 和 `_fseeki64` 產生未定義結果，讓  `fseek` 和 `_fseeki64` 的使用具有限制。  唯一保證 `fseek` 和 `_fseeki64`作業在文字模式下開啟的資料流工作如下:  
  
-   尋找於相對於任何原始值位移 0。  
  
-   從檔案開頭加上當使用 `fseek` 時 `ftell` 回傳的位移值或是當使用 `_fseeki64` 時 `_ftelli64` 回傳的位移值尋找這個物件。  
  
 在文字模式下，CTRL\+Z 也會在輸入時解譯成檔案結尾字元。  開啟為讀取\/寫入的檔案中， `fopen` 及所有相關的常式會檢查檔案結尾是否有 CTRL\+Z，並加以移除 \(如果可能\)。  之所以這樣做，是因為使用 `fseek` 和 `ftell` 或是 `_fseeki64` 及 `_ftelli64` 在以 CTRL\+Z 結束的檔案內移動可能會讓 `fseek` 或是 `_fseeki64` 在檔案結尾附近產生不正確的行為。  
  
 當 CRT 開啟開始位元順序標記 \(BOM\) 的檔案時，檔案指標位於 BOM 之後 \(也就是在檔案的實際內容的開頭\)。  如果您必須對檔案作 `fseek` ，請使用 `ftell` 以得到初始位置再作 `fseek` 而不是使用位置 0。  
  
 這個函式在執行期間鎖定其他執行緒因此具備執行緒安全。  如需非鎖定版本，請參閱 [\_fseek\_nolock、\_fseeki64\_nolock](../../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fseek`|\<stdio.h\>|  
|`_fseeki64`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fseek.c  
// This program opens the file FSEEK.OUT and  
// moves the pointer to the file's beginning.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[81];  
   int  result;  
  
   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )  
   {  
      printf( "The file fseek.out was not opened\n" );  
      return -1;  
   }  
   fprintf( stream, "The fseek begins here: "  
                    "This is the file 'fseek.out'.\n" );  
   result = fseek( stream, 23L, SEEK_SET);  
   if( result )  
      perror( "Fseek failed" );  
   else  
   {  
      printf( "File pointer is set to middle of first line.\n" );  
      fgets( line, 80, stream );  
      printf( "%s", line );  
    }  
   fclose( stream );  
}  
```  
  
  **File pointer is set to middle of first line.**  
**This is the file 'fseek.out'.**   
## .NET Framework 對等用法  
  
-   [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
-   [System::IO::FileStream::Seek](https://msdn.microsoft.com/en-us/library/system.io.filestream.seek.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [ftell、\_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)