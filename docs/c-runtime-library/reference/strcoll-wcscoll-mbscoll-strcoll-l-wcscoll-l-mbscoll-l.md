---
title: "strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l | Microsoft Docs"
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
  - "wcscoll"
  - "_mbscoll"
  - "_mbscoll_l"
  - "strcoll"
  - "_strcoll_l"
  - "_wcscoll_l"
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
  - "wcscoll"
  - "_mbscoll"
  - "_tcscoll"
  - "_ftcscoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字碼頁，用於字串比較"
  - "mbscoll 函式"
  - "wcscoll_l 函式"
  - "ftcscoll 函式"
  - "wcscoll 函式"
  - "_strcoll_l 函式"
  - "tcscoll 函式"
  - "_ftcscoll 函式"
  - "_tcscoll 函式"
  - "_wcscoll_l 函式"
  - "_mbscoll 函式"
  - "strcoll_l 函式"
  - "strcoll 函式"
  - "字串 [C++]，依字碼頁比較"
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前的地區設定或指定的 LC\_COLLATE 轉換狀態分類來比較字串。  
  
> [!IMPORTANT]
>  `_mbscoll` 和 `_mbscoll_l` 不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int strcoll(  
   const char *string1,  
   const char *string2   
);  
int wcscoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _strcoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale   
);  
int wcscoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale   
);  
int _mbscoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale   
);  
```  
  
#### 參數  
 `string1`, `string2`  
 以 Null 結束的待比較字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這些函式都會傳回表示 `string1` 和 `string2`*、* 的關係，如下所示。  
  
|傳回值|string1 與 string2 的關係|  
|---------|---------------------------|  
|\< 0|`string1` 小於 `string2`|  
|0|`string1` 與 `string2` 相同|  
|\> 0|`string1` 大於 `string2`|  
  
 這些函式發生錯誤時，傳回 `_NLSCMPERROR` 。  若要使用 `_NLSCMPERROR`，請包含 STRING.H 或 MBSTRING.H。  如果 `string1` 或 `string2` 為 NULL 或包含定序序列的網域之外之寬字元程式碼，`wcscoll` 可能會失敗。  發生錯誤時， `wcscoll` 會將 `errno` 設定為 `EINVAL`。  若要檢查呼叫 `wcscoll` 上的錯誤，請將 `errno` 設定為 0 然後再呼叫 `wcscoll` 之後檢查 `errno` 。  
  
## 備註  
 這些函式都會根據目前使用的字碼頁執行 `string1` 和 `string2` 區分大小寫的比較。  這些函式應該只有在目前字碼頁上，字元集順序和字典字元順序存在差異，且這些差異影響到字串比較時，才會使用。  
  
 這些函式全都會驗證它們的參數。  如果 `string1` 或 `string2` 為 null 指標，或如果 `count` 大於 `INT_MAX`，無效的參數處理常式會被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 `_NLSCMPERROR`，並將 `errno` 設為 `EINVAL`。  
  
 因為每個地區設定有排序字元不同的規則，兩個字串的比較是與地區設定相關的作業。  這些沒有 `_l` 結尾的函式版本使用此地區設定相關行為的目前執行緒之地區設定；具有 `_l` 結尾的版本與對應的沒有結尾的函式相同，但使用做為參數傳遞的地區設定而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscoll`|`strcoll`|`_mbscoll`|`wcscoll`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strcoll`|\<string.h\>|  
|`wcscoll`|\<wchar.h\>, \<string.h\>|  
|`_mbscoll`, `_mbscoll_l`|\<mbstring.h\>|  
|`_strcoll_l`|\<string.h\>|  
|`_wcscoll_l`|\<wchar.h\>, \<string.h\>|  
  
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