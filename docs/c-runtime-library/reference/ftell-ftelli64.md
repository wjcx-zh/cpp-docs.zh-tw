---
title: "ftell、_ftelli64 | Microsoft Docs"
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
  - "_ftelli64"
  - "ftell"
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
  - "_ftelli64"
  - "ftell"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftelli64 函式"
  - "檔案指標 [C++]"
  - "檔案指標 [C++], 取得目前位置"
  - "ftell 函式"
  - "ftelli64 函式"
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ftell、_ftelli64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得檔案指標的目前位置。  
  
## 語法  
  
```  
long ftell(   
   FILE *stream   
);  
__int64 _ftelli64(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 目標 `FILE` 結構。  
  
## 傳回值  
 `ftell` 和 `_ftelli64` 會傳回目前的檔案位置。  因為文字模式會重設為一組轉譯， 所以`ftell` 和 `_ftelli64` 所傳回的值可能不會反映在文字模式下開啟的資料流中的位元組位移。  使用 `ftell` 和 `fseek`或`_ftelli64`和`_fseeki64` 傳回正確檔案位置。  若有錯誤則 `ftell` 為 NULL，並`_ftelli64`會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續執行，則這些函式傳回 \-1L 並將 `errno` 設定至在 ERRNO.H. 定義的其中一個常數。  `EBADF` 常數代表 `stream` 引數不是有效的檔案指標值也不會開啟檔案。  `EINVAL` 表示無效 `stream` 引數傳遞至函式。  在裝置上不能達到尋找 \(例如終端和印表機\)，或 `stream` 時，並未參考開啟檔案時，傳回值為 undefined。  
  
 如需有關這些回傳碼和其他回傳碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `ftell` 和 `_ftelli64`函式擷取檔案指標的目前位置 \(如果有的話\) 相關聯的 `stream`*。*位置以資料流的開頭、目前寫入位置或結尾表示。  
  
 注意，當檔案為附加資料開啟時，目前的檔案位置取決於最後一個 I\/O 作業，而不是寫入將發生的位置。  例如，如果檔案開啟為開啟，而最後一個作業是讀取，則檔案位置是下一個讀取作業即將開始點，而不是下一個寫入開始的位置。\(當檔案開啟為追加時，檔案位置移至任何寫入作業之前檔案結尾\)。如果在為附加開啟的檔案未發生 I\/O 作業，檔案位置是檔案的開頭。  
  
 在此文字模式下，CTRL\+Z 會在輸入時解譯成檔案結尾字元。  開啟為讀取\/寫入的檔案中， `fopen` 及所有相關的常式會檢查檔案結尾是否有 CTRL\+Z，並加以移除 \(如果可能\)。  之所以這樣做，是因為使用 `ftell` 和 `fseek`或是 `_ftelli64`  和`_fseeki64`，在以 CTRL\+Z 結束的檔案內移動可能會讓 `ftell`或`_ftelli64` 在檔案結尾附近產生不正確的行為。  
  
 這個函式在執行期間鎖定呼叫的執行緒，因此具備執行緒安全。  如需非鎖定版本，請參閱 `_ftell_nolock`。  
  
## 需求  
  
|功能|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`ftell`|\<stdio.h\>|\<errno.h\>|  
|`_ftelli64`|\<stdio.h\>|\<errno.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_ftell.c  
// This program opens a file named CRT_FTELL.C  
// for reading and tries to read 100 characters. It  
// then uses ftell to determine the position of the  
// file pointer and displays this position.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long position;  
   char list[100];  
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )  
   {  
      // Move the pointer by reading data:   
      fread( list, sizeof( char ), 100, stream );  
      // Get position after read:   
      position = ftell( stream );  
      printf( "Position after trying to read 100 bytes: %ld\n",  
              position );  
      fclose( stream );  
   }  
}  
```  
  
  **位置在嘗試讀取後 100 個位元組:100**   
## .NET Framework 對等用法  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek、\_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)