---
title: "_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strlwr_l"
  - "_strlwr"
  - "_wcslwr_l"
  - "_mbslwr_l"
  - "_wcslwr"
  - "_mbslwr"
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
  - "_strlwr"
  - "wcslwr_l"
  - "_ftcslwr"
  - "mbslwr_l"
  - "_mbslwr"
  - "_wcslwr"
  - "strlwr_l"
  - "_tcslwr"
  - "mbslwr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcslwr 函式"
  - "_mbslwr 函式"
  - "_mbslwr_l 函式"
  - "_strlwr 函式"
  - "_strlwr_l 函式"
  - "_tcslwr 函式"
  - "_tcslwr_l 函式"
  - "_wcslwr 函式"
  - "_wcslwr_l 函式"
  - "大小寫, 轉換"
  - "轉換大小寫"
  - "轉換大小寫, CRT 函式"
  - "ftcslwr 函式"
  - "mbslwr 函式"
  - "mbslwr_l 函式"
  - "字串轉換 [C++], 大小寫"
  - "字串 [C++], 大小寫"
  - "字串 [C++], 轉換大小寫"
  - "strlwr_l 函式"
  - "tcslwr 函式"
  - "tcslwr_l 函式"
  - "wcslwr_l 函式"
ms.assetid: d279181d-2e7d-401f-ab44-6e7c2786a046
caps.latest.revision: 36
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 36
---
# _strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一個字串轉換為小寫。  更多這些函式的可用安全版本，請參閱 [\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbslwr` and `_mbslwr_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *_strlwr(  
   char * str  
);  
wchar_t *_wcslwr(  
   wchar_t * str  
);  
unsigned char *_mbslwr(  
   unsigned char * str  
);  
char *_strlwr_l(  
   char * str,  
   _locale_t locale  
);  
wchar_t *_wcslwr_l(  
   wchar_t * str,  
   _locale_t locale  
);  
unsigned char *_mbslwr_l(  
   unsigned char * str,  
   _locale_t locale   
);  
template <size_t size>  
char *_strlwr(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wcslwr(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
unsigned char *_mbslwr(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
char *_strlwr_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
wchar_t *_wcslwr_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
unsigned char *_mbslwr_l(  
   unsigned char (&str)[size],  
   _locale_t locale   
); // C++ only  
```  
  
#### 參數  
 `str`  
 將以 Null 結束之字串轉換為小寫。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 每一個這些函式都會傳回已轉換後的字符串的指標。  由於修改已完成，則傳回的指標與傳遞輸入引數的指標相同。  未保留表示錯誤的傳回值。  
  
## 備註  
 `_strlwr` 函式轉換 `str` 中的所有大寫字母為小寫取決於地區設定分類的 `LC_CTYPE` 設定。  其他字元不會受到影響。  如需`LC_CTYPE`的詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些版本沒有這種功能，without`_l` 後置字元使用當前區域設置為他們的語言環境相關的行為;版本與`_l` 後置字元是相同的，只是它們使用的，而不是通過語言環境。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 `_wcslwr` 和 `_mbslwr` 函式是 `_strlwr`寬字元和多位元組字元版本。  `_wcslwr` 的引數和傳回值是寬字元字串，而 `_mbslwr` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 如果 `str` 為 `NULL` 指標，則無效參數處理常式會被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回原始字串並將 `errno` 設為 `EINVAL` 。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcslwr`|`_strlwr`|`_mbslwr`|`_wcslwr`|  
|`_tcslwr_l`|`_strlwr_l`|`_mbslwr_l`|`_wcslwr_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strlwr`, `_strlwr_l`|\<string.h\>|  
|`_wcslwr`, `_wcslwr_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbslwr`, `_mbslwr_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strlwr.c  
// compile with: /W3  
// This program uses _strlwr and _strupr to create  
// uppercase and lowercase copies of a mixed-case string.  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The String to End All Strings!";  
   char * copy1 = _strdup( string ); // make two copies  
   char * copy2 = _strdup( string );  
  
   _strlwr( copy1 ); // C4996  
   // Note: _strlwr is deprecated; consider using _strlwr_s instead  
   _strupr( copy2 ); // C4996  
   // Note: _strupr is deprecated; consider using _strupr_s instead  
  
   printf( "Mixed: %s\n", string );  
   printf( "Lower: %s\n", copy1 );  
   printf( "Upper: %s\n", copy2 );  
  
   free( copy1 );  
   free( copy2 );  
}  
```  
  
  **Mixed: The String to End All Strings\!**  
**Lower: the string to end all strings\!**  
**Upper: THE STRING TO END ALL STRINGS\!**   
## .NET Framework 對等用法  
 [System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [\_strupr、\_strupr\_l、\_mbsupr、\_mbsupr\_l、\_wcsupr\_l、\_wcsupr](../../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)