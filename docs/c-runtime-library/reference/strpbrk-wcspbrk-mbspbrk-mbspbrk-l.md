---
title: "strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbspbrk"
  - "wcspbrk"
  - "_mbspbrk_l"
  - "strpbrk"
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
  - "_fstrpbrk"
  - "_mbspbrk"
  - "strpbrk"
  - "_tcspbrk"
  - "_ftcspbrk"
  - "wcspbrk"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fstrpbrk 函式"
  - "_ftcspbrk 函式"
  - "_mbspbrk 函式"
  - "_mbspbrk_l 函式"
  - "_tcspbrk 函式"
  - "字元集 [C++], 掃描字串以找出字元"
  - "字元 [C++], 掃描字串"
  - "fstrpbrk 函式"
  - "ftcspbrk 函式"
  - "mbspbrk 函式"
  - "mbspbrk_l 函式"
  - "字串 [C++], 掃描中"
  - "strpbrk 函式"
  - "tcspbrk 函式"
  - "wcspbrk 函式"
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

掃描字串中是否有指定字元集中的字元。  
  
> [!IMPORTANT]
>  `_mbspbrk` and `_mbspbrk_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C only  
char *strpbrk(  
   char *str,  
   const char *strCharSet   
); // C++ only  
const char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C++ only  
wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C only  
wchar_t *wcspbrk(  
   wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
const wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C only  
unsigned char *_mbspbrk(  
   unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
const unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C only  
unsigned char *_mbspbrk_l(  
   unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char* strCharSet,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 以 Null 結束的搜尋字串。  
  
 `strCharSet`  
 以 Null 結束的字元集。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果兩個字串引數沒有共同字元，傳回 `strCharSet` 中任何一個字元在 `str` 第一次出現的位置或 `NULL` 指標。  
  
## 備註  
 `strpbrk` 函式會傳回指標指向 `strCharSet` 中的字元第一次 `str` 中出現的位置。  搜尋不包含結束的 NULL 字元。  
  
 `wcspbrk` 和 `_mbspbrk` 是 `strpbrk` 的寬字元和多位元組字元版本。  `wcspbrk` 的引數和傳回值是寬字元字串，而 `_mbspbrk` 的引數和傳回值則是多位元組字元字串。  
  
 `_mbspbrk` 會驗證其參數。  如果 `str` 或 `strCharSet` 是 `NULL`，會觸發無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `_mbspbrk` 會傳回 `NULL` 並設定 `errno` 為 `EINVAL`。  `strpbrk` 和 `wcspbrk` 並不驗證它們的參數。  這三個函式其餘部分的運作相同。  
  
 `_mbspbrk` 與 `_mbscspn` 類似，除了 `_mbspbrk` 傳回指標而非 [size\_t](../../c-runtime-library/standard-types.md)型別的值。  
  
 在 C 裏，這些函式的第一個引數採用 `const` 的指標。  在 C\+\+ 裏，有兩個多載版本可供使用。  多載的一個版本接受 `const` 的指標並回傳 `const` 的指標。另一個則接受 `const` 的指標並回傳非 `const` 的指標。  如果 `const` 和非 `const` 的版本均可用，會定義巨集 \_CONST\_CORRECT\_OVERLOADS 。  如果您需要 C\+\+ 兩個多載版本有非 `const` 的行為，請定義符號 \_CONST\_RETURN 。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  沒有 `_l` 後綴的程式版本在這些地區相依的行為上使用目前的地區設定；有 `_l` 後綴的版本也是一樣，除了它會使用傳入的地區設定參數之外。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|  
|**N\/A**|**N\/A**|`_mbspbrk_l`|**N\/A**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strpbrk`|\<string.h\>|  
|`wcspbrk`|\<string.h\> 或 \<wchar.h\>|  
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h\>|  
  
 如需更多相容性的資訊，請參閱 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strpbrk.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";  
   char *result = NULL;  
  
   // Return pointer to first digit in "string".  
   printf( "1: %s\n", string );  
   result = strpbrk( string, "0123456789" );  
   printf( "2: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "3: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "4: %s\n", result );  
}  
```  
  
  **1: The 3 men and 2 boys ate 5 pigs**  
**2: 3 men and 2 boys ate 5 pigs**  
**3: 2 boys ate 5 pigs**  
**4: 5 pigs**   
## .NET Framework 對等用法  
 [System::String::IndexOfAny](https://msdn.microsoft.com/en-us/library/system.string.indexofany.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strchr、wcschr、\_mbschr、\_mbschr\_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)