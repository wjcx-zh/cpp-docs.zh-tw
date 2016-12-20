---
title: "_strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l | Microsoft Docs"
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
  - "_mbsnicoll_l"
  - "_mbsnicoll"
  - "_wcsnicoll_l"
  - "_strnicoll"
  - "_strnicoll_l"
  - "_wcsnicoll"
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
  - "wcshicoll_l"
  - "_ftcsncicoll"
  - "strnicoll_l"
  - "_wcsnicoll"
  - "mbsnicoll_l"
  - "_strnicoll"
  - "mbsnicoll"
  - "_ftcsnicoll"
  - "wcsnicoll"
  - "_tcsnicoll"
  - "_mbsnicoll"
  - "strinicoll"
  - "_tcsncicoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsncicoll 函式"
  - "_ftcsnicoll 函式"
  - "_mbsnicoll 函式"
  - "_mbsnicoll_l 函式"
  - "_strnicoll 函式"
  - "_strnicoll_l 函式"
  - "_tcsncicoll 函式"
  - "_tcsnicoll 函式"
  - "_wcsnicoll 函式"
  - "_wcsnicoll_l 函式"
  - "字碼頁, 用於字串比較"
  - "ftcsncicoll 函式"
  - "ftcsnicoll 函式"
  - "mbsnicoll 函式"
  - "mbsnicoll_l 函式"
  - "字串 [C++], 依字碼頁比較"
  - "strnicoll 函式"
  - "strnicoll_l 函式"
  - "tcsncicoll 函式"
  - "tcsnicoll 函式"
  - "wcsnicoll 函式"
  - "wcsnicoll_l 函式"
ms.assetid: abf0c569-725b-428d-9ff2-924f430104b4
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用地區設定特定的資訊來比較字串。  
  
> [!IMPORTANT]
>  `_mbsnicoll` 和 `_mbsnicoll_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _strnicoll(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsnicoll(  
   const wchar_t *string1,  
   const wchar_t *string2 ,  
   size_t count   
);  
int _mbsnicoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strnicoll_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsnicoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2 ,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `string1, string2`  
 以 Null 結束的待比較字串。  
  
 `count`  
 要比較的字元數。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 這些函式都會傳回暗指 `string1` 和 `string2`的子關聯性的值*，* 如下所示。  
  
|傳回值|string1 與 string2 的關係|  
|---------|---------------------------|  
|\< 0|`string1` 小於 `string2`|  
|0|`string1` 與 `string2` 相同|  
|\> 0|`string1` 大於 `string2`|  
  
 這些函式都會傳回 `_NLSCMPERROR`。  若要使用 `_NLSCMPERROR`，請 include STRING.H 或 MBSTRING.H。  如果 `string1` 或 `string2` 包含在定序序列的網域之外之寬字元程式碼，`_wcsnicoll` 可能會失敗。  發生錯誤時， `_wcsnicoll` 會將 `errno` 設定為 `EINVAL`。  要檢查呼叫 `_wcsnicoll`的錯誤，將`errno` 設為 0 並檢查 `errno` 在呼叫`_wcsnicoll`之後**.**  
  
## 備註  
 這些函式都會根據字碼頁在 `string1` 和 `string2` 執行的第一個 `count` 字元的不區分大小寫的比較。  這些函式應該只有在字碼頁上，字元集順序和字典字元順序存在差異，且這些差異影響到字串比較時，才會使用。  這些函式版本沒有 `_l` 尾碼來使用目前的地區設定和字碼頁。  以`_l`為字尾的版本也相同，不同處為使用傳遞過來的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 這些函式全都會驗證它們的參數。  如果 `string1` 或 `string2` 為 null 指標，或如果 `INT_MAX` 大於 ，無效的參數處理常式會被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 `_NLSCMPERROR`，並將 `errno` 設為 `EINVAL`**.**。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncicoll`|`_strnicoll`|`_mbsnbicoll`|`_wcsnicoll`|  
|`_tcsnicoll`|`_strnicoll`|[\_mbsnbicoll](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|`_wcsnicoll`|  
|`_tcsnicoll_l`|`_strnicoll_l`|`_mbsnbicoll_l`|`_wcsnicoll_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strnicoll`, `_strnicoll_l`|\<string.h\>|  
|`_wcsnicoll`, `_wcsnicoll_l`|\<wchar.h\> 或 \<string.h\>|  
|`_mbsnicoll`, `_mbsnicoll_l`|\<mbstring.h\>|  
  
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