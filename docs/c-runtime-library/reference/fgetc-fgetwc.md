---
title: "fgetc、fgetwc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fgetwc"
  - "fgetc"
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
  - "_fgettc"
  - "fgetwc"
  - "fgetc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fgettc 函式"
  - "字元, 讀取"
  - "fgetc 函式"
  - "fgettc 函式"
  - "fgetwc 函式"
  - "從資料流讀取字元"
  - "資料流, 讀取字元來源"
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# fgetc、fgetwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料流讀取一個字元。  
  
## 語法  
  
```  
int fgetc(   
   FILE *stream   
);  
wint_t fgetwc(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 `fgetc` 傳回作為 `int` 讀取的字元或傳回`EOF` 表示錯誤或檔案結尾。  `fgetwc` 返回，如 [wint\_t](../../c-runtime-library/standard-types.md)，對應至字元的寬字元讀取或傳回 `WEOF` 來表示錯誤或檔案結尾。  對於兩個函式，請使用 `feof` 或 `ferror` 區別錯誤和文件結尾條件。  如果讀取錯誤，資料流的錯誤指示器被設定。  如果 `stream` 為 `NULL`，`fgetc` 和 `fgetwc`叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 `EOF`。  
  
## 備註  
 這些函式從與 `stream` 相關聯的檔案的目前位置讀取單一字元。  函式會將關聯的檔案指標 \(如果有定義\)指向下一個字元。  如果資料流已在檔案結尾，資料流的檔案結尾標記會被設定。  
  
 `fgetc` 與 `getc` 相等，不過，只有實作為函式，而不是函式和巨集。  
  
 `fgetwc` 為`fgetc` 的寬字元版本；它將 `c` 根據是否 `stream` 在文字模式或二進為模式開啟決定作為多位元組字元或寬字元來讀取。  
  
 有 `_nolock` 結尾的版本是相同的，除非它們受到其他執行緒干擾。  
  
 如需處理寬字元和多位元組字元的詳細資訊文字和二進位模式的詳細資訊，請參閱 [Unicode 文字和二進位模式的資料流 I\/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_fgettc`|`fgetc`|`fgetc`|`fgetwc`|  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fgetc`|\<stdio.h\>|  
|`fgetwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fgetc.c  
// This program uses getc to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   char buffer[81];  
   int  i, ch;  
  
   // Open file to read line from:  
   fopen_s( &stream, "crt_fgetc.txt", "r" );  
   if( stream == NULL )  
      exit( 0 );  
  
   // Read in first 80 characters and place them in "buffer":   
   ch = fgetc( stream );  
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = fgetc( stream );  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
   fclose( stream );  
}  
```  
  
## Input: crt\_fgetc.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Line one.  
Line two.  
```  
  
## .NET Framework 對等用法  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx).  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)