---
title: "fread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fread"
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
  - "fread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料 [C++], 從輸入資料流讀取"
  - "fread 函式"
  - "讀取資料 [C++], 從輸入資料流"
  - "資料流 [C++], 讀取資料來源"
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# fread
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料流讀取資料。  
  
## 語法  
  
```  
size_t fread(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### 參數  
 `buffer`  
 資料儲存位置  
  
 `size`  
 項目大小 \(以位元組為單位\)。  
  
 `count`  
 要讀取的最大項目數。  
  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 `fread` 傳回實際讀取的完整項目的數目，此數目可能小於 `count` ，如果發生錯誤，或如果檔案結尾在達到 `count`之前發生*。*使用 `feof` 或 `ferror` 函式具有文件關閉條件差異讀取錯誤。  如果 `size` 或 `count` 為 0 時， `fread` 會傳回 0，而緩衝區內容不會變更。  如果 `stream` 或 `buffer` 為 null 指標，則`fread` 叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 0 。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `fread` 函式。 `buffer`讀取由 `size` 位元組決定 `count` 項目從輸入 `stream` 的並儲存它們*。*檔案指標相關聯的 `stream` \(如果有的話\) 是實際讀取的位元組數目增加。  如果指定的資料流文字模式開啟，重設為一組可用於唯一換行字元取代。  取代為對檔案指標或傳回值沒有作用。  如果發生錯誤，檔案指標位置為不定。  部分讀取項目的值無法判斷的。  
  
 這個函式鎖定其他執行緒。  如果您需要非鎖定版本，請使用 `_fread_nolock`。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fread`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fread.c  
// This program opens a file named FREAD.OUT and  
// writes 25 characters to the file. It then tries to open  
// FREAD.OUT and read in 25 characters. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   // Open file in text mode:  
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )  
   {  
      for ( i = 0; i < 25; i++ )  
         list[i] = (char)('z' - i);  
      // Write 25 characters to stream   
      numwritten = fwrite( list, sizeof( char ), 25, stream );  
      printf( "Wrote %d items\n", numwritten );  
      fclose( stream );  
  
   }  
   else  
      printf( "Problem opening the file\n" );  
  
   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )  
   {  
      // Attempt to read in 25 characters   
      numread = fread( list, sizeof( char ), 25, stream );  
      printf( "Number of items read = %d\n", numread );  
      printf( "Contents of buffer = %.25s\n", list );  
      fclose( stream );  
   }  
   else  
      printf( "File could not be opened\n" );  
}  
```  
  
  **撰寫 25 項目**  
**項目數讀取 \= 25**  
**緩衝區 \= zyxwvutsrqponmlkjihgfedcb 內容**   
## .NET Framework 對等用法  
 [System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)