---
title: "strcpy_s、wcscpy_s、_mbscpy_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcscpy_s"
  - "_mbscpy_s"
  - "strcpy_s"
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
  - "strcpy_s"
  - "_mbscpy_s"
  - "_tcscpy_s"
  - "wcscpy_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strcpy_s 函式"
  - "_tcscpy_s 函式"
  - "_mbscpy_s 函式"
  - "複製字串"
  - "複製字串 [c + +]"
  - "tcscpy_s 函式"
  - "wcscpy_s 函式"
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
caps.latest.revision: 41
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 41
---
# strcpy_s、wcscpy_s、_mbscpy_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製字串。 這些版本 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) 中所述，具有安全性增強功能， [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
> [!IMPORTANT]
>  不可在於 `_mbscpy_s` 中執行的應用程式中使用 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。 如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t strcpy_s(  
   char *strDestination,  
   size_t numberOfElements,  
   const char *strSource   
);  
errno_t wcscpy_s(  
   wchar_t *strDestination,  
   size_t numberOfElements,  
   const wchar_t *strSource   
);  
errno_t _mbscpy_s(  
   unsigned char *strDestination,  
   size_t numberOfElements,  
   const unsigned char *strSource   
);  
template <size_t size>  
errno_t strcpy_s(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
errno_t wcscpy_s(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
errno_t _mbscpy_s(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### 參數  
 `strDestination`  
 目的地字串緩衝區的位置。  
  
 `numberOfElements`  
 目的地字串緩衝區的大小，若為窄和多位元組函式則以 `char` 為單位，而若為寬函式則以 `wchar_t` 為單位。  
  
 `strSource`  
 以 null 結束的來源字串緩衝區。  
  
## 傳回值  
 如果成功則為零，否則為錯誤。  
  
### 錯誤狀況  
  
|`strDestination`|`numberOfElements`|`strSource`|傳回值|`strDestination` 的內容。|  
|----------------------|------------------------|-----------------|---------|---------------------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|`strDestination`\[0\] 設為 0|  
|任何|0 或太小|any|`ERANGE`|`strDestination`\[0\] 設為 0|  
  
## 備註  
 `strcpy_s` 函式會將 `strSource` 位址中的內容 \(包含結束的 null 字元\) 複製到 `strDestination` 所指定的位置。 目的字串必須大到足以保留來源字串及其結束的 null 字元。 如果來源和目的字串重疊，則 `strcpy_s` 的行為未定義。  
  
 `wcscpy_s` 是 `strcpy_s` 的寬字元版本，而 `_mbscpy_s` 則是多位元組字元版本。`wcscpy_s` 的引數和傳回值是寬字元字串；`_mbscpy_s` 的引數則是多位元組字元字串。 除此之外，這三個函式的行為相同。  
  
 如果 `strDestination` 或 `strSource` 是 null 指標，或如果目的地字串太小，不正確的參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，當 `strDestination` 或 `strSource` 為 null 指標時，這些函式會傳回 `EINVAL` 並將 `errno` 設為 `EINVAL`，當目的字串太小時，這些函式會傳回 `ERANGE` 並將 `errno` 設為 `ERANGE`。  
  
 成功執行後，目的字串永遠是以 null 終止的。  
  
 在 C\+\+ 中，樣板多載簡化了這些函式的使用方式，樣板多載可自動推斷緩衝區長度 \(因而您不須指定大小引數\)，也可以自動將較舊且較不安全的函式取代成其較新且較安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFE 填入緩衝區。 若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscpy_s`|`strcpy_s`|`_mbscpy_s`|`wcscpy_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strcpy_s`|\<string.h\>|  
|`wcscpy_s`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscpy_s`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strcpy_s.cpp  
// This program uses strcpy_s and strcat_s  
// to build a phrase.  
//  
  
#include <string.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   char string[80];  
   // using template versions of strcpy_s and strcat_s:  
   strcpy_s( string, "Hello world from " );  
   strcat_s( string, "strcpy_s " );  
   strcat_s( string, "and " );  
   // of course we can supply the size explicitly if we want to:  
   strcat_s( string, _countof(string), "strcat_s!" );  
  
   printf( "String = %s\n", string );  
}  
```  
  
```Output  
String = Hello world from strcpy_s and strcat_s!  
```  
  
## .NET Framework 對等用法  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)