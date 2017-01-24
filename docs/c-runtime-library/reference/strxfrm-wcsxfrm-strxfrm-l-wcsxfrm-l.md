---
title: "strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l | Microsoft Docs"
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
  - "strxfrm"
  - "_wcsxfrm_l"
  - "_strxfrm_l"
  - "wcsxfrm"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strxfrm"
  - "_tcsxfrm"
  - "wcsxfrm"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strxfrm_l 函式"
  - "_tcsxfrm 函式"
  - "_wcsxfrm_l 函式"
  - "字串比較 [C++], 轉換字串"
  - "字串 [C++], 比較地區設定"
  - "strxfrm 函式"
  - "strxfrm_l 函式"
  - "tcsxfrm 函式"
  - "wcsxfrm 函式"
  - "wcsxfrm_l 函式"
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換是根據地區設定特定資訊的字串。  
  
## 語法  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `strDest`  
 目標字串。  
  
 `strSource`  
 來源字串。  
  
 `count`  
 要讀取以放置在`strDest`*.*的最大字元數  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 回傳已轉換的字串長度，不包括結束的null字元。  如果回傳值大於或等於 `count`，則`strDest` 不可預期。  若有錯誤，每個函式會設定`errno` 並傳回 `INT_MAX`。  如需無效字元， `errno` 設定為 `EILSEQ`。  
  
## 備註  
 `strxfrm` 函式轉換字串指向 `strSource` 成儲存於 `strDest`中的新的自動分頁的表單。  沒有超過 `count` 個字元，包括 null 字元，轉換並放入結果字串。  使用地區設定的 `LC_COLLATE` 分類設定，轉換進行。  如需`LC_COLLATE`的詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  `strxfrm` 為其地區設定相關行為使用目前的地區設定; `_strxfrm_l`除了使用地區設定來取代目前的地區設定都與之相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在轉換之後，呼叫具有兩個已轉換字串yield結果的`strcmp`的方式和呼叫具有套用至兩個原始字串的`strcoll` 的方法相同。  與 `strcoll` 和 `stricoll`， `strxfrm` 會自動處理多位元組字元字串。  
  
 `wcsxfrm` 是 `strxfrm` 的寬字元版本，`wcsxfrm` 的字串引數是寬字元指標。  對於`wcsxfrm`，在字串轉換後，呼叫具有兩個已轉換字串yield結果的`wcscmp`的方式和呼叫具有套用至兩個原始字串的`wcscoll`的方法相同。  `wcsxfrm` 和 `strxfrm` 其餘行為相同。  `wcsxfrm` 為其地區設定相關行為使用目前的地區設定; `_wcsxfrm_l` 使用地區設定來取代目前的地區設定。  
  
 這些函式會驗證它們的參數。  如果 `strSource` 為 null 指標，或 `strDest` 為 null 指標 \(除非計數為零\)，或者如果 `count` 大於 `INT_MAX`，則無效的參數會叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 `INT_MAX`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 在「C」地區設定，字元順序字元集 \(ASCII 字元集\) 的字典會相同。  然而，在其他地區設定中，字元順序字元集可能與傳統詞的已纂順序不同。  例如在某些歐洲地區，在字元集中字碼頁字元「a」\(值 0x61\) 在「&\#x00E4;」\(值 0xE4\) 之前，但字典中字元「ä 」在字元「a」之前。  
  
 在字元集和字典會不同地區設定，在原始字串中使用 `strxfrm` 在結果字串之 `strcmp` 屬性的字串字典會根據目前地區設定的 `LC_COLLATE` 分類設定。  因此，動詞命令一般地比較兩個字串在上述地區設定，在原始字串中使用 `strxfrm` ，然後在結果字串的 `strcmp` 。  或者，您可以使用 `strcoll` 而不是原始字串的 `strcmp` 。  
  
 `strxfrm` 基本上是包裝函式在 [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) 周圍以及 `LCMAP_SORTKEY`。  
  
 下列運算式的值需要陣列大小保留來源字串的 `strxfrm` 轉換:  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 只在「C」地區設定中，`strxfrm` 等同於下列:  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strxfrm`|\<string.h\>|  
|`wcsxfrm`|\<string.h\> 或 \<wchar.h\>|  
|`_strxfrm_l`|\<string.h\>|  
|`_wcsxfrm_l`|\<string.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)