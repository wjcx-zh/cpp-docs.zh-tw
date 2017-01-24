---
title: "strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l | Microsoft Docs"
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
  - "_wcsncat_s_l"
  - "wcsncat_s"
  - "_mbsncat_s_l"
  - "_mbsncat_s"
  - "strncat_s"
  - "_strncat_s_l"
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
  - "strncat_s_l"
  - "_mbsncat_s_l"
  - "_tcsncat_s"
  - "wcsncat_s"
  - "wcsncat_s_l"
  - "strncat_s"
  - "_mbsncat_s"
  - "_tcsncat_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsncat_s 函式"
  - "_mbsncat_s_l 函式"
  - "_tcsncat_s 函式"
  - "_tcsncat_s_l 函式"
  - "附加字串"
  - "串連字串"
  - "mbsncat_s 函式"
  - "mbsncat_s_l 函式"
  - "字串串連 [C++]"
  - "字串 [C++], 附加"
  - "strncat_s 函式"
  - "strncat_s_l 函式"
  - "wcsncat_s 函式"
  - "wcsncat_s_l 函式"
ms.assetid: de77eca2-4d9c-4e66-abf2-a95fefc21e5a
caps.latest.revision: 42
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字元附加至字串。  這些 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbsncat_s` and `_mbsncat_s_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t strncat_s(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count  
);  
errno_t _strncat_s_l(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t wcsncat_s(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count   
);  
errno_t _wcsncat_s_l(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t _mbsncat_s(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count  
);  
errno_t _mbsncat_s_l(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t strncat_s(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
errno_t _strncat_s_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t wcsncat_s(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcsncat_s_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsncat_s(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
errno_t _mbsncat_s_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 \[out\] `strDest`  
 以 Null 結束的結束字串。  
  
 \[in\]`numberOfElements`  
 目的端緩衝區的大小。  
  
 \[in\]`strSource`  
 以 Null 結束的來源字串。  
  
 \[in\]`count`  
 附加的字元數，或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in\] `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果成功，回傳零，如果失敗，則為錯誤碼。  
  
### 錯誤狀況  
  
|`strDestination`|`numberOfElements`|`strSource`|傳回值|`strDestination` 的內容|  
|----------------------|------------------------|-----------------|---------|--------------------------|  
|`NULL` 或未結束|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|未修改|  
|any|0 或太小|any|`ERANGE`|未修改|  
  
## 備註  
 這些函式嘗試附加 `strSource` 的第一個 `D` 字元加入至 `strDest`的結尾， `D` 是較小的 `count` 和 `strSource`的長度。  如果附加這些 `D` 字元在大小中適當值會測量為 \(`numberOfElements`\) 的 `strDest` 和仍然保留 null 結束字元的空間，則這些字元附加開始，原始的結尾的 null，則為 `strDest`，而且新的結尾附加 null ;否則 `strDest`\[0\] 被設為 Null 字元和無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 上述段落中有個例外。  如果 `count` 為 `strSource` [\_TRUNCATE](../../c-runtime-library/truncate.md) 則符合附加至 `strDest` ，同時保留空間附加一個結尾的 null。  
  
 例如：  
  
 `char dst[5];`  
  
 `strncpy_s(dst, _countof(dst), "12", 2);`  
  
 `strncat_s(dst, _countof(dst), "34567", 3);`  
  
 表示我們要求 `strncat_s` 在五個字元的緩衝區附加三個字元至兩個字元;這不會保留空間給 null 結束字元的空間，所以 `strncat_s` 歸零字串並告知無效的參數處理常式。  
  
 如果攔截行為是必要的，請使用 `_TRUNCATE` 或調整 `size` 參數:  
  
 `strncat_s(dst, _countof(dst), "34567", _TRUNCATE);`  
  
 或  
  
 `strncat_s(dst, _countof(dst), "34567", _countof(dst)-strlen(dst)-1);`  
  
 在所有情況下，結果產生的字串是以 null 字元結束。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
 如果 `strSource` 或 `strDest` 為 `NULL` 或 `numberOfElements` 為零，則會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果執行允許繼續執行，函式會傳回 `EINVAL` ，但不修改其參數。  
  
 `wcsncat_s` 和 `_mbsncat_s` 是 `strncat_s` 的寬字元和多位元組字元版本。  `wcsncat_s` 的字串引數和傳回值是寬字元字串，而 `_mbsncat_s` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncat_s`|`strncat_s`|`_mbsnbcat_s`|`wcsncat_s`|  
|`_tcsncat_s_l`|`_strncat_s_l`|`_mbsnbcat_s_l`|`_wcsncat_s_l`|  
  
 `_strncat_s_l` 和 `_wcsncat_s_l` 沒有地區設定相關屬性;它們只針對 `_tcsncat_s_l`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strncat_s`|\<string.h\>|  
|`wcsncat_s`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncat_s`, `_mbsncat_s_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strncat_s.cpp  
// compile with: /MTd  
  
// These #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
errno_t strncat_s_tester( const char * initialDest,  
                          const char * src,  
                          int count )  
{  
   char dest[10];  
   strcpy_s( dest, _countof(dest), initialDest );  
  
   printf_s( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf_s( "Appending '%s' to %d-byte buffer dest with truncation semantics\n",  
               src, _countof(dest) );  
   else  
      printf_s( "Appending %d chars of '%s' to %d-byte buffer dest\n",  
              count, src, _countof(dest) );  
  
   printf_s( "    old contents of dest: '%s'\n", dest );  
  
   errno_t err = strncat_s( dest, _countof(dest), src, count );  
  
   printf_s( "    new contents of dest: '%s'\n", dest );  
  
   return err;  
}  
  
void Examples()  
{  
   strncat_s_tester( "hi ", "there", 4 );  
   strncat_s_tester( "hi ", "there", 5 );  
   strncat_s_tester( "hi ", "there", 6 );  
  
   printf_s( "\nDestination buffer too small:\n" );  
   strncat_s_tester( "hello ", "there", 4 );  
  
   printf_s( "\nTruncation examples:\n" );  
  
   errno_t err = strncat_s_tester( "hello ", "there", _TRUNCATE );  
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   err = strncat_s_tester( "hello ", "!", _TRUNCATE );  
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   printf_s( "\nSecure template overload example:\n" );  
  
   char dest[10] = "cats and ";  
   strncat( dest, "dachshunds", 15 );  
   // With secure template overloads enabled (see #define  
   // at top of file), the preceding line is replaced by  
   //    strncat_s( dest, _countof(dest), "dachshunds", 15 );  
   // Instead of causing a buffer overrun, strncat_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, strncat would  
   // append "dachshunds" and overrun the dest buffer.  
   printf_s( "    new contents of dest: '%s'\n", dest );  
}  
  
void myInvalidParameterHandler(  
   const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf_s(L"Invalid parameter handler invoked: %s\n", expression);  
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
  
  **附加 4 個字元「where」到 10 個位元組 dest 緩衝區**  
 **dest 的舊內容:「"hi"」**  
 **dest 的新內容:「"hi ther"」**  
**附加 5 個字元「where」到 10 個位元組 dest 緩衝區**  
 **dest 的舊內容:「"hi"」**  
 **dest 的新內容:「"hi there"」**  
**附加 6 個字元「where」到 10 個位元組 dest 緩衝區**  
 **dest 的舊內容:「"hi"」**  
 **dest 的新內容:「"hi there"」**  
**目的緩衝區過小：**  
**附加 4 個字元「where」到 10 個位元組 dest 緩衝區**  
 **dest 的舊內容:「hello」**  
**呼叫無效的參數處理常式：\(L 「緩衝區太小」 && 0\)**   
 **目的新內容：「**  
**攔截範例：**  
**附加「where」會以攔截語意的 10 位元組 dest 緩衝區**   
 **dest 的舊內容:「hello」**  
 **dest 新內容:「hello the」**  
 **攔截發生**  
**附加「\!」到攔截語意的 10 位元組 dest 緩衝區**   
 **dest 的舊內容:「hello」**  
 **dest 的新內容:「hello\!」**  
 **攔截未發生**  
**保護範本多載範例：**  
**呼叫無效的參數處理常式：\(L 「緩衝區太小」 && 0\)**   
 **目的新內容：「**   
## .NET Framework 對等用法  
 [System::String::Concat](https://msdn.microsoft.com/en-us/library/system.string.concat.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
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