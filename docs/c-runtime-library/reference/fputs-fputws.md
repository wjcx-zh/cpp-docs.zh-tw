---
title: "fputs、fputws | Microsoft Docs"
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
  - "fputs"
  - "fputws"
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
  - "fputs"
  - "fputws"
  - "_fputts"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fputts 函式"
  - "fputs 函式"
  - "fputts 函式"
  - "fputws 函式"
  - "資料流, 將字串寫入"
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fputs、fputws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串寫入一個資料流。  
  
## 語法  
  
```  
int fputs(   
   const char *str,  
   FILE *stream   
);  
int fputws(   
   const wchar_t *str,  
   FILE *stream   
);  
```  
  
#### 參數  
 `str`  
 輸出字串。  
  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 如果成功，這些函式都會傳回非負值。  在錯誤， `fputs` 和 `fputws` 會傳回 `EOF`。  如果 `str` 或 `stream` 為 null 指標，則這些函示叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並且`fputs`回傳`EOF`，和`fputws`傳回`WEOF`  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 這些函式中的每個 `str` 複製到輸出 `stream` 目前所在位置。  `fputws` 分別複製寬字元引數 `str` 對 `stream` 做為多位元組字元字串或寬字元字串，根據可能的選取 `stream` 文字模式或二進位模式開啟。  沒有函式複製結束的 null 字元。  
  
 如果資料流是以 ANSI 模式開啟，則這兩個函式的行為相同。  `fputs` 目前不支援輸出到 UNICODE 資料流。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fputts`|`fputs`|`fputs`|`fputws`|  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`fputs`|\<stdio.h\>|  
|`fputws`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fputs.c  
// This program uses fputs to write  
// a single line to the stdout stream.  
  
#include <stdio.h>  
  
int main( void )  
{  
   fputs( "Hello world from fputs.\n", stdout );  
}  
```  
  
  **Hello World 從 fputs 的。**   
## .NET Framework 對等用法  
 [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [gets、\_getws](../../c-runtime-library/gets-getws.md)   
 [puts、\_putws](../../c-runtime-library/reference/puts-putws.md)