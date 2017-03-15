---
title: "strcat、wcscat、_mbscat | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbscat"
  - "wcscat"
  - "strcat"
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
  - "_mbscat"
  - "_ftcscat"
  - "_tcscat"
  - "strcat"
  - "wcscat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcscat 函式"
  - "_mbscat 函式"
  - "_tcscat 函式"
  - "附加字串"
  - "串連字串"
  - "ftcscat 函式"
  - "mbscat 函式"
  - "strcat 函式"
  - "字串 [C++], 附加"
  - "字串 [C++], 串連"
  - "tcscat 函式"
  - "wcscat 函式"
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# strcat、wcscat、_mbscat
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

增添字串。  更多這些函式的可用安全版本，請參閱 [strcat\_s、wcscat\_s、\_mbscat\_s](../../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)。  
  
> [!IMPORTANT]
>  `_mbscat_s`不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strcat(  
   char *strDestination,  
   const char *strSource   
);  
wchar_t *wcscat(  
   wchar_t *strDestination,  
   const wchar_t *strSource   
);  
unsigned char *_mbscat(  
   unsigned char *strDestination,  
   const unsigned char *strSource   
);  
template <size_t size>  
char *strcat(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
wchar_t *wcscat(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
unsigned char *_mbscat(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### 參數  
 `strDestination`  
 以 Null 結束的結束字串。  
  
 `strSource`  
 以 Null 結束的來源字串。  
  
## 傳回值  
 這些函式都會傳回目標字串`strDestination`。  未保留表示錯誤的傳回值。  
  
## 備註  
 `strcat` 函式會將 `strSource` 附加至 `strDestination` 並用 null 字元結束結果字串。  `strSource` 的初始字元覆寫 `strDestination`結束的 null 字元。  如果來源和目的字串發生重疊，則 `strcat` 的行為是未定義。  
  
> [!IMPORTANT]
>  因為`strcat`不會在添加`strSource`前檢查`strDestination`是否有足夠的空間，這是緩衝區滿溢的潛在因素。  請考慮改用[\_malloca](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)。  
  
 `wcscat` 和 `_mbscat` 是 `strcat` 的寬字元和多位元組字元版本。  `wcscat` 的引數和傳回值是寬字元字串，而 `_mbscat` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscat`|`strcat`|`_mbscat`|`wcscat`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strcat`|\<string.h\>|  
|`wcscat`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscat`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::String::Concat](https://msdn.microsoft.com/en-us/library/system.string.concat.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)