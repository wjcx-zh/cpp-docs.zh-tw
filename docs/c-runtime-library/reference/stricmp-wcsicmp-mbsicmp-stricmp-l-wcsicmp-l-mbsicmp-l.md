---
title: "_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l | Microsoft Docs"
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
  - "_stricmp_l"
  - "_mbsicmp"
  - "_wcsicmp"
  - "_mbsicmp_l"
  - "_stricmp"
  - "_wcsicmp_l"
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
  - "_ftcsicmp"
  - "_stricmp"
  - "wcsicmp_l"
  - "_wcsicmp"
  - "_tcsicmp"
  - "_strcmpi"
  - "stricmp_l"
  - "_mbsicmp"
  - "_fstricmp"
  - "mbsicmp_l"
  - "mbsicmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstricmp 函式"
  - "_ftcsicmp 函式"
  - "_mbsicmp 函式"
  - "_mbsicmp_l 函式"
  - "_strcmpi 函式"
  - "_stricmp 函式"
  - "_stricmp_l 函式"
  - "_tcsicmp 函式"
  - "_wcsicmp 函式"
  - "_wcsicmp_l 函式"
  - "fstricmp 函式"
  - "ftcsicmp 函式"
  - "mbsicmp 函式"
  - "mbsicmp_l 函式"
  - "stricmp_l 函式"
  - "字串比較 [C++], 小寫"
  - "字串 [C++], 比較"
  - "tcsicmp 函式"
  - "wcsicmp_l 函式"
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行字串的不區分大小寫比較。  
  
> [!IMPORTANT]
>  在 Windows 執行階段中執行的應用程式中無法使用 `_mbsicmp` 和 `_mbsicmp_l`。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _stricmp(  
   const char *string1,  
   const char *string2   
);  
int _wcsicmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricmp_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicmp_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `string1, string2`  
 以 Null 結束的待比較字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回值，表示 `string1` 對 `string2` 的關聯，如下所示。  
  
|傳回值|描述|  
|---------|--------|  
|\< 0|`string1` 小於 `string2`|  
|0|`string1` 等於 `string2`|  
|\> 0|`string1` 大於 `string2`|  
  
 發生錯誤時，`_mbsicmp` 會傳回 `_NLSCMPERROR` \(定義在 \<string.h\> 和 \<mbstring.h\> 中\)。  
  
## 備註  
 `_stricmp` 函式一般會在每個字元轉換成小寫之後，比較 `string1` 和 `string2`，並傳回表示它們關聯性的值。  `_stricmp` 與 `_stricoll` 不同之處為，`_stricmp` 比較只會受到 `LC_CTYPE` 的影響，它會決定哪些字元為大寫和小寫。  `_stricoll` 函式會根據地區設定的 `LC_CTYPE` 和 `LC_COLLATE` 分類，其中包括大小寫和定序排序，來比較字串。  如需 `LC_COLLATE` 分類的詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 和[地區設定分類](../../c-runtime-library/locale-categories.md)。  沒有 `_l` 字尾的這些函式版本，會針對與地區設定相依的行為，使用目前的地區設定。  具有字尾的版本也一樣，只不過它們改用傳入的地區設定。  如果尚未設定地區設定，會使用 C 地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
> [!NOTE]
>  `_stricmp` 相當於 `_strcmpi`。  它們可以交替使用，但 `_stricmp` 是慣用的標準。  
  
 `_strcmpi` 函式相當於 `_stricmp`，而且只是為了回溯相容性而提供。  
  
 因為 `_stricmp` 有小寫的比較，這可能會導致非預期的行為。  
  
 為了說明 `_stricmp` 的大小寫轉換會在何時影響比較的結果，我們假設您有兩個字串 JOHNSTON 和 JOHN\_HENRY。  字串 JOHN\_HENRY 會被視為少於 JOHNSTON，因為 "\_" 的 ASCII 值比小寫 S 更低。  事實上，所有 ASCII 值在 96 和 91 之間的任何字元都會被視為小於任何字母。  
  
 如果改用 [strcmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) 函式取代 `_stricmp`，JOHN\_HENRY 將會大於 JOHNSTON。  
  
 `_wcsicmp` 和 `_mbsicmp` 分別是 `_stricmp` 的寬字元版本和多位元組字元版本。  `_wcsicmp` 的引數和傳回值是寬字元字串；`_mbsicmp` 的引數則是多位元組字元字串。  `_mbsicmp` 會根據目前的多位元組字碼頁，辨識多位元組字元序列，並在發生錯誤時傳回 `_NLSCMPERROR`。  如需詳細資訊，請參閱[字碼頁](../../c-runtime-library/code-pages.md)。  除此之外，這三個函式的行為相同。  
  
 `_wcsicmp` 和 `wcscmp` 的行為相同，除了 `wcscmp` 不會在進行比較之前，將其引數轉換成小寫。  `_mbsicmp` 和 `_mbscmp` 的行為相同，除了 `_mbscmp` 不會在進行比較之前，將其引數轉換成小寫。  
  
 您必須為 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 呼叫 `_wcsicmp`，以使用「拉丁文 1」的字元。  依預設 C 地區設定會生效，因此，舉例來說，ä 不會等於 Ä。  搭配 C 地區設定以外的任何地區設定呼叫 `setlocale` 會在 `_wcsicmp` 呼叫之前。  下列範例示範地區設定如何影響 `_wcsicmp`：  
  
```  
// crt_stricmp_locale.c  
#include <string.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main() {  
   setlocale(LC_ALL,"C");   // in effect by default  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails  
   setlocale(LC_ALL,"");  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds  
}  
```  
  
 替代方法是呼叫 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)，並且將傳回的地區設定物件做為參數傳遞至 `_wcsicmp_l`。  
  
 這些函式全都會驗證它們的參數。  若 `string1` 或 `string2` 其中一個為 null 指標，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 `_NLSCMPERROR`，並將 `errno` 設為 `EINVAL`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsicmp`|`_stricmp`|`_mbsicmp`|`_wcsicmp`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_stricmp`, `_stricmp_l`|\<string.h\>|  
|`_wcsicmp`, `_wcsicmp_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsicmp`, `_mbsicmp_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_stricmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
  **Compare strings:**  
 **The quick brown dog jumps over the lazy fox**  
 **The QUICK brown dog jumps over the lazy fox**  
 **strcmp:   String 1 is greater than string 2**  
 **\_stricmp:  String 1 is equal to string 2**   
## .NET Framework 對等用法  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [\_memicmp、\_memicmp\_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)