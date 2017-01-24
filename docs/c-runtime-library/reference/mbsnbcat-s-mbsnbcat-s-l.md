---
title: "_mbsnbcat_s、_mbsnbcat_s_l | Microsoft Docs"
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
  - "_mbsnbcat_s_l"
  - "_mbsnbcat_s"
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
  - "_mbsnbcat_s"
  - "mbsnbcat_s"
  - "_mbsnbcat_s_l"
  - "mbsnbcat_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcat_s 函式"
  - "_mbsnbcat_s_l 函式"
  - "_tcsncat 函式"
  - "_tcsncat_s_l 函式"
  - "mbsnbcat_s 函式"
  - "mbsnbcat_s_l 函式"
  - "tcsncat 函式"
  - "tcsncat_s_l 函式"
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbcat_s、_mbsnbcat_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將另一個多位元組字元字串的最多前 `n` 個位元組附加至多位元組字元字串。  這些是 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md) 之具有安全性增強功能的版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t _mbsnbcat_s(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count   
);  
errno_t _mbsnbcat_s_l(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbcat_s(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbcat_s_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `dest`  
 以 null 終止的多位元組字元目的字串。  
  
 `sizeInBytes`  
 以位元組為單位的 `dest` 緩衝區大小。  
  
 `src`  
 以 null 終止的多位元組字元來源字串。  
  
 `Count`  
 要從 `src` 附加至 `dest` 的位元組數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果成功則為零，否則為錯誤碼。  
  
### 錯誤狀況  
  
|`Dest`|`sizeInBytes`|`src`|傳回值|  
|------------|-------------------|-----------|---------|  
|`NULL`|任何|任何|`EINVAL`|  
|任何|\<\= 0|任何|`EINVAL`|  
|任何|任何|`NULL`|`EINVAL`|  
  
 如果發生其中任何一種錯誤狀況，此函式會產生無效的參數錯誤，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果已處理此錯誤，則此函式會傳回 `EINVAL`，並將 `errno` 設定為 `EINVAL`。  
  
## 備註  
 `_mbsnbcat_s` 函式會將 `src` 的最多前 `count` 個位元組附加至 `dest`。  如果緊接在 `dest` 中之 null 字元之前的位元組是前導位元組，則 `src` 的初始位元組會將其覆寫。  否則，`src` 的初始位元組會覆寫 `dest` 之結束的 null 字元。  如果在已附加 `count` 個位元組之前，於 `src` 出現 null 位元組，則 `_mbsnbcat_s` 會附加 `src` 之中直到該 null 字元為止的所有位元組。  如果 `count` 大於 `src` 的長度，則會使用 `src` 的長度來取代 `count`。  此產生的字串便會由 null 字元所終止。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響；如需詳細資訊，請參閱 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些函式的版本均相同，除了沒有 `_l` 後置字元的函式會使用目前的地區設定，而具有 `_l` 後置字元的函式會改用傳入的地區設定參數。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，樣板多載簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以自動使用其較新且較安全的函式，藉此取代較舊且較不安全的函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncat`|[strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat_s`|[wcsncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_s_l`|`_strncat_s_l`|`_mbsnbcat_s_l`|`_wcsncat_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnbcat_s`|\<mbstring.h\>|  
|`_mbsnbcat_s_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_strncnt、\_wcsncnt、\_mbsnbcnt、\_mbsnbcnt\_l、\_mbsnccnt、\_mbsnccnt\_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [\_mbsnbcpy、\_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [\_mbsnbcpy\_s、\_mbsnbcpy\_s\_l](../../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)   
 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)