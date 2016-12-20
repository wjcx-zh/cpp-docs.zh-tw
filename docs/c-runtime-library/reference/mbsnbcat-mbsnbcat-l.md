---
title: "_mbsnbcat、_mbsnbcat_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbcat_l"
  - "_mbsnbcat"
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
  - "mbsnbcat"
  - "mbsnbcat_l"
  - "_mbsnbcat"
  - "_mbsnbcat_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcat 函式"
  - "_mbsnbcat_l 函式"
  - "_tcsncat 函式"
  - "_tcsncat_l 函式"
  - "mbsnbcat 函式"
  - "mbsnbcat_l 函式"
  - "tcsncat 函式"
  - "tcsncat_l 函式"
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbcat、_mbsnbcat_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

最多附加第一個 `n` 位元組的多位元組字元字串到另一個。  更多這些函式的可用安全版本，請參閱 [\_mbsnbcat\_s、\_mbsnbcat\_s\_l](../../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned char *_mbsnbcat(  
   unsigned char *dest,  
   const unsigned char *src,  
   size_t count   
);  
unsigned char *_mbsnbcat_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
unsigned char *_mbsnbcat(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsnbcat_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `dest`  
 null 結尾多位元組字元的字串。  
  
 `src`  
 null 結尾多位元組字元來源字串。  
  
 `count`  
 位元組數從附加的 `src` 為 `dest`。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_mbsnbcat`傳回一個指標到目的地字串。  未保留表示錯誤的傳回值。  
  
## 備註  
 `_mbsnbcat` 函式，至多附加， `src` 第一個 `count` 位元至 `dest`中。  如果在 Null 字元之前的位元組在 `dest` 是前導位元組，初始位元組 `src` 覆寫這個前導位元組。  否則，初始位元組 `src` 覆寫 `dest`結束的 null 字元。  如果 null 位元組出現在 `src` ， `count` 附加前，位元組附加\_`mbsnbcat` 從 `src`中的所有位元組，由 null 字元。  如果 `count` 大於 `src` 的長度，長度為 `src` 而非 `count` 的。  結果字串是以 NULL 字元結束。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  使用目前地區設定地區設定相關行為的`_mbsnbcat`版本；`_mbsnbcat_l`版本除了傳遞不同的地區設定參數外都一樣。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 **Security Note** 使用 null 結尾的字串。  null 結尾字串不能超過目的緩衝區的大小。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
 如果 `dest` 或 `src` 是 `NULL`，函式會產生不正確的參數錯誤，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果錯誤已處理，則函式會回傳 `EINVAL`並將 `errno` 設為 `EINVAL`。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcsncat`|[strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat`|[wcsncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_l`|`_strncat_l`|`_mbsnbcat_l`|`_wcsncat_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnbcat`|\<mbstring.h\>|  
|`_mbsnbcat_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_strncnt、\_wcsncnt、\_mbsnbcnt、\_mbsnbcnt\_l、\_mbsnccnt、\_mbsnccnt\_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [\_mbsnbcpy、\_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [\_mbsnbicmp、\_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [\_mbsnbcat\_s、\_mbsnbcat\_s\_l](../../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)