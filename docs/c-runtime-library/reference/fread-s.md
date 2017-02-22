---
title: "fread_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fread_s"
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
  - "fread_s"
  - "stdio/fread_s"
dev_langs: 
  - "C++"
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# fread_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料流讀取資料。  這些[fread](../../c-runtime-library/reference/fread.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
size_t fread_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### 參數  
 `buffer`  
 資料儲存位置  
  
 `bufferSize`  
 終點緩衝區的大小 \(以位元組為單位\)。  
  
 `elementSize`  
 寫入位元組之項目的大小。  
  
 `count`  
 要讀取的最大項目數。  
  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 `fread_s` 會傳回讀取至緩衝區，可能小於 `count` \(整個\) 中的項目數目，如果讀取錯誤或檔案結尾，遇到在 `count` 之前。  使用 `feof` 或 `ferror` 函式具有文件關閉條件差異錯誤。  如果 `size` 或 `count` 為 0 時， `fread_s` 會傳回 0，而緩衝區內容不會變更。  如果 `stream` 或 `buffer` 為 null 指標，則`fread_s` 叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 0 。  
  
 如需更多有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `fread_s` 函式。 `buffer`讀取由 `elementSize` 位元組決定 `count` 項目從輸入 `stream` 的並儲存它們。檔案指標相關聯的 `stream` \(如果有的話\) 是實際讀取的位元組數目增加。  如果指定的資料流文字模式開啟，重設為一組可用於唯一換行字元取代。  取代為對檔案指標或傳回值沒有作用。  如果發生錯誤，檔案指標位置為不定。  部分讀取項目的值無法判斷的。  
  
 這個函式鎖定其他執行緒。  如果您需要非鎖定版本，請使用 `_fread_nolock`。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fread_s`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```cpp  
  
// crt_fread_s.c  
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c  
//  
// This program opens a file that's named FREAD.OUT and  
// writes characters to the file. It then tries to open  
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
#define BUFFERSIZE 30  
#define DATASIZE 22  
#define ELEMENTCOUNT 2  
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)  
#define FILENAME "FREAD.OUT"  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   for ( i = 0; i < DATASIZE; i++ )  
      list[i] = (char)('z' - i);  
   list[DATASIZE] = '\0'; // terminal null so we can print it  
  
   // Open file in text mode:  
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )  
   {  
      // Write DATASIZE characters to stream   
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );  
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );  
      printf( "Wrote %d items\n\n", numwritten );  
      fclose( stream );  
   } else {  
      printf( "Problem opening the file\n" );  
      return -1;  
   }  
  
   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {  
      // Attempt to read in characters in 2 blocks of 11  
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );  
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );  
      printf( "Contents of buffer after write/read:\n\t%s\n", list );  
      fclose( stream );  
   } else {  
      printf( "File could not be opened\n" );  
      return -1;  
   }  
}  
```  
  
  **讀取的緩衝區內容在寫入前\/:**  
 **zyxwvutsrqponmlkjihgfe**  
 **撰寫 22 項目**   
 **11 位元組元素數目讀取 \= 2**   
 **讀取的緩衝區內容在寫入後\/:**   
 **zyxwvutsrqponmlkjihgfe**    
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)