---
title: "strcat_s、wcscat_s、_mbscat_s | Microsoft Docs"
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
  - "strcat_s"
  - "_mbscat_s"
  - "wcscat_s"
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
  - "strcat_s"
  - "wcscat_s"
  - "_mbscat_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbscat_s 函式"
  - "附加字串"
  - "mbscat_s 函式"
  - "strcat_s 函式"
  - "字串 [C++], 附加"
  - "wcscat_s 函式"
ms.assetid: 0f2f9901-c5c5-480b-98bc-f8f690792fc0
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcat_s、wcscat_s、_mbscat_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

增添字串。  這些 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbscat_s`不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t strcat_s(  
   char *strDestination,  
   size_t numberOfElements,  
   const char *strSource   
);  
errno_t wcscat_s(  
   wchar_t *strDestination,  
   size_t numberOfElements,  
   const wchar_t *strSource   
);  
errno_t _mbscat_s(  
   unsigned char *strDestination,  
   size_t numberOfElements,  
   const unsigned char *strSource   
);  
template <size_t size>  
errno_t strcat_s(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
errno_t wcscat_s(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
errno_t _mbscat_s(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### 參數  
 `strDestination`  
 以 Null 結束的目標字串緩衝區。  
  
 `numberOfElements`  
 目的端字串緩衝區的大小。  
  
 `strSource`  
 以 Null 結束的來源字串緩衝區。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### 錯誤狀況  
  
|`strDestination`|`numberOfElements`|`strSource`|傳回值|`strDestination` 的內容|  
|----------------------|------------------------|-----------------|---------|--------------------------|  
|`NULL` 或未結束|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|`strDestination`\[0\] 設為 0|  
|any|0 或太小|any|`ERANGE`|`strDestination`\[0\] 設為 0|  
  
## 備註  
 `strcat_s` 函式會將 `strSource` 附加至 `strDestination` 並用 null 字元結束結果字串。  `strSource` 的初始字元覆寫 `strDestination`結束的 null 字元。  如果來源和目的字串發生重疊，則 `strcat_s` 的行為是未定義。  
  
 請注意第二個參數是緩衝區的總數，而非剩餘大小:  
  
```  
char buf[16];  
strcpy_s(buf, 16, "Start");  
strcat_s(buf, 16, " End");               // Correct  
strcat_s(buf, 16 – strlen(buf), " End"); // Incorrect  
```  
  
 `wcscat_s` 和 `_mbscat_s` 是 `strcat_s` 的寬字元和多位元組字元版本。  `wcscat_s` 的引數和傳回值是寬字元字串，而 `_mbscat_s` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 如果 `strDestination` 為 null 指標或非以 null 結束，或者 `strSource` 是 `NULL` 指標，或者是目標字串太小，會如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述，無效的參數處理常式將受叫用。  如果允許繼續執行，這些函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscat_s`|`strcat_s`|`_mbscat_s`|`wcscat_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strcat_s`|\<string.h\>|  
|`wcscat_s`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscat_s`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [strcpy\_s、wcscpy\_s、\_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 中的範例。  
  
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