---
title: "strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strncpy"
  - "_strncpy_l"
  - "_mbsncpy"
  - "wcsncpy"
  - "_mbsncpy_l"
  - "_wcsncpy_l"
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
  - "_fstrncpy"
  - "strncpy"
  - "_ftcsncpy"
  - "_tcsnccpy_l"
  - "_tcsnccpy"
  - "_mbsncpy"
  - "wcsncpy"
  - "_tcsncpy"
  - "_strncpy_l"
  - "_mbsncpy_l"
  - "_wcsncpy_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrncpy 函式"
  - "_ftcsncpy 函式"
  - "_mbsncpy 函式"
  - "_mbsncpy_l 函式"
  - "_strncpy_l 函式"
  - "_tcsnccpy 函式"
  - "_tcsnccpy_l 函式"
  - "_tcsncpy 函式"
  - "_tcsncpy_l 函式"
  - "_wcsncpy_l 函式"
  - "字元 [C++], 複製"
  - "複製字串的字元"
  - "fstrncpy 函式"
  - "ftcsncpy 函式"
  - "mbsncpy 函式"
  - "mbsncpy_l 函式"
  - "字串 [C++], 複製"
  - "strncpy 函式"
  - "strncpy_l 函式"
  - "tcsnccpy 函式"
  - "tcsnccpy_l 函式"
  - "tcsncpy 函式"
  - "tcsncpy_l 函式"
  - "wcsncpy 函式"
  - "wcsncpy_l 函式"
ms.assetid: ac4345a1-a129-4f2f-bb8a-373ec58ab8b0
caps.latest.revision: 42
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一個字串的字元複製到另一個。  這些函式已有更安全的版本可用，請參閱 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)。  
  
> [!IMPORTANT]
>  不可在於 `_mbsncpy` 中執行的應用程式中使用 `_mbsncpy_l` 和 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strncpy(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
char *_strncpy_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   locale_t locale   
);  
wchar_t *wcsncpy(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
wchar_t *_wcsncpy_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   locale_t locale   
);  
unsigned char *_mbsncpy(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count   
);  
unsigned char *_mbsncpy_l(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
char *strncpy(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
char *_strncpy_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   locale_t locale   
); // C++ only  
template <size_t size>  
wchar_t *wcsncpy(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
wchar_t *_wcsncpy_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   locale_t locale   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncpy(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncpy_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `strDest`  
 目的字串。  
  
 `strSource`  
 來源字串。  
  
 `count`  
 要複製的字元數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回 `strDest`。  未保留表示錯誤的傳回值。  
  
## 備註  
 `strncpy` 函式會將 `strSource` 的初始 `count` 字元複製到 `strDest`，並傳回 `strDest`。  如果 `count` 小於或等於 `strSource` 的長度，則 null 字元不會自動附加至複製的字串。  如果 `count` 大於 `strSource` 的長度，則會以 null 字元填補目的字串，直到長度達 `count` 為止。  如果來源和目的字串重疊，則 `strncpy` 的行為未定義。  
  
> [!IMPORTANT]
>  `strncpy` 不會檢查在 `strDest` 中是否有足夠的空間；使得這成為緩衝區滿溢的潛在原因。  `count` 引數會限制複製的字元數目；這並非 `strDest` 大小上的限制。  請參閱下列範例。  如需詳細資訊，請參閱[避免緩衝區滿溢](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 如果 `strDest` 或 `strSource` 為 `NULL` 指標，或如果 `count` 小於或等於零，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則這些函式會傳回 \-1，並將 `errno` 設為 `EINVAL`。  
  
 `wcsncpy` 和 `_mbsncpy` 是寬字元和多位元組字元版本的 `strncpy`。  `wcsncpy` 和 `_mbsncpy` 的引數和傳回值會隨之改變。  除此之外，這六個函式的行為相同。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用這些函式對應的更新與安全版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncpy`|`strncpy`|`_mbsnbcpy`|`wcsncpy`|  
|`_tcsncpy_l`|`_strncpy_l`|`_mbsnbcpy_l`|`_wcsncpy_l`|  
  
> [!NOTE]
>  `_strncpy_l` 和 `_wcsncpy_l` 沒有任何地區設定相依性；它們只是為了 `_tcsncpy_l` 而提供，而不是用於直接呼叫。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strncpy`|\<string.h\>|  
|`wcsncpy`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncpy`, `_mbsncpy_l`|\<mbstring.h\>|  
  
 如需其他平台相容性的資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 下列範例示範 `strncpy` 如何使用和如何遭誤用，導致程式 Bug 和安全性問題。  此編譯器會為 `strncpy` 的每次呼叫產生警告，類似 **crt\_strncpy\_x86.c\(15\) : warning C4996: 'strncpy': This function or variable may be unsafe. Consider using strncpy\_s instead. To disable deprecation, use \_CRT\_SECURE\_NO\_WARNINGS. See online help for details.**  
  
```  
// crt_strncpy_x86.c  
// Use this command in an x86 developer command prompt to compile:   
// cl /TC /W3 crt_strncpy_x86.c  
  
#include <stdio.h>  
#include <string.h>  
  
int main() {  
   char t[20];  
   char s[20];  
   char *p = 0, *q = 0;  
  
   strcpy_s(s, sizeof(s), "AA BB CC");  
   // Note: strncpy is deprecated; consider using strncpy_s instead  
   strncpy(s, "aa", 2);     // "aa BB CC"         C4996  
   strncpy(s + 3, "bb", 2); // "aa bb CC"         C4996  
   strncpy(s, "ZZ", 3);     // "ZZ",              C4996  
                            // count greater than strSource, null added  
   printf("%s\n", s);  
  
   strcpy_s(s, sizeof(s), "AA BB CC");  
   p = strstr(s, "BB");  
   q = strstr(s, "CC");  
   strncpy(s, "aa", p - s - 1);   // "aa BB CC"   C4996  
   strncpy(p, "bb", q - p - 1);   // "aa bb CC"   C4996  
   strncpy(q, "cc",  q - s);      // "aa bb cc"   C4996  
   strncpy(q, "dd", strlen(q));   // "aa bb dd"   C4996  
   printf("%s\n", s);  
  
   // some problems with strncpy  
   strcpy_s(s, sizeof(s), "test");  
   strncpy(t, "this is a very long string", 20 ); // C4996  
   // Danger: at this point, t has no terminating null,  
   // so the printf continues until it runs into one.  
   // In this case, it will print "this is a very long test"  
   printf("%s\n", t);  
  
   strcpy_s(t, sizeof(t), "dogs like cats");  
   printf("%s\n", t);  
  
   strncpy(t + 10, "to chase cars.", 14); // C4996  
   printf("%s\n", t);  
  
   // strncpy has caused a buffer overrun and corrupted string s  
   printf("Buffer overrun: s = '%s' (should be 'test')\n", s);  
   // Since the stack grows from higher to lower addresses, buffer  
   // overruns can corrupt function return addresses on the stack,  
   // which can be exploited to run arbitrary code.  
}  
```  
  
 輸出  
  
  **ZZ**  
**aa bb dd**  
**this is a very long test**  
**dogs like cats**  
**dogs like to chase cars.  Buffer overrun: s \= 'ars.' \(should be 'test'\)**  自動變數的配置以及錯誤偵測和程式碼保護的層級可能會隨變更的編譯器設定而異。  建置在其他編譯環境中，或藉由其他編譯器選項建置時，此範例可能會有不同的結果。  
  
## .NET Framework 對等用法  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcpy、\_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strcpy\_s、wcscpy\_s、\_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)