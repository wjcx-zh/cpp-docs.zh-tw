---
title: "_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vsprintf_p"
  - "_vswprintf_p"
  - "_vsprintf_p_l"
  - "_vswprintf_p_l"
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
  - "vsprintf_p"
  - "_vswprintf_p"
  - "_vstprintf_p"
  - "vswprintf_p"
  - "_vsprintf_p"
  - "vstprintf_p"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vsprintf_p 函式"
  - "_vsprintf_p_l 函式"
  - "_vstprintf_p 函式"
  - "_vstprintf_p_l 函式"
  - "_vswprintf_p 函式"
  - "_vswprintf_p_l 函式"
  - "格式化的文字 [C++]"
  - "vsprintf_p 函式"
  - "vsprintf_p_l 函式"
  - "vstprintf_p 函式"
  - "vstprintf_p_l 函式"
  - "vswprintf_p 函式"
  - "vswprintf_p_l 函式"
ms.assetid: 00821c0d-9fee-4d8a-836c-0669cfb11317
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將格式化輸出利用指標寫入至參數清單，並能指定參數使用的順序。  
  
## 語法  
  
```  
int _vsprintf_p(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   va_list argptr   
);   
int _vsprintf_p_l(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);   
int _vswprintf_p(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vswprintf_p_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### 參數  
 `buffer`  
 輸出的儲存位置。  
  
 `sizeInBytes`  
 `buffer` 的大小 \(以字元為單位\)。  
  
 `count`  
 在此函式 UNICODE 版本為儲存的最大字元數。  
  
 `format`  
 格式規範。  
  
 `argptr`  
 參數清單的指標。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 `_vsprintf_p` 和 `_vswprintf_p` 回傳寫入的字元數，不包含結尾的空字元，或者在輸出發生錯誤時回傳一個負值。  
  
## 備註  
 這些函式接受一個指向參數清單的指標，格式化並將給定的資料寫入到 `buffer` 所指向的記憶體。  
  
 這些函式與 `vsprintf_s` 和 `vswprintf_s` 不同的地方只有於它們支援位置參數。  如需詳細資訊，請參閱[printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 這些函式的以 `_l` 後綴版本相同，但使用傳遞的地區設定參數而非目前執行緒的地區設定。  
  
 如果 `buffer` 或 `format` 參數為空指標、 count 為零或格式字串包含無效的格式規範字元，無效參數處理常式會被呼叫，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  如果允許繼續執行，函式回傳 \-1 並將 `errno` 設置為 `EINVAL` 。  
  
### 泛用文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstprintf_p`|`_vsprintf_p`|`_vsprintf_p`|`_vswprintf_p`|  
|`_vstprintf_p_l`|`_vsprintf_p_l`|`_vsprintf_p_l`|`_vswprintf_p_l`|  
  
## 需求  
  
|程序|必要的標頭檔|選擇性的標頭檔|  
|--------|------------|-------------|  
|`_vsprintf_p`, `_vsprintf_p_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vswprintf_p`, `_vswprintf_p_l`|\<stdio.h\> 或 \<wchar.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 要求 UNIX V 相容性。  
  
 如需其他相容性資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt__vsprintf_p.c  
// This program uses vsprintf_p to write to a buffer.  
// The size of the buffer is determined by _vscprintf_p.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <stdarg.h>  
  
void example( char * format, ... )  
{  
    va_list  args;  
    int      len;  
    char     *buffer = NULL;  
  
    va_start( args, format );  
  
    // _vscprintf doesn't count the   
    // null terminating string so we add 1.  
    len = _vscprintf_p( format, args ) + 1;  
  
    // Allocate memory for our buffer  
    buffer = (char*)malloc( len * sizeof(char) );  
    if (buffer)  
    {  
        _vsprintf_p( buffer, len, format, args );  
        puts( buffer );  
        free( buffer );  
    }  
}  
  
int main( void )  
{  
    // First example  
    example( "%2$d %1$c %3$d", '<', 123, 456 );  
  
    // Second example  
    example( "%s", "This is a string" );  
}  
```  
  
  **123 \< 456 This is a string**   
## .NET Framework 對等用法  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)