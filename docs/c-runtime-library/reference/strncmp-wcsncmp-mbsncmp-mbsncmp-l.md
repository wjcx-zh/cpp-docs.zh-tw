---
title: "strncmp、wcsncmp、_mbsncmp、_mbsncmp_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strncmp"
  - "_mbsncmp"
  - "wcsncmp"
  - "_mbsncmp_l"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ftcsnccmp"
  - "_ftcsncmp"
  - "_tcsncmp"
  - "_tcsnccmp"
  - "strncmp"
  - "_mbsncmp"
  - "wcsncmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsnccmp 函式"
  - "_ftcsncmp 函式"
  - "_mbsncmp 函式"
  - "_mbsncmp_l 函式"
  - "_tcsnccmp 函式"
  - "_tcsncmp 函式"
  - "字元 [C++], 比較"
  - "ftcsnccmp 函式"
  - "ftcsncmp 函式"
  - "mbsncmp 函式"
  - "mbsncmp_l 函式"
  - "字串比較 [C++], strncmp 函式"
  - "字串 [C++], 比較其字元"
  - "strncmp 函式"
  - "tcsnccmp 函式"
  - "tcsncmp 函式"
  - "wcsncmp 函式"
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# strncmp、wcsncmp、_mbsncmp、_mbsncmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比較最多兩個字串的指定字元計數。  
  
> [!IMPORTANT]
>  在 Windows 執行階段中執行的應用程式中無法使用 `_mbsncmp` 和 `_mbsncmp_l`。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int strncmp(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int wcsncmp(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsncmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,   
   _locale_t locale  
);int _mbsnbcmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### 參數  
 `string1, string2`  
 要比較的字串。  
  
 `count`  
 要比較的字元數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回值，表示 `string1` 子字串和 `string2` 子字串的關聯，如下所示。  
  
|傳回值|描述|  
|---------|--------|  
|\< 0|`string1` 子字串小於 `string2` 子字串|  
|0|`string1` 子字串與 `string2` 子字串相同|  
|\> 0|`string1` 子字串大於 `string2` 子字串|  
  
 參數驗證錯誤時，`_mbsncmp` 和 `_mbsncmp_l` 會傳回 `_NLSCMPERROR` \(定義在 \<string.h\> 和 \<mbstring.h\> 中\)。  
  
## 備註  
 `strncmp` 函式會執行 `count` 和 `string1` 中最多第一個 `string2` 字元的序數比較，並傳回指出子字串之間關聯性的值。  `strncmp` 是 `_strnicmp` 的區分大小寫版本。  `wcsncmp` 和 `_mbsncmp` 是 `_wcsnicmp` 和 `_mbsnicmp` 的區分大小寫版本。  
  
 `wcsncmp` 和 `_mbsncmp` 分別是 `strncmp` 的寬字元版本和多位元組字元版本。  `wcsncmp` 的引數是寬字元字串；`_mbsncmp` 的引數則是多位元組字元字串。  `_mbsncmp` 會根據多位元組字碼頁，辨識多位元組字元序列，並在發生錯誤時傳回 `_NLSCMPERROR`。  
  
 此外，`_mbsncmp` 和 `_mbsncmp_l` 也會驗證參數。  如果 `string1` 或 `string2` 為 null 指標，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則 `_mbsncmp` 和 `_mbsncmp_l` 會傳回 `_NLSCMPERROR`，且 `errno` 設為 `EINVAL`。  `strncmp` 和 `wcsncmp` 不會驗證其參數。  除此之外，這些函式的行為相同。  
  
 比較 `_mbsncmp` 和 `_mbsncmp_l` 的行為會受到地區設定的 `LC_CTYPE` 分類設定所影響。  這會控制對多位元組字元的開頭和結尾位元組的偵測。  如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  `_mbsncmp` 函式使用目前的地區設定進行這項與地區設定相關的行為。  `_mbsncmp_l` 函式相同，但會改用 `locale` 參數。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  如果地區設定是單一位元組的地區設定，則這些函式的行為等同於 `strncmp`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnccmp`|`strncmp`|`_mbsncmp`|`wcsncmp`|  
|`_tcsncmp`|`strncmp`|`_mbsnbcmp`|`wcsncmp`|  
|`_tccmp`|巨集或內嵌函式的對應|`_mbsncmp`|巨集或內嵌函式的對應|  
|**不適用**|**不適用**|`_mbsncmp_l`|**不適用**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strncmp`|\<string.h\>|  
|`wcsncmp`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncmp`, `_mbsncmp_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strncmp.c  
#include <string.h>  
#include <stdio.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown fox jumps over the lazy dog";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
   printf( "Compare strings:\n      %s\n      %s\n\n",  
           string1, string2 );  
   printf( "Function:   strncmp (first 10 characters only)\n" );  
   result = strncmp( string1, string2 , 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n\n", tmp );  
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );  
   result = _strnicmp( string1, string2, 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n", tmp );  
}  
```  
  
  **Compare strings:**  
 **The quick brown dog jumps over the lazy fox**  
 **The QUICK brown fox jumps over the lazy dog**  
**Function:   strncmp \(first 10 characters only\)**  
**Result:      String 1 is greater than string 2**  
**Function:   strnicmp \_strnicmp \(first 10 characters only\)**  
**Result:      String 1 is equal to string 2**   
## .NET Framework 對等用法  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_mbsnbicmp、\_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)