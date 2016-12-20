---
title: "_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l | Microsoft Docs"
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
  - "_fwprintf_p"
  - "_fprintf_p_l"
  - "_fwprintf_p_l"
  - "_fprintf_p"
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
  - "_fprintf_p"
  - "_ftprintf_p"
  - "fwprintf_p"
  - "_fwprintf_p"
  - "fprintf_p"
  - "ftprintf_p"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fprintf_p 函式"
  - "_fprintf_p_l 函式"
  - "_ftprintf_p 函式"
  - "_ftprintf_p_l 函式"
  - "_fwprintf_p 函式"
  - "_fwprintf_p_l 函式"
  - "fprintf_p 函式"
  - "fprintf_p_l 函式"
  - "ftprintf_p 函式"
  - "ftprintf_p_l 函式"
  - "fwprintf_p 函式"
  - "fwprintf_p_l 函式"
  - "列印 [C++], 格式化的資料至資料流"
  - "資料流, 將格式化的資料列印至"
ms.assetid: 46b082e1-45ba-4383-9ee4-97015aa50bc6
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將格式化的資料列印至資料流。  
  
## 語法  
  
```  
int _fprintf_p(   
   FILE *stream,  
   const char *format [,  
   argument ]...  
);  
int _fprintf_p_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...  
);  
int _fwprintf_p(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...  
);  
int _fwprintf_p_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...  
);  
```  
  
#### 參數  
 `stream`  
 `FILE` 結構的指標。  
  
 `format`  
 格式控制字串。  
  
 `argument`  
 選擇性引數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 當發生 I\/O 錯誤時，`_fprintf_p` 和 `_fwprintf_p` 傳回寫入的字元數或傳回負值。  
  
## 備註  
 `_fprintf_p`格式化並在輸出`stream`中印出一連串字元和值。  每個函式 `argument` \(如果有的話\) 是根據 `format` 中的對應格式規格進行轉換和輸出。  如果是 `_fprintf_p`，則 `format` 引數具有它在 `_printf_p`的相同語法和用法。  這些函式支援位置參數，就可以變更格式字串所使用的參數順序。  如需位置參數的詳細資訊，請參閱  [printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md) 。  
  
 `_fwprintf_p` 是 `_fprintf_p` 的寬字元版本；在`_fwprintf_p`中，`format` 是寬字元字串。  如果資料流是以 ANSI 模式開啟，則這些函式的行為相同。  `_fprintf_p` 目前不支援輸出到 UNICODE 串流。  
  
 這些以 `_l` 後綴的函式版本除了使用傳入的地區設定以外行為相同。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
 如果 `stream` 或 `format`任一 為 null 指標，或如果有任何未知或格式錯誤的格式規範，則像不安全的版本 \(請參閱 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)\)，這些函式會驗證它們的參數並叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所描述的。  如果允許繼續執行，函式回傳 \-1 並將 `errno` 設置為 `EINVAL` 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_ftprintf_p`|`_fprintf_p`|`_fprintf_p`|`_fwprintf_p`|  
|`_ftprintf_p_l`|`_fprintf_p_l`|`_fprintf_p_l`|`_fwprintf_p_l`|  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fprintf_p`, `_fprintf_p_l`|\<stdio.h\>|  
|`_fwprintf_p`, `_fwprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_fprintf_p.c  
// This program uses _fprintf_p to format various  
// data and print it to the file named FPRINTF_P.OUT. It  
// then displays FPRINTF_P.OUT on the screen using the system  
// function to invoke the operating-system TYPE command.  
//   
  
#include <stdio.h>  
#include <process.h>  
  
int main( void )  
{  
    FILE    *stream = NULL;  
    int     i = 10;  
    double  fp = 1.5;  
    char    s[] = "this is a string";  
    char    c = '\n';  
  
    // Open the file  
    if ( fopen_s( &stream, "fprintf_p.out", "w" ) == 0)  
    {  
        // Format and print data  
        _fprintf_p( stream, "%2$s%1$c", c, s );  
        _fprintf_p( stream, "%d\n", i );  
        _fprintf_p( stream, "%f\n", fp );  
  
        // Close the file  
        fclose( stream );  
    }  
  
    // Verify our data  
    system( "type fprintf_p.out" );  
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
 [printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)   
 [\_cprintf\_p、\_cprintf\_p\_l、\_cwprintf\_p、\_cwprintf\_p\_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)   
 [fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)