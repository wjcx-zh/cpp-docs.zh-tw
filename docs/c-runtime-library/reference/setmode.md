---
title: "_setmode | Microsoft Docs"
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
  - "_setmode"
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
  - "_setmode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_setmode 函式"
  - "檔案轉譯 [C++], 設定模式"
  - "檔案 [C++], 模式"
  - "檔案 [C++], 轉譯"
  - "setmode 函式"
  - "Unicode [C++], 主控台輸出"
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _setmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定檔案轉譯模式。  
  
## 語法  
  
```  
int _setmode (    int fd,    int mode  );  
```  
  
#### 參數  
 `fd`  
 檔案描述項。  
  
 `mode`  
 新的轉譯模式。  
  
## 傳回值  
 若成功，會傳回之前的轉譯模式。  
  
 若傳遞了無效的參數到此函式，則會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  若允許繼續執行，此函式會傳回 –1，並將 `errno` 設定為 `EBADF`：表示無效的檔案描述項；或是設定為 `EINVAL`：表示無效的 `mode` 引數。  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_setmode` 函式會設定 `mode` 為 `fd` 所指定之檔案的轉譯模式。  若 `mode` 設定文字 \(亦即：已轉譯\) 模式，則傳遞 `_O_TEXT`。  歸位字元–換行字元 \(CR\-LF\) 的組合會在輸入中轉譯為單行換行字元。  換行字元會在輸出中轉譯為 CR\-LF 組合。  傳遞 `_O_BINARY` 可設定二進位 \(未轉譯\) 模式，此模式會抑止這些轉譯。  
  
 您也可以傳遞 `_O_U16TEXT`、`_O_U8TEXT` 或 \_`O_WTEXT` 以啟用 Unicode 模式，本文件稍後的第二個範例即會進行示範。  一般而言會使用 `_setmode` 修改 `stdin` 和 `stdout` 的預設轉譯模式，但您可以將其用於任何檔案。  若您將 `_setmode` 套用於資料流的檔案描述項，請先呼叫 `_setmode`，再於資料流上執行任意輸入或輸出作業。  
  
> [!CAUTION]
>  若您將資料寫入檔案資料流，請先使用 [fflush](../../c-runtime-library/reference/fflush.md) 明確地清除代碼，再使用 `_setmode` 變更模式。  若您沒有清除代碼，可能會發生未預期的行為。  若您沒有將資料寫入資料流，則不用清除代碼。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_setmode`|\<io.h\>|\<fcntl.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_setmode.c  
// This program uses _setmode to change  
// stdin from text mode to binary mode.  
  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
int main( void )  
{  
   int result;  
  
   // Set "stdin" to have binary mode:  
   result = _setmode( _fileno( stdin ), _O_BINARY );  
   if( result == -1 )  
      perror( "Cannot set mode" );  
   else  
      printf( "'stdin' successfully changed to binary mode\n" );  
}  
```  
  
  **'stdin' successfully changed to binary mode**   
## 範例  
  
```  
// crt_setmodeunicode.c  
// This program uses _setmode to change  
// stdout to Unicode. Cyrillic and Ideographic  
// characters will appear on the console (if  
// your console font supports those character sets).  
  
#include <fcntl.h>  
#include <io.h>  
#include <stdio.h>  
  
int main(void) {  
    _setmode(_fileno(stdout), _O_U16TEXT);  
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");  
    return 0;  
}  
  
```  
  
## .NET Framework 同等  
  
-   [\<caps:sentence id\="tgt28" sentenceid\="fe03c471a7a38d5378cea62467482dae" class\="tgtSentence"\>System::IO::BinaryReader 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.aspx)  
  
-   [\<caps:sentence id\="tgt29" sentenceid\="105e62b7505c25e3e182779c87f145eb" class\="tgtSentence"\>System::IO::TextReader 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.textreader.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md)