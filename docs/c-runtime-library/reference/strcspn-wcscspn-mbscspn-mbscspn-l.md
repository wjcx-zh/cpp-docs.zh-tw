---
title: "strcspn、wcscspn、_mbscspn、_mbscspn_l | Microsoft Docs"
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
  - "_mbscspn_l"
  - "wcscspn"
  - "_mbscspn"
  - "strcspn"
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
  - "strcspn"
  - "_mbscspn"
  - "wcscspn"
  - "_ftcscspn"
  - "_tcscspn"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcscspn 函式"
  - "_mbscspn 函式"
  - "_mbscspn_l 函式"
  - "_tcscspn 函式"
  - "ftcscspn 函式"
  - "mbscspn 函式"
  - "mbscspn_l 函式"
  - "strcspn 函式"
  - "字串 [C++], 搜尋"
  - "tcscspn 函式"
  - "wcscspn 函式"
ms.assetid: f73f51dd-b533-4e46-ba29-d05c553708a6
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcspn、wcscspn、_mbscspn、_mbscspn_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回字串中第一個相符於字元集的字元索引。  
  
> [!IMPORTANT]
>  `_mbschr` and `_mbschr_l`不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
size_t strcspn(  
   const char *str,  
   const char *strCharSet   
);  
size_t wcscspn(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
);  
size_t _mbscspn(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
);  
size_t _mbscspn_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `str`  
 以 Null 結束的搜尋字串。  
  
 `strCharSet`  
 以 Null 結束的字元集。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這些函式傳回 `strCharSet` 中第一個字元在 `str` 中的索引。  如果在 `str` 中的字元都不是 `strCharSet`，則傳回值是 `str`的長度。  
  
 未保留表示錯誤的傳回值。  
  
## 備註  
 `wcscspn` 和 `_mbscspn` 是 `strcspn` 的寬字元和多位元組字元版本。  `wcscspn` 的引數是寬字元字串，而 `_mbscspn` 的引數和傳回值則是多位元組字元字串。  
  
 `_mbscspn` 會驗證其參數。  如果 `str` 或 `strCharSet` 為 null 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，則函式會傳回 0 並將 `errno` 設定為 `EINVAL`。  `strcspn` 和 `wcscspn` 並不驗證它們的參數。  這三個函式其餘部分的運作相同。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscspn`|`strcspn`|`_mbscspn`|`wcscspn`|  
|`n/a`|`n/a`|`_mbscspn_l`|`n/a`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strcspn`|\<string.h\>|  
|`wcscspn`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscspn`, `_mbscspn_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strcspn.c  
  
#include <string.h>  
#include <stdio.h>  
  
void test( const char * str, const char * strCharSet )  
{  
   int pos = strcspn( str, strCharSet );  
   printf( "strcspn( \"%s\", \"%s\" ) = %d\n", str, strCharSet, pos );      
}  
  
int main( void )  
{  
   test( "xyzbxz", "abc" );  
   test( "xyzbxz", "xyz" );  
   test( "xyzbxz", "no match" );  
   test( "xyzbxz", "" );  
   test( "", "abc" );  
   test( "", "" );  
}  
```  
  
  **strcspn\( "xyzbxz", "abc" \) \= 3**  
**strcspn\( "xyzbxz", "xyz" \) \= 0**  
**strcspn\( "xyzbxz", "no match" \) \= 6**  
**strcspn\( "xyzbxz", "" \) \= 6**  
**strcspn\( "", "abc" \) \= 0**  
**strcspn\( "", "" \) \= 0**   
## .NET Framework 對等用法  
 [System::String::Substring](https://msdn.microsoft.com/en-us/library/system.string.substring.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)