---
title: "strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l | Microsoft Docs"
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
  - "_mbsncpy_s_l"
  - "wcsncpy_s"
  - "_strncpy_s_l"
  - "strncpy_s"
  - "_mbsncpy_s"
  - "_wcsncpy_s_l"
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
  - "_tcsncpy_s"
  - "_wcsncpy_s_l"
  - "strncpy_s"
  - "_strncpy_s_l"
  - "wcsncpy_s"
  - "_tcsncpy_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcpy_s 函式"
  - "_mbsnbcpy_s_l 函式"
  - "_strncpy_s_l 函式"
  - "_tcsncpy_s 函式"
  - "_tcsncpy_s_l 函式"
  - "_wcsncpy_s_l 函式"
  - "複製字串"
  - "mbsncpy_s 函式"
  - "mbsncpy_s_l 函式"
  - "字串 [C++], 複製"
  - "strncpy_s 函式"
  - "strncpy_s_l 函式"
  - "wcsncpy_s 函式"
  - "wcsncpy_s_l 函式"
ms.assetid: a971c800-94d1-4d88-92f3-a2fe236a4546
caps.latest.revision: 47
caps.handback.revision: 45
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串的字元複製到另一個。這些 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbsncpy_s` and `_mbsncpy_s_l`不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t strncpy_s(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count  
);  
errno_t _strncpy_s_l(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t wcsncpy_s(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count   
);  
errno_t _wcsncpy_s_l(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t _mbsncpy_s(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count   
);  
errno_t _mbsncpy_s_l(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count,  
   locale_t locale  
);  
template <size_t size>  
errno_t strncpy_s(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
errno_t _strncpy_s_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t wcsncpy_s(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcsncpy_s_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsncpy_s(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsncpy_s_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `strDest`  
 目的地字串。  
  
 `numberOfElements`  
 目的地字串中的以字元為單位的大小。  
  
 `strSource`  
 來源字串。  
  
 `count`  
 要複製的字元數，或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 如果成功則為零，如果攔截發生，則為 `STRUNCATE` ，否則為錯誤碼。  
  
### 錯誤狀況  
  
|`strDest`|`numberOfElements`|`strSource`|傳回值|`strDest` 的內容|  
|---------------|------------------------|-----------------|---------|-------------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|`strDest`\[0\] 設為 0|  
|any|0|any|`EINVAL`|未修改|  
|非`NULL`|太小|any|`ERANGE`|`strDest`\[0\] 設為 0|  
  
## 備註  
 這些函式嘗試複製 `strSource` 的第一個 `D` 字元到 `strDest`， `D` 為較小的 `count` 和 `strSource`的長度。  如果那些 `D` 字元在`strDest` \(其大小為 `numberOfElements`\)中符合大小中且仍然保留 null 結數字元的空間，則那些字元將被複製並附加結束的 null ；否則， `strDest`\[0\] 將設定為 null 字元且將呼叫無效的參數處理程式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 上述段落中有個例外。  如果 `count` 是 `_TRUNCATE`，則大部分 `strSource` 將符合放入複製並同時保留永遠附加的結尾 NULL 空間的 `strDest` 。  
  
 例如：  
  
 `char dst[5];`  
  
 `strncpy_s(dst, 5, "a long string", 5);`  
  
 表示我們要求 `strncpy_s` 複製五個字元進緩衝區五個位元組；這不會保留 null 結束字元的空間，所以 `strncpy_s` 歸零字串並告知無效的參數處理程式。  
  
 如果攔截行為是必要的，請使用 `_TRUNCATE` 或`size` – 1\):  
  
 `strncpy_s(dst, 5, "a long string", _TRUNCATE);`  
  
 `strncpy_s(dst, 5, "a long string", 4);`  
  
 請注意與 `strncpy` 不同，如果 `count` 大於 `strSource`的長度，目的字串非使用 null 字原填補長度 `count`。  
  
 如果來源和目的字串發生重疊，則 `strncpy_s` 的行為是未定義。  
  
 如果 `strDest` 或 `strSource` 是 `NULL`，或者 `numberOfElements` 是 0，則呼叫無效的參數處理常式。  如果允許繼續執行，此函式回傳 `EINVAL` 並設置 `errno` 為 `EINVAL` 。  
  
 `wcsncpy_s` 和 `_mbsncpy_s` 是 `strncpy_s` 的寬字元和多位元組字元版本。  `wcsncpy_s` 的引數與回傳值以及 `mbsncpy_s`會跟著變更。  否則，這六個函式的行為相同。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncpy_s`|`strncpy_s`|`_mbsnbcpy_s`|`wcsncpy_s`|  
|`_tcsncpy_s_l`|`_strncpy_s_l`|`_mbsnbcpy_s_l`|`_wcsncpy_s_l`|  
  
