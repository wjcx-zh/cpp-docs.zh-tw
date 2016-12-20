---
title: "_strset_s、_strset_s_l、_wcsset_s、_wcsset_s_l、_mbsset_s、_mbsset_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsset_s"
  - "_wcsset_s_l"
  - "_strset_s"
  - "_mbsset_s_l"
  - "_strset_s_l"
  - "_mbsset_s"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wcsset_s_l"
  - "strset_s"
  - "_mbsset_s"
  - "mbsset_s"
  - "_strset_s"
  - "_mbsset_s_l"
  - "strset_s_l"
  - "_wcsset_s"
  - "mbsset_s_l"
  - "wcsset_s_l"
  - "wcsset_s"
  - "_strset_s_l"
  - "_tcsset_s_l"
  - "_tcsset_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsset_s 函式"
  - "_mbsset_s_l 函式"
  - "_strset_s 函式"
  - "_strset_s_l 函式"
  - "_tcsset_s 函式"
  - "_tcsset_s_l 函式"
  - "_wcsset_s 函式"
  - "_wcsset_s_l 函式"
  - "字元 [C++], 設定"
  - "mbsset_s 函式"
  - "mbsset_s_l 函式"
  - "字串 [C++], 設定字元"
  - "strset_s 函式"
  - "strset_s_l 函式"
  - "tcsset_s 函式"
  - "tcsset_s_l 函式"
  - "wcsset_s 函式"
  - "wcsset_s_l 函式"
ms.assetid: dceb2909-6b41-4792-acb7-888e45bb8b35
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strset_s、_strset_s_l、_wcsset_s、_wcsset_s_l、_mbsset_s、_mbsset_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定字串為字元的字元。  這些 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbsset_s` and `_mbsset_s_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t _strset_s(  
   char *str,  
   size_t numberOfElements,  
   int c   
);  
errno_t _strset_s_l(  
   char *str,  
   size_t numberOfElements,  
   int c,  
   locale_t locale  
);  
errno_t _wcsset_s(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c   
);  
errno_t *_wcsset_s_l(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c,  
   locale_t locale  
);  
errno_t _mbsset_s(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c   
);  
errno_t _mbsset_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `str`  
 以null結尾的字符串進行設置。  
  
 `numberOfElements`  
 緩衝區的大小`str`。  
  
 `c`  
 字元設定。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果成功則為零，否則為錯誤碼。  
  
 這些函式會驗證它們的參數。  如果 `str` 為 null 指標，則 `numberOfElements` 引數小於或等於 0，或者傳遞的區塊不是以 null 終止，則無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 `EINVAL` 設定為 `errno` 給`EINVAL`  
  
## 備註  
 `_strset_s` 函式會將所有字元轉換為 `c`的 `str` ，轉換為 `char`，除了終止的空字符。  `_wcsset_s` 和 `_mbsset_s` 是 `_strset_s` 的寬字元和多位元組字元版本。  引數和傳回值的資料型別對應的變更。  這三個函式其餘部分的運作相同。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsset_s`|`_strset_s`|`_mbsset_s`|`_wcsset_s`|  
|`_tcsset_s_l`|`_strset_s_l`|`_mbsset_s_l`|`_wcsset_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strset_s`|\<string.h\>|  
|`_strset_s_l`|\<tchar.h\>|  
|`_wcsset_s`|\<string.h\> 或 \<wchar.h\>|  
|`_wcsset_s_l`|\<tchar.h\>|  
|`_mbsset_s`, `_mbsset_s_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strset_s.c  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char string[] = "Fill the string with something.";  
   printf( "Before: %s\n", string );  
   _strset_s( string, _countof(string), '*' );  
   printf( "After:  %s\n", string );  
}  
```  
  
  **先前:以項目填滿字串。**  
**執行後：\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\***   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)