---
title: "strchr、wcschr、_mbschr、_mbschr_l | Microsoft Docs"
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
  - "strchr"
  - "wcschr"
  - "_mbschr_l"
  - "_mbschr"
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
apitype: "DLLExport"
f1_keywords: 
  - "_ftcschr"
  - "strchr"
  - "wcschr"
  - "_tcschr"
  - "_mbschr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcschr 函式"
  - "_mbschr 函式"
  - "_mbschr_l 函式"
  - "_tcschr 函式"
  - "字元 [C++], 在字串中尋找"
  - "ftcschr 函式"
  - "mbschr 函式"
  - "mbschr_l 函式"
  - "strchr 函式"
  - "字串 [C++], 搜尋"
  - "tcschr 函式"
  - "wcschr 函式"
ms.assetid: 2639905d-e983-43b7-b885-abef32cfac43
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strchr、wcschr、_mbschr、_mbschr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前的地區設定或指定的 LC\_CTYPE 轉換狀態分類，尋找字串中的字元。  
  
> [!IMPORTANT]
>  `_mbschr` 和 `_mbschr_l` 不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strchr(  
   const char *str,  
   int c   
);  // C only  
char *strchr(  
   char * str,  
   int c   
); // C++ only  
const char *strchr(  
   const char * str,  
   int c   
); // C++ only  
wchar_t *wcschr(  
   const wchar_t *str,  
   wchar_t c   
); // C only  
wchar_t *wcschr(  
   wchar_t *str,  
   wchar_t c   
);  // C++ only  
const wchar_t *wcschr(  
   const wchar_t *str,  
   wchar_t c   
);  // C++ only  
unsigned char *_mbschr(  
   const unsigned char *str,  
   unsigned int c   
); // C only  
unsigned char *_mbschr(  
   unsigned char *str,  
   unsigned int c   
); // C++ only  
const unsigned char *_mbschr(  
   const unsigned char *str,  
   unsigned int c   
); // C++ only  
unsigned char *_mbschr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C only   
unsigned char *_mbschr_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbschr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 以 Null 結束的來源字串。  
  
 `c`  
 待配置的字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這些函式都會傳回指標在 `str` 第一次出現的 `c`，或者如果找不到 `c`，會回傳`NULL` 。  
  
## 備註  
 `strchr` 函式會找到在 `str`中第一次出現的 `c` ，或則傳回 `NULL`，如果找不到 `c` 。  null 結尾字元包含在搜尋中。  
  
 `wcschr` 、 `_mbschr` 和 `_mbschr_l` 是 `strchr` 的寬字元和多位元組字元版本。  `wcschr` 的引數和傳回值是寬字元字串，而 `_mbschr` 的引數和傳回值則是多位元組字元字串。  `_mbschr` 可辨識多位元組字元序列。  而且，如果字串為 null 指標，`_mbschr`則叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `_mbschr` 會傳回 `NULL` 並設定 `errno` 為 `EINVAL`。  `strchr` 和 `wcschr` 並不驗證它們的參數。  這三個函式其餘部分的運作相同。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C 裏，這些函式的第一個引數採用 `const` 的指標。  在 C\+\+ 裏，有兩個多載版本可供使用。  多載的一個版本接受 `const` 的指標並回傳 `const` 的指標。另一個則接受 `const` 的指標並回傳非 `const` 的指標。  如果 `const` 和非 `const` 的版本均可用，會定義巨集 \_CONST\_CORRECT\_OVERLOADS 。  如果您需要 C\+\+ 兩個多載版本有非 `const` 的行為，請定義符號 \_CONST\_RETURN 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcschr`|`strchr`|`_mbschr`|`wcschr`|  
|**\_n\/a**|**N\/A**|`_mbschr_l`|**N\/A**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strchr`|\<string.h\>|  
|`wcschr`|\<string.h\> 或 \<wchar.h\>|  
|`_mbschr`, `_mbschr_l`|\<mbstring.h\>|  
  
 如需更多相容性的資訊，請參閱 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strchr.c  
//   
// This program illustrates searching for a character  
// with strchr (search forward) or strrchr (search backward).  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int  ch = 'r';  
  
char string[] = "The quick brown dog jumps over the lazy fox";  
char fmt1[] =   "         1         2         3         4         5";  
char fmt2[] =   "12345678901234567890123456789012345678901234567890";  
  
int main( void )  
{  
   char *pdest;  
   int result;  
  
   printf_s( "String to be searched:\n      %s\n", string );  
   printf_s( "      %s\n      %s\n\n", fmt1, fmt2 );  
   printf_s( "Search char:   %c\n", ch );  
  
   // Search forward.   
   pdest = strchr( string, ch );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf_s( "Result:   first %c found at position %d\n",   
              ch, result );  
   else  
      printf_s( "Result:   %c not found\n", ch );  
  
   // Search backward.   
   pdest = strrchr( string, ch );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf_s( "Result:   last %c found at position %d\n", ch, result );  
   else  
      printf_s( "Result:\t%c not found\n", ch );  
}  
```  
  
  **String to be searched:**  
 **The quick brown dog jumps over the lazy fox**  
 **1         2         3         4         5**  
 **12345678901234567890123456789012345678901234567890**  
**Search char:   r**  
**Result:   first r found at position 12**  
**Result:   last r found at position 30**   
## .NET Framework 對等用法  
 [System::String::IndexOf](https://msdn.microsoft.com/en-us/library/system.string.indexof.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strpbrk、wcspbrk、\_mbspbrk、\_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strstr、wcsstr、\_mbsstr、\_mbsstr\_l](../../c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l.md)