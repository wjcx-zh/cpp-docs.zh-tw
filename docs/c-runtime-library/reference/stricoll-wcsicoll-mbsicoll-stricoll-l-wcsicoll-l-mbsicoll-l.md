---
title: "_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l | Microsoft Docs"
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
  - "_mbsicoll_l"
  - "_stricoll_l"
  - "_mbsicoll"
  - "_wcsicoll_l"
  - "_wcsicoll"
  - "_stricoll"
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
  - "stricoll"
  - "_stricoll"
  - "_wcsicoll"
  - "mbsicoll_l"
  - "_mbsicoll"
  - "_ftcsicoll"
  - "wcsicoll_l"
  - "_tcsicoll"
  - "mbsicoll"
  - "stricoll_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsicoll 函式"
  - "_mbsicoll 函式"
  - "_mbsicoll_l 函式"
  - "_stricoll 函式"
  - "_stricoll_l 函式"
  - "_tcsicoll 函式"
  - "_wcsicoll 函式"
  - "字碼頁, 用於字串比較"
  - "ftcsicoll 函式"
  - "mbsicoll 函式"
  - "mbsicoll_l 函式"
  - "stricoll 函式"
  - "stricoll_l 函式"
  - "字串比較 [C++], 特定文化特性"
  - "字串 [C++], 依字碼頁比較"
  - "tcsicoll 函式"
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用地區設定特定的資訊來比較字串。  
  
> [!IMPORTANT]
>  `_mbsicoll` 和 `_mbsicoll_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _stricoll(  
   const char *string1,  
   const char *string2   
);  
int _wcsicoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `string1, string2`  
 以 Null 結束的待比較字串。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 這些函式都會傳回表示 `string1` 和 `string2`*、* 的關係，如下所示。  
  
|傳回值|string1 與 string2 的關係|  
|---------|---------------------------|  
|\< 0|`string1` 小於 `string2`|  
|0|`string1` 與 `string2` 相同|  
|\> 0|`string1` 大於 `string2`|  
|`_NLSCMPERROR`|發生錯誤。|  
  
 這些函式都會傳回 `_NLSCMPERROR`。  若要使用 `_NLSCMPERROR`，請包含 `STRING.H` 或 `MBSTRING.H`。  如果 `string1` 或 `string2` 包含在定序序列的網域之外之寬字元程式碼，`_wcsicoll` 可能會失敗。  發生錯誤時， `_wcsicoll` 會將 `errno` 設定為 `EINVAL`。  若要檢查呼叫 `_wcsicoll` 上的錯誤，請將 `errno` 設定為 0 然後再呼叫 `_wcsicoll` 之後檢查 `errno` 。  
  
## 備註  
 這些函式都會根據目前使用的字碼頁執行 `string1` 和 `string2` 不區分大小寫的比較。  這些函式應該只有在目前字碼頁上，字元集順序和字典字元順序存在差異，且這些差異影響到字串比較時，才會使用。  
  
 `_stricmp` 與`_stricoll` 不同之處在於`_stricmp` 的比較過程受 `LC_CTYPE` 的影響，而`_stricoll` 的比較結果是根據 `LC_CTYPE` 和地區設定的`LC_COLLATE`類別。  如需`LC_COLLATE`分類的詳細資訊，請參閱[setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 和 [地區設定分類](../../c-runtime-library/locale-categories.md)。  這些沒有 `_l` 尾碼的函式版本使用目前的地區設定；有`_l` 尾碼的函式版本則使用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 這些函式全都會驗證它們的參數。  如果 `string1` 或 `string2` 為`NULL` 指標，就會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 `_NLSCMPERROR`，並將 `errno` 設為 `EINVAL`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsicoll`|`_stricoll`|`_mbsicoll`|`_wcsicoll`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_stricoll`, `_stricoll_l`|\<string.h\>|  
|`_wcsicoll`, `_wcsicoll_l`|\<wchar.h\>, \<string.h\>|  
|`_mbsicoll`, `_mbsicoll_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## 請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_mbsnbcoll、\_mbsnbcoll\_l、\_mbsnbicoll、\_mbsnbicoll\_l](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [\_stricmp、\_wcsicmp、\_mbsicmp、\_stricmp\_l、\_wcsicmp\_l、\_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)