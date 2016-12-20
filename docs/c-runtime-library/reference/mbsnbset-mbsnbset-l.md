---
title: "_mbsnbset、_mbsnbset_l | Microsoft Docs"
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
  - "_mbsnbset"
  - "_mbsnbset_l"
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
  - "mbsnbset"
  - "mbsnbset_l"
  - "_mbsnbset"
  - "_mbsnbset_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbset 函式"
  - "_mbsnbset_l 函式"
  - "_tcsnset 函式"
  - "_tcsnset_l 函式"
  - "mbsnbset 函式"
  - "mbsnbset_l 函式"
  - "tcsnset 函式"
  - "tcsnset_l 函式"
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbset、_mbsnbset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定多位元組字元字串的第一個 `n` 位元組至指定的字元。  更多這些函式的可用安全版本，請參閱 [\_mbsnbset\_s、\_mbsnbset\_s\_l](../../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned char *_mbsnbset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnbset_l(  
   unsigned char *str,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `str`  
 待變更字串。  
  
 `c`  
 單一位元組或多位元組字元設定。  
  
 `count`  
 要設定的位元組數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_mbsnbset` 傳回變更後字串的指標。  
  
## 備註  
 `_mbsnbset` 和 `_mbsnbset_l` 函式最多將第一個 `count` 位元組 `str` 設為 `c`。  如果 `count` 大於 `str` 的長度，長度為 `str` 而非 `count` 的。  如果 `c` 是多位元組字元，且無法完全設定成 `count`指定的最後一個位元組，最後一個位元組會填補一個空白字元。  `_mbsnbset` 和 `_mbsnbset_l`不會將 NULL 放在 `str`的結尾。  
  
 `_mbsnbset` 和 `_mbsnbset_l`與 `_mbsnset` 類似，不過，它設定 `count` 位元組而不是 `c` 的 `count` 字元。  
  
 如果 `str` 是 `NULL` 或 `count` 為零，這個函式會產生如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述的無效參數例外狀況。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `NULL`。  此外，如果 `c` 不是有效的多位元組字元， `errno` 會設定為 `EINVAL` ，並使用空格。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式的 `_mbsnbset` 版本使用地區設定相關的行為的目前地區設定；`_mbsnbset_l` 版本是一樣的，只不過它使用的是傳入的地區設定而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 **安全性提示** 這個應用程式開發介面會導致緩衝區滿溢問題而有潛在的威脅。  緩衝區溢位問題是系統攻擊的常見方法，它會導致權限不確定性的增加。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnbset`|\<mbstring.h\>|  
|`_mbsnbset_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_mbsnbset.c  
// compile with: /W3  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset( string, '*', 4 ); // C4996  
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s  
   printf( "After:  %s\n", string );  
}  
```  
  
## Output  
  
```  
Before: This is a test  
After:  **** is a test  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)