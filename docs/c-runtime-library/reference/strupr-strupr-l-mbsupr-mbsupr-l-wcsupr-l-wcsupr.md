---
title: "_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr | Microsoft Docs"
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
  - "_mbsupr_l"
  - "_mbsupr"
  - "_strupr_l"
  - "_wcsupr"
  - "_wcsupr_l"
  - "_strupr"
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
  - "_mbsupr"
  - "_ftcsupr"
  - "mbsupr"
  - "_tcsupr"
  - "strupr_l"
  - "_fstrupr"
  - "_strupr"
  - "mbsupr_l"
  - "_wcsupr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrupr 函式"
  - "_ftcsupr 函式"
  - "_mbsupr 函式"
  - "_mbsupr_l 函式"
  - "_strupr 函式"
  - "_strupr_l 函式"
  - "_tcsupr 函式"
  - "_tcsupr_l 函式"
  - "_wcsupr 函式"
  - "_wcsupr_l 函式"
  - "轉換大小寫, CRT 函式"
  - "fstrupr 函式"
  - "ftcsupr 函式"
  - "mbsupr 函式"
  - "mbsupr_l 函式"
  - "字串轉換 [C++], 大小寫"
  - "字串 [C++], 大小寫"
  - "字串 [C++], 轉換大小寫"
  - "strupr 函式"
  - "strupr_l 函式"
  - "tcsupr 函式"
  - "tcsupr_l 函式"
  - "大寫, 轉換字串為"
  - "wcsupr 函式"
  - "wcsupr_l 函式"
ms.assetid: caac8f16-c233-41b6-91ce-575ec7061b77
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將字串轉換為大寫。  更多這些函式的可用安全版本，請參閱 [\_strupr\_s、\_strupr\_s\_l、\_mbsupr\_s、\_mbsupr\_s\_l、\_wcsupr\_s、\_wcsupr\_s\_l](../../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbsupr` 與 `_mbsupr_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *_strupr(  
   char *str   
);  
wchar_t *_wcsupr(  
   wchar_t *str   
);  
unsigned char *_mbsupr(  
   unsigned char *str   
);  
char *_strupr_l(  
   char *str,  
   _locale_t locale  
);  
wchar_t *_wcsupr_l(  
   wchar_t *str,  
   _locale_t locale  
);  
unsigned char *_mbsupr_l(  
   unsigned char *str,  
   _locale_t locale  
);  
template <size_t size>  
char *_strupr(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wcsupr(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
unsigned char *_mbsupr(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
char *_strupr_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
wchar_t *_wcsupr_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
unsigned char *_mbsupr_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 大寫的字串。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 傳回變更後字串的指標。  由於修改已完成，則傳回的指標與傳遞輸入引數的指標相同。  未保留表示錯誤的傳回值。  
  
## 備註  
 `_strupr` 函式轉換，準備就緒， `str` 中的每個小寫字母轉換為大寫。  轉換取決於地區設定的 `LC_CTYPE` 分類設定。  其他字元不會受到影響。  如需`LC_CTYPE`詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些沒有 `_l` 尾碼的函式版本使用目前的地區設定；有`_l`尾碼的函式版本則使用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 `_wcsupr` 和 `_mbsupr` 是 `_strupr` 的寬字元和多位元組字元版本。  `_wcsupr` 的引數和傳回值是寬字元字串，而 `_mbsupr` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 如果 `str` 如  [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述為 null 指標，則叫用無效參數處理常式。  如果允許繼續執行，這些函式會傳回原始字串並將 `errno` 設為 `EINVAL` 。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsupr`|`_strupr`|`_mbsupr`|`_wcsupr`|  
|`_tcsupr_l`|`_strupr_l`|`_mbsupr_l`|`_wcsupr_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strupr`, `_strupr_l`|\<string.h\>|  
|`_wcsupr`, `_wcsupr_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsupr`, `_mbsupr_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [strlwr](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)  
  
## 請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strlwr、\_wcslwr、\_mbslwr、\_strlwr\_l、\_wcslwr\_l、\_mbslwr\_l](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)