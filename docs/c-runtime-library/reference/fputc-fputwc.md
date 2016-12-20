---
title: "fputc、fputwc | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fputc"
  - "fputwc"
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
  - "fputc"
  - "fputwc"
  - "_fputtc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fputtc 函式"
  - "fputc 函式"
  - "fputtc 函式"
  - "fputwc 函式"
  - "資料流, 將字元寫入"
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fputc、fputwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一個字元寫入資料流。  
  
## 語法  
  
```  
int fputc(  
   int c,  
   FILE *stream   
);  
wint_t fputwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### 參數  
 `c`  
 待寫入字元。  
  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 這些函式都會傳回寫入的字元。  對於`fputc`, 回傳值為 `EOF` 表示錯誤。  對於`fputwc`, 回傳值為 `WEOF` 表示錯誤。  如果 `stream` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，它們會傳回 `EOF`，並將 `errno` 設為 `EINVAL`。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 這些函式都會寫入單一字元 `c` 到檔案在關聯的檔案位置、位置指示器 \(如果已定義\) 和之前所指出的位置指示器屬性。  在 `fputc` 和 `fputwc`的情況下，檔案會和`stream` *相關聯 。*如果檔案在附加模式不支援定位要求也未開啟，字元附加至資料流的末端。  
  
 如果資料流是以 ANSI 模式開啟，則這兩個函式的行為相同。  `fputc` 目前不支援輸出到 UNICODE 資料流。  
  
 與 `_nolock` 結尾的版本相同，但不會防止被其他執行緒干擾。  如需詳細資訊，請參閱[\_fputc\_nolock、\_fputwc\_nolock](../../c-runtime-library/reference/fputc-nolock-fputwc-nolock.md)。  
  
 再來為常式特定圖例。  
  
|常式|備註|  
|--------|--------|  
|`fputc`|相當於 `putc`，不過，只有會實作為函式，而不是函式和巨集。|  
|`fputwc`|`fputc`寬字元版本。  為多位元組字元或寬字元寫入 `c` ，根據可能的選取 `stream` 文字模式或二進位模式下開啟。|  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fputtc`|`fputc`|`fputc`|`fputwc`|  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`fputc`|\<stdio.h\>|  
|`fputwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fputc.c  
// This program uses fputc  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of fputc!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
  **這是 fputc 的測試\!\!**   
## .NET Framework 對等用法  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)