---
title: "fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l | Microsoft Docs"
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
  - "_fprintf_s_l"
  - "fwprintf_s"
  - "fprintf_s"
  - "_fwprintf_s_l"
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
  - "_ftprintf_s"
  - "fprintf_s"
  - "fwprintf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fprintf_s_l 函式"
  - "_ftprintf_s 函式"
  - "_ftprintf_s_l 函式"
  - "_fwprintf_s_l 函式"
  - "fprintf_s 函式"
  - "fprintf_s_l 函式"
  - "ftprintf_s 函式"
  - "ftprintf_s_l 函式"
  - "fwprintf_s 函式"
  - "fwprintf_s_l 函式"
  - "將格式化的資料列印至資料流"
ms.assetid: 16067c3c-69ce-472a-8272-9aadf1f5beed
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將格式化的資料列印至資料流。  這些是 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
int fprintf_s(   
   FILE *stream,  
   const char *format [,  
   argument ]...  
);  
int _fprintf_s_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...  
);  
int fwprintf_s(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...  
);  
int _fwprintf_s_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]…  
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
 `format`  
 格式控制字串。  
  
 `argument`  
 選擇性引數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `fprintf_s`傳回寫入的位元組數目。  `fwprintf_s` 傳回寫入的寬字元數目。  當發生輸出錯誤時，這些函式都會傳回負值。  
  
## 備註  
 `fprintf_s` 會在 `stream` 輸出中格式化並儲存一連串字元和值。每個 `argument` 函式\(如果有的話\) 是根據 `format` 中的對應格式規格進行轉換和輸出。如果是 `fprintf_s`，則 `format` 引數具有它在 `printf_s`的相同語法和用法。  
  
 `fwprintf_s` 是 `fprintf_s` 的寬字元版本；在`fwprintf_s`中，`format` 是寬字元字串。  如果資料流是以 ANSI 模式開啟，則這些函式的行為相同。  `fprintf_s` 目前不支援輸出到 UNICODE 串流。  
  
 這些以 `_l` 後綴的函式版本除了使用傳入的地區設定以外行為相同。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
 像不安全的版本 \(請參閱 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)\)，如果 `stream` 或 `format`為 null 指標，這些函式會驗證它們的參數並叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  這些函式與不安全的版本不同之處在於格式字串也會驗證。  如果有任何未知或格式錯誤的格式規範，這些函式產生無效的參數例外狀況。  在所有案例中，如果允許繼續執行，這些函式會傳回 \-1 ，並將  `errno`設為`EINVAL` 。  如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE 和 \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_ftprintf_s`|`fprintf_s`|`fprintf_s`|`fwprintf_s`|  
|`_ftprintf_s_l`|`_fprintf_s_l`|`_fprintf_s_l`|`_fwprintf_s_l`|  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fprintf_s`, `_fprintf_s_l`|\<stdio.h\>|  
|`fwprintf_s`, `_fwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fprintf_s.c  
// This program uses fprintf_s to format various  
// data and print it to the file named FPRINTF_S.OUT. It  
// then displays FPRINTF_S.OUT on the screen using the system  
// function to invoke the operating-system TYPE command.  
  
#include <stdio.h>  
#include <process.h>  
  
FILE *stream;  
  
int main( void )  
{  
   int    i = 10;  
   double fp = 1.5;  
   char   s[] = "this is a string";  
   char   c = '\n';  
  
   fopen_s( &stream, "fprintf_s.out", "w" );  
   fprintf_s( stream, "%s%c", s, c );  
   fprintf_s( stream, "%d\n", i );  
   fprintf_s( stream, "%f\n", fp );  
   fclose( stream );  
   system( "type fprintf_s.out" );  
}  
```  
  
  **this is a string**  
**10**  
**1.500000**   
## .NET Framework 對等用法  
 [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)