---
title: "_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l | Microsoft Docs"
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
  - "_mbsnset"
  - "_strnset"
  - "_mbsnset_l"
  - "_wcsnset_l"
  - "_wcsnset"
  - "_strnset_l"
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
  - "_tcsncset_l"
  - "mbsnset_l"
  - "_tcsnset_l"
  - "_fstrnset"
  - "_wcsnset_l"
  - "_ftcsnset"
  - "wcsnset_l"
  - "_mbsnset_l"
  - "_strnset"
  - "_tcsnset"
  - "_strnset_l"
  - "mbsnset"
  - "strnset_l"
  - "_mbsnset"
  - "_wcsnset"
  - "_tcsncset"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrnset 函式"
  - "_ftcsnset 函式"
  - "_mbsnset 函式"
  - "_mbsnset_l 函式"
  - "_strnset 函式"
  - "_strnset_l 函式"
  - "_tcsncset 函式"
  - "_tcsncset_l 函式"
  - "_tcsnset 函式"
  - "_tcsnset_l 函式"
  - "_wcsnset 函式"
  - "_wcsnset_l 函式"
  - "字元 [C++], 初始化為格式"
  - "fstrnset 函式"
  - "ftcsnset 函式"
  - "初始化字元"
  - "mbsnset 函式"
  - "mbsnset_l 函式"
  - "字串 [C++], 初始化"
  - "strnset_l 函式"
  - "tcsncset 函式"
  - "tcsnset 函式"
  - "tcsnset_l 函式"
  - "wcsnset_l 函式"
ms.assetid: 3f306489-5763-48e5-b939-aefee7c94ef5
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始化字串的字元至指定的字元。  這些函式已存在更安全的版本，請參閱 [\_strnset\_s、\_strnset\_s\_l、\_wcsnset\_s、\_wcsnset\_s\_l、\_mbsnset\_s、\_mbsnset\_s\_l](../../c-runtime-library/reference/strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbsnset` and `_mbsnset_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *_strnset(  
   char *str,  
   int c,  
   size_t count   
);  
char *_strnset_l(  
   char *str,  
   int c,  
   size_t count,  
   locale_t locale  
);  
wchar_t *_wcsnset(  
   wchar_t *str,  
   wchar_t c,  
   size_t count   
);  
wchar_t *_wcsnset_l(  
   wchar_t *str,  
   wchar_t c,  
   size_t count,  
   _locale_t locale  
);  
unsigned char *_mbsnset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnset_l(  
   unsigned char *str,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `str`  
 待變更字串。  
  
 `c`  
 字元設定。  
  
 `count`  
 要設定的字元長度。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回變更後字串的指標。  
  
## 備註  
 `_strnset` 函式最多將  `str` 的`count` 字元設為 `c` \(轉換為 `char`\)。  如果 `count` 大於 `str` 的長度，長度為 `str` 而非 `count` 的。  
  
 `_wcsnset` 和 `_mbsnset`  是 `_strnset` 的寬字元和多位元組字元版本。  `_wcsnset`  的字串引數和傳回值是寬字元字串，而 `_mbsnset` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 `_mbsnset`  使自身參數有效化，如果 `str` 為 null 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `_mbsnset`  會傳回 NULL 並設定 `errno` 為 `EINVAL`。  `_strnset` 和 `_wcsnset` 並不驗證它們的參數。  
  
 輸出值受地區設定的 `LC_CTYPE`  分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strnset`|\<string.h\>|  
|`_strnset_l`|\<tchar.h\>|  
|`_wcsnset`|\<string.h\> 或 \<wchar.h\>|  
|`_wcsnset_l`|\<tchar.h\>|  
|`_mbsnset`, `_mbsnset_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strnset.c  
// compile with: /W3  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 characters of string to be *'s */  
   printf( "Before: %s\n", string );  
   _strnset( string, '*', 4 ); // C4996  
   // Note: _strnset is deprecated; consider using _strnset_s  
   printf( "After:  %s\n", string );  
}  
```  
  
  **之前: 這是測試**  
**之後: \*\*\*\* 是測試**   
## .NET Framework 對等用法  
 [System::String::Replace](https://msdn.microsoft.com/en-us/library/system.string.replace.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)