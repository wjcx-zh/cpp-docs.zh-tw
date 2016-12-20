---
title: "strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l | Microsoft Docs"
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
  - "_mbslen"
  - "_mbslen_l"
  - "_mbstrlen"
  - "wcslen"
  - "_mbstrlen_l"
  - "strlen"
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
  - "_mbstrlen"
  - "wcslen"
  - "_tcslen"
  - "_ftcslen"
  - "strlen"
  - "_mbslen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcslen 函式"
  - "_mbslen 函式"
  - "_mbslen_l 函式"
  - "_mbstrlen 函式"
  - "_mbstrlen_l 函式"
  - "_tcslen 函式"
  - "ftcslen 函式"
  - "長度, 字串"
  - "mbslen 函式"
  - "mbslen_l 函式"
  - "mbstrlen 函式"
  - "mbstrlen_l 函式"
  - "字串長度, 取得"
  - "字串 [C++], 取得長度"
  - "strlen 函式"
  - "tcslen 函式"
  - "wcslen 函式"
ms.assetid: 16462f2a-1e0f-4eb3-be55-bf1c83f374c2
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前的地區設定或指定的地區設定取得字串的長度。  這些函式已有更安全的版本可用，請參閱 [strnlen、strnlen\_s、wcsnlen、wcsnlen\_s、\_mbsnlen、\_mbsnlen\_l、\_mbstrnlen、\_mbstrnlen\_l](../../c-runtime-library/reference/strnlen-strnlen-s.md)。  
  
> [!IMPORTANT]
>  在 Windows 執行階段中執行的應用程式中無法使用 `_mbslen`、`_mbslen_l`、`_mbstrlen` 和 `_mbstrlen_l`。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
size_t strlen(    const char *str ); size_t wcslen(    const wchar_t *str  ); size_t _mbslen(    const unsigned char *str  ); size_t _mbslen_l(    const unsigned char *str,    _locale_t locale ); size_t _mbstrlen(    const char *str ); size_t _mbstrlen_l(    const char *str,    _locale_t locale );  
```  
  
#### 參數  
 `str`  
 以 Null 結束的字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這些函式每個都會傳回 `str` 中的字元數，但不包含終端 `NULL`。  不會保留傳回值以指出錯誤，但 `_mbstrlen` 和 `_mbstrlen_l` 除外，其會在字串包含無效的多位元組字元時傳回 `((size_t)(-1))`。  
  
## 備註  
 `strlen` 會將字串解譯為單一位元組字元字串，因此即使字串包含多位元組字元，傳回值也會一律等於位元組數。  `wcslen` 是寬字元版本的 `strlen`；`wcslen` 的引數是寬字元字串，且字元的計數也是使用寬 \(二位元\) 字元。  否則，`wcslen` 和 `strlen` 的行為即會相同。  
  
 **安全性提示** 這些函式可能會帶來緩衝區滿溢問題所引發的威脅。  緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。  如需詳細資訊，請參閱[避免緩衝區滿溢](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcslen`|`strlen`|`strlen`|`wcslen`|  
|`_tcsclen`|`strlen`|`_mbslen`|`wcslen`|  
|`_tcsclen_l`|`strlen`|`_mbslen_l`|`wcslen`|  
  
 `_mbslen` 和 `_mbslen_l` 會傳回多位元組字元字串中的多位元組字元數，但不會測試多位元組字元的有效性。  `_mbstrlen` 和 `_mbstrlen_l` 會測試多位元組字元的有效性，並辨識多位元組字元的序列。  若傳遞至 `_mbstrlen` 或 `_mbstrlen_l` 包含對字碼頁而言為無效的多位元組字元，則函式會傳回 \-1，並將 `errno` 設為 `EILSEQ`。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響；如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些沒有 `_l` 後置字元的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 `_l` 後置字元的版本也一樣，只不過它們會改用傳遞的地區設定參數。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strlen`|\<string.h\>|  
|`wcslen`|\<string.h\> 或 \<wchar.h\>|  
|`_mbslen`, `_mbslen_l`|\<mbstring.h\>|  
|`_mbstrlen`, `_mbstrlen_l`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strlen.c  
// Determine the length of a string. For the multi-byte character  
// example to work correctly, the Japanese language support for  
// non-Unicode programs must be enabled by the operating system.  
  
#include <string.h>  
#include <locale.h>  
  
int main()  
{  
   char* str1 = "Count.";  
   wchar_t* wstr1 = L"Count.";  
   char * mbstr1;  
   char * locale_string;  
  
   // strlen gives the length of single-byte character string  
   printf("Length of '%s' : %d\n", str1, strlen(str1) );  
  
   // wstrlen gives the length of a wide character string  
   wprintf(L"Length of '%s' : %d\n", wstr1, wcslen(wstr1) );  
  
   // A multibyte string: [A] [B] [C] [katakana A] [D] [\0]  
   // in Code Page 932. For this example to work correctly,  
   // the Japanese language support must be enabled by the  
   // operating system.  
   mbstr1 = "ABC" "\x83\x40" "D";  
  
   locale_string = setlocale(LC_CTYPE, "Japanese_Japan");  
  
   if (locale_string == NULL)  
   {  
      printf("Japanese locale not enabled. Exiting.\n");  
      exit(1);  
   }  
   else  
   {  
      printf("Locale set to %s\n", locale_string);  
   }  
  
   // _mbslen will recognize the Japanese multibyte character if the  
   // current locale used by the operating system is Japanese  
   printf("Length of '%s' : %d\n", mbstr1, _mbslen(mbstr1) );  
  
   // _mbstrlen will recognize the Japanese multibyte character  
   // since the CRT locale is set to Japanese even if the OS locale  
   // isnot.   
   printf("Length of '%s' : %d\n", mbstr1, _mbstrlen(mbstr1) );  
   printf("Bytes in '%s' : %d\n", mbstr1, strlen(mbstr1) );     
  
}  
```  
  
  **'Count.' 的長度 : 6**  
**'Count.' 的長度 : 6**  
**'ABCァD' 的長度 : 5**  
**'ABCァD' 的長度 : 5**  
**'ABCァD' 的位元組數 : 6**   
## .NET Framework 對等用法  
 [System::String::Length](https://msdn.microsoft.com/en-us/library/system.string.length.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)