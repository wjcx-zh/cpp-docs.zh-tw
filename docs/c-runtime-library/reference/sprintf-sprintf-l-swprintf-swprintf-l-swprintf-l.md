---
title: "sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l | Microsoft Docs"
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
  - "__swprintf_l"
  - "sprintf"
  - "_sprintf_l"
  - "_swprintf_l"
  - "swprintf"
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
  - "_stprintf_l"
  - "__swprintf_l"
  - "sprintf_l"
  - "swprintf"
  - "_sprintf_l"
  - "sprintf"
  - "_stprintf"
  - "stprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__swprintf_l 函式"
  - "_CRT_NON_CONFORMING_SWPRINTFS"
  - "_sprintf_l 函式"
  - "_stprintf 函式"
  - "_stprintf_l 函式"
  - "_swprintf_l 函式"
  - "格式化的文字 [C++]"
  - "sprintf 函式"
  - "sprintf_l 函式"
  - "stprintf 函式"
  - "stprintf_l 函式"
  - "字串 [C++], 寫入至"
  - "swprintf 函式"
  - "swprintf_l 函式"
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
caps.latest.revision: 36
caps.handback.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將格式化資料寫入字串。  其中一些函式已有更安全的版本可用，請參閱 [sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)。  `swprintf` 和 `_swprintf_l` 的安全版本未採用 `count` 參數。  
  
## 語法  
  
```  
int sprintf(  
   char *buffer,  
   const char *format [,  
   argument] ...   
);  
int _sprintf_l(  
   char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int swprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format [,  
   argument]...  
);  
int _swprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
int __swprintf_l(  
   wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int sprintf(  
   char (&buffer)[size],  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _sprintf_l(  
   char (&buffer)[size],  
   const char *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
  
```  
  
#### 參數  
 `buffer`  
 輸出的儲存位置  
  
 `count`  
 要儲存在此函式的 Unicode 版本中的字元數上限。  
  
 `format`  
 格式控制字串  
  
 `argument`  
 選擇性引數  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 寫入的字元數目，如果發生錯誤則為 \-1。  如果 `buffer` 或 `format` 為 null 指標，則會叫用無效參數處理常式 \(如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述\)。  如果允許繼續執行，這些函式會傳回 \-1，並將 `errno` 設為 `EINVAL`。  
  
 `sprintf` 會傳回儲存在 `buffer` 中的位元組數目，不計結束的 null 字元。  `swprintf`會傳回儲存在  `buffer` 中的寬字元數目，結束的 null 寬字元不計算在內。  
  
## 備註  
 `sprintf` 函式會在 `buffer` 中格式化並儲存一連串字元和值。  每個 `argument` \(如果有的話\) 是根據 `format` 中的對應格式規格進行轉換和輸出。  此格式包含一般字元，與 `format`printf 的 [引數具有相同的形式和功能。](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) null 字元會附加至最後一個寫入的字元之後。  如果在重疊的字串之間進行複製，則行為是未定義的。  
  
> [!IMPORTANT]
>  若使用 `sprintf`，沒有方法可限制寫入的字元數，這表示使用 `sprintf` 的程式碼很容易發生緩衝區溢位。  請考慮使用相關函式 [\_snprintf](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) \(其指定要寫入 `buffer` 的字元數上限\)，或使用 [\_scprintf](../../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md) 以判斷需要多大的緩衝區。  也請確定 `format` 不是使用者定義的字串。  
  
 `swprintf` 是 `sprintf` 的寬字元版本，`swprintf` 的指標引數是寬字元字串。  `swprintf` 的編碼錯誤偵測可能不同於 `sprintf`。  `swprintf` 和 `fwprintf` 的運作方式完全相同，不同處在於 `swprintf` 會將輸出寫入字串，而非類型 `FILE` 的目的地，而且 `swprintf` 需要 `count` 參數指定要寫入的字元數上限。  這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
 `swprintf` 符合 ISO C 標準，其需要 `size_t` 類型的第二個參數 `count`。  若要強制使用舊的非標準行為，請定義 `_CRT_NON_CONFORMING_SWPRINTFS`。  在未來版本中，可能會移除舊的行為，因此應該變更程式碼，以使用新的一致行為。  
  
 在 C\+\+ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_stprintf`|`sprintf`|`sprintf`|`_swprintf`|  
|`_stprintf_l`|`_sprintf_l`|`_sprintf_l`|`__swprintf_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`sprintf`, `_sprintf_l`|\<stdio.h\>|  
|`swprintf`, `_swprintf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_sprintf.c  
// compile with: /W3  
// This program uses sprintf to format various  
// data and place them in the string named buffer.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996  
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996  
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996  
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996  
   // Note: sprintf is deprecated; consider using sprintf_s instead  
  
   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
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
// crt_swprintf.c  
// wide character example  
// also demonstrates swprintf returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf fails because string contains WEOF (\xffff)  
   printf( "wrote %d characters\n", len );  
}  
```  
  
  **已寫入 11 個字元**  
**已寫入 \-1 個字元**   
## .NET Framework 對等用法  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)