> [!NOTE]
>  \_strncpy\_s\_l、 `_wcsncpy_s_l` 和 `_mbsncpy_s_l` 沒有地區設定相關屬性且提供 `_tcsncpy_s_l` 且不會直接被呼叫。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strncpy_s`, `_strncpy_s_l`|\<string.h\>|  
|`wcsncpy_s`, `_wcsncpy_s_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncpy_s`, `_mbsncpy_s_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strncpy_s_1.cpp  
// compile with: /MTd  
  
// these #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
errno_t strncpy_s_tester( const char * src,  
                          int count )  
{  
   char dest[10];  
  
   printf( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf( "Copying '%s' to %d-byte buffer dest with truncation semantics\n",  
               src, _countof(dest) );  
   else  
      printf( "Copying %d chars of '%s' to %d-byte buffer dest\n",  
              count, src, _countof(dest) );  
  
   errno_t err = strncpy_s( dest, _countof(dest), src, count );  
  
   printf( "    new contents of dest: '%s'\n", dest );  
  
   return err;  
}  
  
void Examples()  
{  
   strncpy_s_tester( "howdy", 4 );  
   strncpy_s_tester( "howdy", 5 );  
   strncpy_s_tester( "howdy", 6 );  
  
   printf( "\nDestination buffer too small:\n" );  
   strncpy_s_tester( "Hi there!!", 10 );  
  
   printf( "\nTruncation examples:\n" );  
  
   errno_t err = strncpy_s_tester( "How do you do?", _TRUNCATE );  
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   err = strncpy_s_tester( "Howdy.", _TRUNCATE );  
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   printf( "\nSecure template overload example:\n" );  
  
   char dest[10];  
   strncpy( dest, "very very very long", 15 );  
   // With secure template overloads enabled (see #defines at  
   // top of file), the preceding line is replaced by  
   //    strncpy_s( dest, _countof(dest), "very very very long", 15 );  
   // Instead of causing a buffer overrun, strncpy_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, strncpy would  
   // copy 15 characters and overrun the dest buffer.  
   printf( "    new contents of dest: '%s'\n", dest );  
}  
  
void myInvalidParameterHandler(  
   const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);  
}  
  
int main( void )  
{  
   _invalid_parameter_handler oldHandler, newHandler;  
  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   Examples();  
}  
```  
  
  **複製「howdy」的 4 個字元至 10 個位元組緩衝區目的地**  
 **目的地新內容：「howd」**  
**複製「howdy」的 5 個字元至 10 個位元組緩衝區目的地**  
 **目的新內容：「howdy」**  
**複製「howdy」的 6 個字元至 10 個位元組緩衝區目的**  
 **目的新內容：「howdy」**  
**目的緩衝區過小：**  
**複製「Hi there\!\!」 的10 個字元至 10 位元組緩衝區目的**  
**呼叫無效的參數處理常式：\(L 「緩衝區太小」 && 0\)**   
 **目的新內容：「**  
**攔截範例：**  
**利用攔截語意複製「How do you do?」 至 10 位元組緩衝區目的**  
 **目的新內容：「How do yo」**  
 **攔截發生**  
**以攔截語意複製「Howdy。」至 10 位元組緩衝區目的**  
 **目的新內容：「Howdy。」**  
 **攔截未發生**  
**保護範本多載範例：**  
**呼叫無效的參數處理常式：\(L 「緩衝區太小」 && 0\)**   
 **目的新內容：「**   
## 範例  
  
```  
// crt_strncpy_s_2.c  
// contrasts strncpy and strncpy_s  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char a[20] = "test";  
   char s[20];  
  
   // simple strncpy usage:  
  
   strcpy_s( s, 20, "dogs like cats" );  
   printf( "Original string:\n   '%s'\n", s );  
  
   // Here we can't use strncpy_s since we don't   
   // want null termination  
   strncpy( s, "mice", 4 );  
   printf( "After strncpy (no null-termination):\n   '%s'\n", s );  
   strncpy( s+5, "love", 4 );  
   printf( "After strncpy into middle of string:\n   '%s'\n", s );  
  
   // If we use strncpy_s, the string is terminated   
   strncpy_s( s, _countof(s), "mice", 4 );  
   printf( "After strncpy_s (with null-termination):\n   '%s'\n", s );  
  
}  
```  
  
  **原始字串：**  
 **「dogs like cats」**  
**在 strncpy 之後 \(不是以 null 終止\)：**  
 **「mice like cats」**  
**在 strncpy 至字串中間之後：**  
 **「mice love cats」**  
**在 strncpy\_s 之後 \(以 null 終止\)：**  
 **「mice」**   
## .NET Framework 對等用法  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcpy、\_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [strcat\_s、wcscat\_s、\_mbscat\_s](../../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy\_s、wcscpy\_s、\_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)