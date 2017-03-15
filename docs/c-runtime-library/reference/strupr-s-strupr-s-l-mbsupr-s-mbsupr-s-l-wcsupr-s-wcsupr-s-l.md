---
title: "_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strupr_s"
  - "_strupr_s_l"
  - "_mbsupr_s"
  - "_wcsupr_s_l"
  - "_mbsupr_s_l"
  - "_wcsupr_s"
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
  - "strupr_s"
  - "mbsupr_s"
  - "wcsupr_s"
  - "_mbsupr_s_l"
  - "mbsupr_s_l"
  - "wcsupr_s_l"
  - "_wcsupr_s"
  - "_tcsupr_s_l"
  - "_mbsupr_s"
  - "_tcsupr_s"
  - "strupr_s_l"
  - "_wcsupr_s_l"
  - "_strupr_s"
  - "_strupr_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsupr_s 函式"
  - "_mbsupr_s_l 函式"
  - "_strupr_s 函式"
  - "_strupr_s_l 函式"
  - "_tcsupr_s 函式"
  - "_tcsupr_s_l 函式"
  - "_wcsupr_s 函式"
  - "_wcsupr_s_l 函式"
  - "轉換大小寫, CRT 函式"
  - "mbsupr_s 函式"
  - "mbsupr_s_l 函式"
  - "字串轉換 [C++], 大小寫"
  - "字串 [C++], 大小寫"
  - "字串 [C++], 轉換大小寫"
  - "strupr_s 函式"
  - "strupr_s_l 函式"
  - "tcsupr_s 函式"
  - "tcsupr_s_l 函式"
  - "大寫, 轉換字串為"
  - "wcsupr_s 函式"
  - "wcsupr_s_l 函式"
ms.assetid: 82d3a273-9f6f-4a26-9560-919d891e4581
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# _strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前的地區設定或傳遞的指定地區設定將字串轉換為大寫。  這些 [\_strupr、\_strupr\_l、\_mbsupr、\_mbsupr\_l、\_wcsupr\_l、\_wcsupr](../../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbsupr_s` 和 `_mbsupr_s_l` 不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t _strupr_s(  
   char *str,  
   size_t numberOfElements  
);  
errno_t _wcsupr_s(  
   wchar_t * str,  
   size_t numberOfElements  
);  
errno_t _strupr_s_l(  
   char * str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _wcsupr_s_l(  
   wchar_t * str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _mbsupr_s(  
   unsigned char *str,  
   size_t numberOfElements  
);  
errno_t _mbsupr_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _strupr_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wcsupr_s(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _strupr_s_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _wcsupr_s_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsupr_s(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _mbsupr_s_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 大寫的字串。  
  
 `numberOfElements`  
 緩衝區的大小。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 如果成功則得到 0 值；如果失敗，則結果為不為 0 的錯誤碼。  
  
 這些函式會驗證它們的參數。  如果 `str` 為 `NULL` 指標，則無效參數處理常式會被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式會傳回 `EINVAL` 並將 `errno` 設定為 `EINVAL`。  如果 `numberOfElements` 小於字串長度，函式一樣傳回 `ERANGE` 並將 `errno` 設定為 `ERANGE`。  
  
## 備註  
 `_strupr_s` 函式恰當地將 `str` 中的每個小寫字母轉換為大寫。  `_wcsupr_s` 是 `_strupr_s`的寬字元版本。  `_mbsupr_s` 是 `_strupr_s` 多位元組字元版本。  
  
 轉換取決於地區設定的 `LC_CTYPE` 分類設定。  其他字元不會受到影響。  如需`LC_CTYPE`的詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些沒有 `_l` 尾碼的函式版本使用目前的地區設定；有`_l` 尾碼的函式版本則使用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsupr_s`|`_strupr_s`|`_mbsupr_s`|`_wcsupr_s`|  
|`_tcsupr_s_l`|`_strupr_s_l`|`_mbsupr_s_l`|`_wcsupr_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strupr_s`, `_strupr_s_l`|\<string.h\>|  
|`_wcsupr_s`, `_wcsupr_s_l`, `_mbsupr_s`, `_mbsupr_s_l`|\<string.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱[\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)中的範例。  
  
## .NET Framework 對等用法  
 [System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)  
  
## 請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)