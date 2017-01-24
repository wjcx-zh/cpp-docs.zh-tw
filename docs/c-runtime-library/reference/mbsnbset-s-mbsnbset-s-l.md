---
title: "_mbsnbset_s、_mbsnbset_s_l | Microsoft Docs"
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
  - "_mbsnbset_s_l"
  - "_mbsnbset_s"
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
  - "mbsnbset_s"
  - "_mbsnbset_s_l"
  - "_mbsnbset_s"
  - "mbsnbset_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbset_s 函式"
  - "_mbsnbset_s_l 函式"
  - "_tcsnset_s 函式"
  - "_tcsnset_s_l 函式"
  - "mbsnbset_s 函式"
  - "mbsnbset_s_l 函式"
  - "tcsnset_s 函式"
  - "tcsnset_s_l 函式"
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbset_s、_mbsnbset_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將多位元組字元字串的前 `n` 個位元組設定為指定的字元。  這些版本的 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md) 具有安全性增強功能，如[CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t _mbsnbset_s(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count   
);  
errno_t _mbsnbset_s_l(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbset_s(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbset_s_l(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 待變更字串。  
  
 `size`  
 字串緩衝區的大小。  
  
 `c`  
 單一位元組或多位元組字元的設定。  
  
 `count`  
 要設定的位元組數目。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果成功則為零，否則為錯誤碼。  
  
## 備註  
 `_mbsnbset_s` 和 `_mbsnbset_s_l` 函式會將 `str` 的最多前 `count` 個位元組設為 `c`。  如果 `count` 大於 `str` 的長度，則會使用 `str` 的長度，而非 `count`。  如果 `c` 是多位元組字元，而且無法將其完全設定到 `count` 所指定的最後一個位元組，則此最後一個位元組會以空白的字元填補。  `_mbsnbset_s` 和 `_mbsnbset_s_l` 並不會在 `str` 的結尾置入終止的 null 。  
  
 `_mbsnbset_s` 和 `_mbsnbset_s_l` 類似 `_mbsnset`，只不過它們設定 `count` 位元組，而非 `c` 的 `count` 字元。  
  
 如果 `str` 是 `NULL`，或 `count` 為零，則此函式會產生無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  若允許繼續執行，`errno` 會設為 `EINVAL`，且此函式會傳回 `NULL`。  此外，如果 `c` 不是有效的多位元組字元，則會將 `errno` 設為 `EINVAL`，並改用一個空格。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響；如需詳細資訊，請參閱 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這個函式的 `_mbsnbset_s` 版本會針對地區設定相關的行為使用目前的地區設定；而 `_mbsnbset_s_l` 版本也一樣，除了改用傳入的地區設定以外。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，樣板多載簡化了這些函式的使用方式；此多載可自動推斷緩衝區長度，因此不須指定大小引數。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnset_s`|`_strnset_s`|`_mbsnbset_s`|`_wcsnset_s`|  
|`_tcsnset_s_l`|`_strnset_s _l`|`_mbsnbset_s_l`|`_wcsnset_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnbset_s`|\<mbstring.h\>|  
|`_mbsnbset_s_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_mbsnbset_s.c  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset_s( string, sizeof(string), '*', 4 );  
   printf( "After:  %s\n", string );  
}  
```  
  
## 輸出  
  **Before: This is a test**  
**After:  \*\*\*\* is a test**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)