---
title: "flushall | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_flushall"
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
  - "flushall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "flushall 函式"
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _flushall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

清除所有資料流；清除所有的緩衝區。  
  
## 語法  
  
```  
int _flushall( void );  
```  
  
## 傳回值  
 `_flushall` 傳回開啟資料流數目 \(輸入和輸出\)。  不會回傳錯誤。  
  
## 備註  
 根據預設， `_flushall` 函式寫入適當檔案所有緩衝區內容與開啟輸出資料流。  所有緩衝區與開啟輸入資料流清除其目前的內容。\(這些緩衝區由作業系統通常維護，判斷最佳時寫入磁碟自動寫入資料：當緩衝區已滿，在資料流關閉，或者當程式正常終止，不需關閉的資料流\)。  
  
 如果讀取之後呼叫 `_flushall`，新的資料會從輸入檔案讀取至緩衝區。  在呼叫 `_flushall`之後，所有資料流保持開啟。  
  
 執行階段程式庫的對硬碟操作功能使您可以確保重要資料被直接寫入硬碟而非先寫入作業系統緩衝區。  不會覆寫現有的程式，您可以連接程式的目的檔與 Commode.obj 啟用這項功能。  在產生的可執行檔，呼叫 `_flushall` 時寫入磁碟任何緩衝區內容。  只有 `_flushall` 和 `fflush` 是受 Commode.obj 影響。  
  
 如需控制項對鍵盤功能的詳細資訊，請參閱 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)、 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)和 [\_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)。  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`_flushall`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_flushall.c  
// This program uses _flushall  
// to flush all open buffers.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int numflushed;  
  
   numflushed = _flushall();  
   printf( "There were %d streams flushed\n", numflushed );  
}  
```  
  
  **會有 3 個資料流清除**   
## .NET Framework 對等用法  
  
-   [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
-   [System::IO::StreamWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.flush.aspx)  
  
-   [System::IO::TextWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.textwriter.flush.aspx)  
  
-   [System::IO::BinaryWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.flush.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_commit](../../c-runtime-library/reference/commit.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)