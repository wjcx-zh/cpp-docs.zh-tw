---
title: "strrchr、wcsrchr、_mbsrchr、_mbsrchr_l | Microsoft Docs"
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
  - "strrchr"
  - "wcsrchr"
  - "_mbsrchr"
  - "_mbsrchr_l"
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
  - "_tcsrchr"
  - "_ftcsrchr"
  - "strrchr"
  - "wcsrchr"
  - "_mbsrchr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsrchr 函式"
  - "_mbsrchr 函式"
  - "_mbsrchr_l 函式"
  - "_tcsrchr 函式"
  - "字元 [C++], 掃描"
  - "ftcsrchr 函式"
  - "mbsrchr 函式"
  - "mbsrchr_l 函式"
  - "掃描字串"
  - "字串 [C++], 掃描中"
  - "strrchr 函式"
  - "tcsrchr 函式"
  - "wcsrchr 函式"
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strrchr、wcsrchr、_mbsrchr、_mbsrchr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找字串中某個字元最後一次出現的位置。  
  
> [!IMPORTANT]
>  `_mbsrchr` and `_mbsrchr_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strrchr(  
   const char *str,  
   int c   
); // C only  
char *strrchr(  
   char *str,  
   int c   
); // C++ only  
const char *strrchr(  
   const char *str,  
   int c   
); // C++ only  
wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C only  
wchar_t *wcsrchr(  
   wchar_t *str,  
   wchar_t c   
); // C++ only  
const wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C++ only  
unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C only  
unsigned char *_mbsrchr(  
   unsigned char *str,  
   unsigned int c   
); // C++ only  
const unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C++ only  
unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C only  
unsigned char *_mbsrchr_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 從中搜尋的 NULL 結尾字串。  
  
 `c`  
 待配置的字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果找不到 `c` ，則傳回指向 `c` 在 `str` 中最後一次出現的位置之指標或是 `NULL` 。  
  
## 備註  
 `strrchr` 函式會尋找 `c` 在 `str` 中最後一次的出現 \(轉換為 `char`\) 。  這項搜尋包含結束的 null 字元。  
  
 `wcsrchr` 和 `_mbsrchr` 是 `strrchr` 的寬字元和多位元組字元版本。  `wcsrchr`  的引數和傳回值是寬字元字串，而 `_mbsrchr` 的引數和傳回值則是多位元組字元字串。  
  
 在 C 裏，這些函式的第一個引數採用 `const` 的指標。  在 C\+\+ 裏，有兩個多載版本可供使用。  多載的一個版本接受 `const` 的指標並回傳 `const` 的指標。另一個則接受 `const` 的指標並回傳非 `const` 的指標。  如果 `const` 和非 `const` 的版本均可用，會定義巨集 \_CONST\_CORRECT\_OVERLOADS 。  如果您需要 C\+\+ 兩個多載版本有非 `const` 的行為，請定義符號 \_CONST\_RETURN 。  
  
 `_mbsrchr` 會驗證其參數。  如果 `str` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，則 `errno`  會被設為 `EINVAL`  並且 `_mbsrchr`  會傳回 0。  `strrchr` 和 `wcsrchr` 並不驗證它們的參數。  這三個函式其餘部分的運作相同。  
  
 輸出值受地區設定的 `LC_CTYPE`  分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|  
|**N\/A**|**N\/A**|`_mbsrchr_l`|**N\/A**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strrchr`|\<string.h\>|  
|`wcsrchr`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h\>|  
  
 如需更多相容性的資訊，請參閱 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 如需使用 `strrchr` 的範例，請參閱 [](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md "strchr, wcschr, _mbschr, _mbschr_l")。  
  
## .NET Framework 對等用法  
 [System::String::LastIndexOf](https://msdn.microsoft.com/en-us/library/system.string.lastindexof.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strchr、wcschr、\_mbschr、\_mbschr\_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strpbrk、wcspbrk、\_mbspbrk、\_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)