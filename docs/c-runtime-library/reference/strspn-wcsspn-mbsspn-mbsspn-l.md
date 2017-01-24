---
title: "strspn、wcsspn、_mbsspn、_mbsspn_l | Microsoft Docs"
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
  - "_mbsspn_l"
  - "wcsspn"
  - "strspn"
  - "_mbsspn"
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
  - "_ftcsspn"
  - "wcsspn"
  - "_mbsspn"
  - "_tcsspn"
  - "strspn"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsspn 函式"
  - "_mbsspn 函式"
  - "_mbsspn_l 函式"
  - "_tcsspn 函式"
  - "ftcsspn 函式"
  - "mbsspn 函式"
  - "mbsspn_l 函式"
  - "字串 [C++], 搜尋"
  - "strspn 函式"
  - "子字串, 尋找"
  - "tcsspn 函式"
  - "wcsspn 函式"
ms.assetid: d077284a-809f-4068-959e-c6d6262677eb
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strspn、wcsspn、_mbsspn、_mbsspn_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回第一個字元的索引，在字串，不屬於一組字元。  
  
> [!IMPORTANT]
>  `_mbsspn` and `_mbsspn_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
size_t strspn(  
   const char *str,  
   const char *strCharSet   
);  
size_t wcsspn(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
);  
size_t _mbsspn(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
);  
size_t _mbsspn_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `str`  
 從中搜尋的 NULL 結尾字串。  
  
 `strCharSet`  
 以 Null 結束的字元集。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回指定完全包含在 `strCharSet`字元的子字串長度的整數值是 `str`*。*如果 `str` 是一個字元開始不是 `strCharSet`*，* 函式會傳回 0。  
  
## 備註  
 `strspn` 函式會傳回不屬於集合在 `strCharSet`中字元的第一個字元在 `str` 中的索引。  搜尋不包含結束的 NULL 字元。  
  
 `wcsspn` 和 `_mbsspn`是寬字符和多位元字符版本`strspn`**。**`wcsspn` 的引數是寬字元字串，而 `_mbsspn` 的引數和傳回值則是多位元組字元字串。  `_mbsspn` 會驗證其參數。  如果 `str`或`strCharSet`是`NULL` 無效參數調用處理程序，如以下所描述[參數驗證](../../c-runtime-library/parameter-validation.md)。  如果允許繼續執行， `_mbspn` 會設定 `errno` 為 `EINVAL` 並回傳 0 。  `strspn` 和 `wcsspn` 並不驗證它們的參數。  這三個函式其餘部分的運作相同。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsspn`|`strspn`|`_mbsspn`|`wcsspn`|  
|**N\/A**|**N\/A**|`_mbsspn_l`|**N\/A**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strspn`|\<string.h\>|  
|`wcsspn`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsspn`, `_mbsspn_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strspn.c  
// This program uses strspn to determine  
// the length of the segment in the string "cabbage"  
// consisting of a's, b's, and c's. In other words,  
// it finds the first non-abc letter.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[] = "cabbage";  
   int  result;  
   result = strspn( string, "abc" );  
   printf( "The portion of '%s' containing only a, b, or c "  
           "is %d bytes long\n", string, result );  
}  
```  
  
  **包含」a、b、c 只"循環白菜區段長度為 5 個位元組**   
## .NET Framework 對等用法  
 [System::String::Substring](https://msdn.microsoft.com/en-us/library/system.string.substring.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strspnp、\_wcsspnp、\_mbsspnp、\_mbsspnp\_l](../../c-runtime-library/reference/strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)