---
title: "_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l | Microsoft Docs"
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
  - "_strncoll"
  - "_mbsncoll_l"
  - "_wcsncoll"
  - "_wcsncoll_l"
  - "_mbsncoll"
  - "_strncoll_l"
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
  - "mbsncoll_l"
  - "strncoll"
  - "_wcsncoll"
  - "_tcsnccoll"
  - "_ftcsnccoll"
  - "wcsncoll"
  - "_mbsncoll"
  - "wcsncoll_l"
  - "strncoll_l"
  - "_ftcsncoll"
  - "_strncoll"
  - "_tcsncoll"
  - "mbsncoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsnccoll 函式"
  - "_ftcsncoll 函式"
  - "_mbsncoll 函式"
  - "_mbsncoll_l 函式"
  - "_strncoll 函式"
  - "_strncoll_l 函式"
  - "_tcsnccoll 函式"
  - "_tcsncoll 函式"
  - "_wcsncoll 函式"
  - "_wcsncoll_l 函式"
  - "字碼頁, 用於字串比較"
  - "ftcsnccoll 函式"
  - "ftcsncoll 函式"
  - "mbsncoll 函式"
  - "mbsncoll_l 函式"
  - "字串 [C++], 依字碼頁比較"
  - "strncoll 函式"
  - "strncoll_l 函式"
  - "tcsnccoll 函式"
  - "tcsncoll 函式"
  - "wcsncoll 函式"
  - "wcsncoll_l 函式"
ms.assetid: e659a5a4-8afe-4033-8e72-17ffd4bdd8e9
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用地區設定特定資訊，以比較字串。  
  
> [!IMPORTANT]
>  不可在於 `_mbsncoll` 中執行的應用程式中使用 `_mbsncoll_l` 和 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _strncoll(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsncoll(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strncoll_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsncoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsncoll_l(  
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
 要使用的地區設定。  
  
## 傳回值  
 所有這些函式都會傳回值，而值表示 `string1` 子字串和 `string2` 子字串的關聯性，如下所示。  
  
|傳回值|string1 與 string2 的關係|  
|---------|---------------------------|  
|\< 0|`string1` 小於 `string2`。|  
|0|`string1` 等同於 `string2`|  
|\> 0|`string1` 大於 `string2`。|  
  
 所有這些函式都會傳回 `_NLSCMPERROR`。  若要使用 `_NLSCMPERROR`，請包括 STRING.h 或 MBSTRING.h。  如果 `string1` 或 `string2` 包含定序順序之網域外部的寬字元碼，則 `_wcsncoll` 可能會失敗。  發生錯誤時，`_wcsncoll` 可能會將 `errno` 設定為 `EINVAL`。  若要檢查呼叫 `_wcsncoll` 時是否發生錯誤，請將 `errno` 設定為 0，然後在呼叫 `_wcsncoll` 之後檢查 `errno`。  
  
## 備註  
 所有這些函式都會根據目前使用中的字碼頁來執行 `string1` 與 `string2` 中第一個 `count` 字元的區分大小寫比較。  只有在字元集順序與字碼頁中的字典編撰字元順序不同時，以及字串比較注意這項差異時，才使用這些函式。  字元集順序是地區設定相關。  這些沒有 `_l` 後置詞之函式的版本會使用目前的地區設定，但具有 `_l` 後置詞的版本會使用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 這些函式全都會驗證它們的參數。  如果 `string1` 或 `string2` 是 null 指標，或者，`count` 大於 `INT_MAX`，則會叫用無效參數處理常式 \(如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述\)。  如果允許繼續執行，這些函式會傳回 `_NLSCMPERROR`，並將 `errno` 設為 `EINVAL`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnccoll`|`_strncoll`|`_mbsncoll`|`_wcsncoll`|  
|`_tcsncoll`|`_strncoll`|[\_mbsnbcoll](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|`_wcsncoll`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strncoll`, `_strncoll_l`|\<string.h\>|  
|`_wcsncoll`, `_wcsncoll_l`|\<wchar.h\> 或 \<string.h\>|  
|`_mbsncoll`, `_mbsncoll_l`|\<mbstring.h\>|  
  
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