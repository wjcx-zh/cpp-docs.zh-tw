---
title: "_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l | Microsoft Docs"
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
  - "_mbsnbicoll_l"
  - "_mbsnbcoll_l"
  - "_mbsnbcoll"
  - "_mbsnbicoll"
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
  - "mbsnbicoll"
  - "mbsnbcoll"
  - "mbsnbicoll_l"
  - "_mbsnbcoll"
  - "_mbsnbicoll"
  - "_ftcsnicoll"
  - "_ftcsncoll"
  - "mbsnbcoll_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcoll 函式"
  - "_mbsnbcoll_l 函式"
  - "_mbsnbicoll 函式"
  - "_mbsnbicoll_l 函式"
  - "_tcsncoll 函式"
  - "_tcsnicoll 函式"
  - "mbsnbcoll 函式"
  - "mbsnbcoll_l 函式"
  - "mbsnbicoll 函式"
  - "mbsnbicoll_l 函式"
  - "tcsncoll 函式"
  - "tcsnicoll 函式"
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用多位元組字碼頁資訊，比較 `n` 的兩個位元組多位元組字元字串。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _mbsnbcoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbcoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnbicoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `string1, string2`  
 要比較的字串。  
  
 `count`  
 要比較的位元組數目。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回表示 `string1` 和 `string2`的子關聯。  
  
|傳回值|描述|  
|---------|--------|  
|\< 0|`string1` 的子字串小於 `string2` 子字串。|  
|0|`string1` 子字串等於 `string2` 子字串。|  
|\> 0|`string1` 的子字串大於 `string2` 子字串。|  
  
 如果 `string1` 或 `string2` 為`NULL` 或`count`是較佳的，相對於`INT_MAX`，無效參數調用處理程序，如以下所描述的[參數驗證](../../c-runtime-library/parameter-validation.md)。  如果允許繼續執行，這些函式會傳回 `_NLSCMPERROR`，並將 `errno` 設為 `EINVAL`。  若要使用 `_NLSCMPERROR`，請包含 String.h或 Mbstring.h。  
  
## 備註  
 這些函式對應中，最多，在 `string1` 和 `string2` 的第一個 `count` 位元組並傳回表示發生 `string1` 的子字串和 `string2`的值之間的關聯性。  如果在 `string1` 或 `string2` 子字串的最後一個位元組是前導位元組，它在比較不包含;這些函式會比較子字串完全字元。  `_mbsnbicoll` 是 `_mbsnbcoll`的不區分大小寫的版本。  與 `_mbsnbcmp` 和 `_mbsnbicmp`、 `_mbsnbcoll` 和 `_mbsnbicoll` ，根據多位元組指定表單的傳統的纂順序自動分頁的兩個多位元組字元字串正在使用中的 [字碼頁](../../c-runtime-library/code-pages.md) 。  
  
 對於某些字碼頁和對應的字元集，字元順序字元集的可能與字典會不同。  在「C」地區設定，這不成立:字元順序在 ASCII 字元集中相同字元的字、編輯纂順序。  例如，然而，在某些歐洲字碼頁字元「a」\(值 0x61\) 以字元「ä」\(值 0xE4\) 在字元集，不過，字元「ä 之前」字一般地在字元「a」之前。  由位元組要執行字串字典會比較這個執行個體，請使用 `_mbsnbcoll` 而非 `_mbsnbcmp`;若要只檢查字串是否相等，請使用 `_mbsnbcmp`。  
  
 因為 `coll` 函式 \(以地自動分頁字串比較的，反之， `cmp` 函式來測試字串是否相等， `coll` 函式比對應的 `cmp` 版本慢。  因此，這些`coll`函式應該只有在目前字碼頁上，字元集順序和字典字元順序存在差異，且這些差異影響到比較時，才會使用。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcsncoll`|[\_strncoll](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll`|[\_wcsncoll](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsncoll_l`|[\_strncoll、\_wcsncoll、\_mbsncoll、\_strncoll\_l、\_wcsncoll\_l、\_mbsncoll\_l](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll_l`|[\_wcsncoll\_l](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsnicoll`|[\_strnicoll](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll`|[\_wcsnicoll](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
|`_tcsnicoll_l`|[\_strnicoll\_l](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll_l`|[\_wcsnicoll\_l](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnbcoll`|\<mbstring.h\>|  
|`_mbsnbcoll_l`|\<mbstring.h\>|  
|`_mbsnbicoll`|\<mbstring.h\>|  
|`_mbsnbicoll_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_mbsnbicmp、\_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)