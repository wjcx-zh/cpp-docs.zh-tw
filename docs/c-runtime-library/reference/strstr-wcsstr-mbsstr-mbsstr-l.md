---
title: "strstr、wcsstr、_mbsstr、_mbsstr_l | Microsoft Docs"
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
  - "_mbsstr"
  - "wcsstr"
  - "_mbsstr_l"
  - "strstr"
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
  - "_fstrstr"
  - "_ftcsstr"
  - "strstr"
  - "wcsstr"
  - "_mbsstr"
  - "_tcsstr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrstr 函式"
  - "_ftcsstr 函式"
  - "_mbsstr 函式"
  - "_mbsstr_l 函式"
  - "_tcsstr 函式"
  - "fstrstr 函式"
  - "ftcsstr 函式"
  - "mbsstr 函式"
  - "mbsstr_l 函式"
  - "字串 [C++], 搜尋"
  - "strstr 函式"
  - "子字串, 尋找"
  - "tcsstr 函式"
  - "wcsstr 函式"
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strstr、wcsstr、_mbsstr、_mbsstr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

回傳指向字串中欲搜尋字串第一個出現位置之指標。  
  
> [!IMPORTANT]
>  `_mbsstr` 與`_mbsstr_l`不能用於[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strstr(  
   const char *str,  
   const char *strSearch   
); // C only  
char *strstr(  
   char *str,  
   const char *strSearch   
); // C++ only  
const char *strstr(  
   const char *str,  
   const char *strSearch   
); // C++ only  
wchar_t *wcsstr(  
   const wchar_t *str,  
   const wchar_t *strSearch   
); // C only  
wchar_t *wcsstr(  
   wchar_t *str,  
   const wchar_t *strSearch   
); // C++ only  
const wchar_t *wcsstr(  
   const wchar_t *str,  
   const wchar_t *strSearch   
); // C++ only  
unsigned char *_mbsstr(  
   const unsigned char *str,  
   const unsigned char *strSearch   
); // C only  
unsigned char *_mbsstr(  
   unsigned char *str,  
   const unsigned char *strSearch   
); // C++ only  
const unsigned char *_mbsstr(  
   const unsigned char *str,  
   const unsigned char *strSearch   
); // C++ only  
unsigned char *_mbsstr_l(  
   const unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C only  
unsigned char *_mbsstr_l(  
   unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsstr_l(  
   const unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 從中搜尋的 NULL 結尾字串。  
  
 `strSearch`  
 要搜尋的目標 NULL 結尾字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 回傳指向 `str` 中第一個出現的 `strSearch` 的位置的指標，如果無法在 `str` 中找到`strSearch` 則回傳 `NULL` 。  如果 `strSearch` 指向長度為零的字串，函式會回傳 `str` 。  
  
## 備註  
 `strstr` 函式傳回指向 `str` 裏第一個出現的 `strSearch` 的指標。  搜尋不包含結束的 NULL 字元。  `wcsstr` 是 `strstr` 的寬字元版本，而 `_mbsstr` 則是多位元組字元版本  `wcsstr` 的引數和傳回值是寬字元字串，而 `_mbsstr` 的引數和傳回值則是多位元組字元字串。  `_mbsstr` 會驗證其參數。  如果 `str` 或 `strSearch` 是 `NULL`，會調用無效參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `_mbsstr` 會設定 `errno` 為 `EINVAL` 並回傳 0 。  `strstr` 和 `wcsstr` 並不驗證它們的參數。  這三個函式其餘部分的運作相同。  
  
> [!IMPORTANT]
>  這些函式可能會造成緩衝區滿溢問題的威脅。  緩衝區滿溢問題可用來攻擊系統，因為它們可以允許執行任意程式碼，這可能導致權限不必要的提升。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
 在 C 裏，這些函式的第一個引數採用 `const` 的指標。  在 C\+\+ 裏，有兩個多載版本可供使用。  一個接受 `const` 的指標的多載版本會回傳 `const` 的指標。另一個接受 `const` 的指標的版本則回傳非 `const` 的指標。  如果 `const` 和非 `const` 的版本均可用，會定義巨集 \_CONST\_CORRECT\_OVERLOADS 。  如果您需要 C\+\+ 兩個多載版本有非 `const` 的行為，請定義符號 \_CONST\_RETURN 。  
  
 輸出值會受到 `LC_CTYPE` 的區域類別設定影響。如需詳細資訊，請參閱 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些沒有 `_l` 後綴的函式之版本會對區域相關的行為使用目前的地區設定；而以 `_l` 為後綴的版本則相同，但會使用傳入的區域參數設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|  
|**N\/A**|**N\/A**|`_mbsstr_l`|**N\/A**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strstr`|\<string.h\>|  
|`wcsstr`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strstr.c  
  
#include <string.h>  
#include <stdio.h>  
  
char str[] =    "lazy";  
char string[] = "The quick brown dog jumps over the lazy fox";  
char fmt1[] =   "         1         2         3         4         5";  
char fmt2[] =   "12345678901234567890123456789012345678901234567890";  
  
int main( void )  
{  
   char *pdest;  
   int  result;  
   printf( "String to be searched:\n   %s\n", string );  
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );  
   pdest = strstr( string, str );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf( "%s found at position %d\n", str, result );  
   else  
      printf( "%s not found\n", str );  
}  
```  
  
  **待搜尋字串：**  
 **The quick brown dog jumps over the lazy fox**  
 **1         2         3         4         5**  
 **12345678901234567890123456789012345678901234567890**  
**lazy發現於位置36**   
## .NET Framework 對等用法  
 [System::String::IndexOf](https://msdn.microsoft.com/en-us/library/system.string.indexof.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strpbrk、wcspbrk、\_mbspbrk、\_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [basic\_string::find](../Topic/basic_string::find.md)