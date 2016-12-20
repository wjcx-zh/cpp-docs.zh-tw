---
title: "_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l | Microsoft Docs"
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
  - "_sprintf_p"
  - "_swprintf_p_l"
  - "_swprintf_p"
  - "_sprintf_p_l"
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
  - "_sprintf_p"
  - "_swprintf_p_l"
  - "_sprintf_p_l"
  - "_swprintf_p"
  - "sprintf_p"
  - "swprint_p_l"
  - "swprintf_p"
  - "swprintf_p_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "sprintf_p_l 函式"
  - "swprintf_p 函式"
  - "swprintf_p_l 函式"
  - "_sprintf_p 函式"
  - "_sprintf_p_l 函式"
  - "_swprintf_p 函式"
  - "sprintf_p 函式"
  - "_stprintf_p 函式"
  - "stprintf_p 函式"
  - "_swprintf_p_l 函式"
  - "stprintf_p_l 函式"
  - "格式化的文字 [C++]"
  - "_stprintf_p_l 函式"
ms.assetid: a2ae78e8-6b0c-48d5-87a9-ea2365b0693d
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寫入字串格式化資料以能夠指定命令參數用於格式字串。  
  
## 語法  
  
```  
int _sprintf_p(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format [,  
   argument] ...   
);  
int _sprintf_p_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _swprintf_p(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format [,  
   argument]...  
);  
int _swprintf_p_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] …   
);  
```  
  
#### 參數  
 `buffer`  
 輸出的儲存位置  
  
 `sizeOfBuffer`  
 要儲存的最大字元數。  
  
 `format`  
 格式控制字串  
  
 `argument`  
 選擇性引數  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 寫入的字元數目，如果發生錯誤則為 \-1。  
  
## 備註  
 `_sprintf_p`  函式會在 `buffer` 中格式化並儲存一連串字元和值。  每個 `argument` \(如果有的話\) 是根據 `format` 中的對應格式規格進行轉換和輸出。  此格式包含一般字元，與 `printf_p` 的 `format` 引數具有相同的形式和功能。  `NULL` 字元會附加至最後一個寫入的字元之後。  如果在重疊的字串之間進行複製，則行為是未定義的。  `_sprintf_p`和 `sprintf_s`的差異在於 `_sprintf_p`支援可以指定命令引數使用格式字串的位置參數。  如需詳細資訊，請參閱[printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 `_swprintf_p` 是 `_sprintf_p` 的寬字元版本，`_swprintf_p` 的指標引數是寬字元字串。  `_swprintf_p` 的編碼錯誤偵測可能不同於 `_sprintf_p`。  `_swprintf_p` 和 `fwprintf_p` 的作用完全相同，例外的是，`_swprintf_p` 會將輸出寫入字串而非類型為 `FILE` 的目的端，而且 `_swprintf_p` 必須有 `count`參數才能指定要寫入的字元數上限。  這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
 `_sprintf_p` 會傳回儲存在 `buffer` 中的位元組數目，不計結束的`NULL`字元。  `_swprintf_p` 會傳回儲存在 `buffer` 中的寬字元數目，不計結束的`NULL`寬字元。  如果 `buffer` 或`format`為 null 指標，或是如果格式字串包含無效的格式化字元，無效的參數會叫用處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 \-1 並將`errno` 設定為 `EINVAL`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_stprintf_p`|`_sprintf_p`|`_sprintf_p`|`_swprintf_p`|  
|`_stprintf_p_l`|`_sprintf_p_l`|`_sprintf_p_l`|`_swprintf_p_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_sprintf_p`, `_sprintf_p_l`|\<stdio.h\>|  
|`_swprintf_p`, `_swprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_sprintf_p.c  
// This program uses _sprintf_p to format various  
// data and place them in the string named buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
    char     buffer[200],  
            s[] = "computer", c = 'l';  
    int      i = 35,  
            j;  
    float    fp = 1.7320534f;  
  
    // Format and print various data:   
    j  = _sprintf_p( buffer, 200,  
                     "   String:    %s\n", s );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Character: %c\n", c );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Integer:   %d\n", i );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Real:      %f\n", fp );  
  
    printf( "Output:\n%s\ncharacter count = %d\n",   
            buffer, j );  
}  
```  
  
  **輸出：**  
 **字串：computer**  
 **字元：l**  
 **整數：35**  
 **實數：1.732053**  
**字元計數 \= 79**   
## 範例  
  
```  
// crt_swprintf_p.c  
// This is the wide character example which  
// also demonstrates _swprintf_p returning  
// error code.  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    wchar_t buffer[BUFFER_SIZE];  
    int     len;  
  
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",  
                      0, L" marbles in your head.");  
    _printf_p( "Wrote %d characters\n", len );  
  
    // _swprintf_p fails because string contains WEOF (\xffff)  
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",   
                      L"Hello\xffff world" );  
    _printf_p( "Wrote %d characters\n", len );  
}  
```  
  
  **已寫入 24 個字元**  
**已寫入 \-1 個字元**   
## .NET Framework 對等用法  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_fprintf\_p、\_fprintf\_p\_l、\_fwprintf\_p、\_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)