---
title: "fflush | Microsoft Docs"
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
  - "fflush"
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
  - "fflush"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fflush 函式"
  - "清除"
  - "資料流, 清除"
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
caps.latest.revision: 18
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fflush
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

清除資料流。  
  
## 語法  
  
```  
int fflush(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 如果成功清除，`fflush` 會傳回 0 緩衝區。  值 0 也指定資料流中沒有緩衝區的情況下傳回或為唯讀是開啟的。  回傳值為 `EOF` 表示錯誤。  
  
> [!NOTE]
>  如果 `fflush` 傳回 `EOF`，資料可能遺失的由於寫入失敗。  當設定關鍵錯誤處理常式時，將緩衝區與 `setvbuf` 函式或低階 I\/O 常式 \(例如 `_open`、 `_close`和 `_write` 而非資料流 I\/O 函式最安全的值。  
  
## 備註  
 `fflush` 函式清除資料流。  如果檔案與 `stream` 為輸出已開啟的 `fflush` ，將加入至該檔案寫入緩衝區的內容與相關聯的資料流。  如果資料流已輸入已開啟， `fflush` 清除內容緩衝區。  `fflush` 否定任何之前呼叫的效果套用至 `ungetc` 物件的 `stream`。  此外， `fflush(NULL)` 清除為輸出所有開啟的資料流。  資料流保持開啟在呼叫之後。  `fflush` 具有無緩衝資料流產生任何作用。  
  
 緩衝區由作業系統通常維護，判斷最佳時寫入磁碟自動寫入資料：當緩衝區已滿，在資料流關閉，或者當程式正常終止，不需關閉的資料流。  執行階段程式庫的對硬碟操作功能使您可以確保重要資料被直接寫入硬碟而非先寫入作業系統緩衝區。  不會覆寫現有的程式，您可以連接程式的目的檔與 COMMODE.OBJ 啟用這項功能。  在產生的可執行檔，呼叫 `_flushall` 時寫入磁碟任何緩衝區內容。  只有 `_flushall` 和 `fflush` 是受 COMMODE.OBJ 影響。  
  
 如需控制項對鍵盤功能的詳細資訊，請參閱 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)、 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)和 [\_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)。  
  
 這個函式鎖定呼叫的執行緒並具備執行緒安全。  如需非鎖定版本，請參閱 `_fflush_nolock`。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fflush`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fflush.c  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int integer;  
   char string[81];  
  
   // Read each word as a string.  
   printf( "Enter a sentence of four words with scanf: " );  
   for( integer = 0; integer < 4; integer++ )  
   {  
      scanf_s( "%s", string, sizeof(string) );        
      printf( "%s\n", string );  
   }  
  
   // You must flush the input buffer before using gets.   
   // fflush on input stream is an extension to the C standard   
   fflush( stdin );     
   printf( "Enter the same sentence with gets: " );  
   gets_s( string, sizeof(string) );  
   printf( "%s\n", string );  
}  
```  
  
  **`這是測試 這是測試`  `這是測試 這是一 testEnter`每四個字行與 scanf 的:這是測試**  
**這個**   
**是**  
**a**  
**測試**  
**輸入同一個句子與取得:這是測試**  
**這是測試**   
## .NET Framework 對等用法  
 [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)