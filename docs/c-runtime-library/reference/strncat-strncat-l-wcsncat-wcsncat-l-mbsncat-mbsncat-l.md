---
title: "strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l | Microsoft Docs"
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
  - "strncat"
  - "_strncat_l"
  - "_mbsncat"
  - "_mbsncat_l"
  - "wcsncat"
  - "wcsncat_l"
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
  - "_tcsncat_l"
  - "_wcsncat_l"
  - "_tcsnccat_l"
  - "_mbsncat"
  - "_strncat_l"
  - "strncat"
  - "_tcsnccat"
  - "_mbsncat_l"
  - "_ftcsncat"
  - "wcsncat"
  - "_tcsncat"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsncat 函式"
  - "_mbsncat 函式"
  - "_mbsncat_l 函式"
  - "_tcsncat 函式"
  - "_tcsncat_l 函式"
  - "_tcsnccat 函式"
  - "_tcsnccat_l 函式"
  - "附加字串"
  - "字元 [C++], 附加至字串"
  - "串連字串"
  - "ftcsncat 函式"
  - "mbsncat 函式"
  - "mbsncat_l 函式"
  - "字串串連 [C++]"
  - "字串 [C++], 附加"
  - "strncat 函式"
  - "tcsncat 函式"
  - "tcsncat_l 函式"
  - "tcsnccat 函式"
  - "tcsnccat_l 函式"
  - "wcsncat 函式"
ms.assetid: de67363b-68c6-4ca5-91e3-478610ad8159
caps.latest.revision: 29
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

曾加一個字串的字元。  這些函式已有更安全的版本可用，請參閱 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) 。  
  
> [!IMPORTANT]
>  `_mbsncat` and `_mbsncat_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strncat(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
wchar_t *wcsncat(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
unsigned char *_mbsncat(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count  
);  
unsigned char *_mbsncat_l(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
char *strncat(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
wchar_t *wcsncat(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncat(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
unsigned char *_mbsncat_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `strDest`  
 以 Null 結束的結束字串。  
  
 `strSource`  
 以 Null 結束的來源字串。  
  
 `count`  
 要附加的字元數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回一個指標到目的地字串。  未保留表示錯誤的傳回值。  
  
## 備註  
 `strncat` 函式，附加至多， `strSource` 第一個 `count` 字元至 `strDest`中。  `strSource` 的初始字元覆寫 `strDest`結束的 null 字元。  如果 null 字元出現在 `strSource` ， `count` 字元附加前，附加 `strncat` 從 `strSource`中的所有字元，由 null 字元。  如果 `count` 大於 `strSource` 的長度，長度為 `strSource` 而非 `count` 的。  在所有情況下，結果產生的字串是以 null 字元結束。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
> [!IMPORTANT]
>  `strncat` 不會檢查 `strDest`的足夠的空間;所以緩衝區滿溢的一個可能的原因。  記住 `count` 條件附加的字元數;會在 `strDest`大小的一項限制。  請參閱下列範例。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
 `wcsncat` 和 `_mbsncat` 是 `strncat` 的寬字元和多位元組字元版本。  `wcsncat` 的字串引數和傳回值是寬字元字串，而 `_mbsncat` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，這些函式有範本多載。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncat`|`strncat`|`_mbsnbcat`|`wcsncat`|  
|`_tcsncat_l`|`_strncat_l`|`_mbsnbcat_l`|`_wcsncat_l`|  
  
> [!NOTE]
>  `_strncat_l` 和 `_wcsncat_l` 沒有地區設定相關屬性並不會直接呼叫。  它們提供內部所使用的 `_tcsncat_l`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strncat`|\<string.h\>|  
|`wcsncat`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncat`|\<mbstring.h\>|  
|`_mbsncat_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strncat.c  
// Use strcat and strncat to append to a string.  
#include <stdlib.h>  
  
#define MAXSTRINGLEN 39  
  
char string[MAXSTRINGLEN+1];  
// or char *string = malloc(MAXSTRINGLEN+1);  
  
void BadAppend( char suffix[], int n )  
{  
   strncat( string, suffix, n );  
}  
  
void GoodAppend( char suffix[], size_t n )  
{  
   strncat( string, suffix, __min( n, MAXSTRINGLEN-strlen(string)) );  
}  
  
int main( void )  
{  
   string[0] = '\0';  
   printf( "string can hold up to %d characters\n", MAXSTRINGLEN );  
  
   strcpy( string, "This is the initial string!" );  
   // concatenate up to 20 characters...  
   BadAppend( "Extra text to add to the string...", 20 );  
   printf( "After BadAppend :  %s (%d chars)\n", string, strlen(string) );  
  
   strcpy( string, "This is the initial string!" );  
   // concatenate up to 20 characters...  
   GoodAppend( "Extra text to add to the string...", 20 );  
   printf( "After GoodAppend:  %s (%d chars)\n", string, strlen(string) );  
}  
```  
  
## Output  
  
```  
string can hold up to 39 characters  
After BadAppend :  This is the initial string!Extra text to add to (47 chars)  
After GoodAppend:  This is the initial string!Extra text t (39 chars)  
```  
  
 請注意 `BadAppend` 造成緩衝區滿溢。  
  
## .NET Framework 對等用法  
 [System::String::Concat](https://msdn.microsoft.com/en-us/library/system.string.concat.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)