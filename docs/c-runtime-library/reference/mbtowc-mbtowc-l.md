---
title: "mbtowc、_mbtowc_l | Microsoft Docs"
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
  - "mbtowc"
  - "_mbtowc_l"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbtowc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbtowc_l 函式"
  - "mbtowc 函式"
  - "mbtowc_l 函式"
ms.assetid: dfd1c8a7-e73a-4307-9353-53b70b45d4d1
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbtowc、_mbtowc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換多位元組字元至對應的寬字元  
  
## 語法  
  
```  
int mbtowc(  
   wchar_t *wchar,  
   const char *mbchar,  
   size_t count   
);  
int _mbtowc_l(  
   wchar_t *wchar,  
   const char *mbchar,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 *wchar*  
 寬字元 \(`wchar_t` 型別\) 的位址。  
  
 `mbchar`  
 多位元組字元位元組序列的位址。  
  
 *count*  
 要檢查的位元組數目。  
  
 *Locale \- 地區設定*  
 要使用的地區設定。  
  
## 傳回值  
 如果 **mbchar** 不是 **NULL** ，且如果 `mbchar` 指向表單構成有效多位元組字元的物件， `mbtowc` 傳回多位元組字元的位元組的長度。  如果 `mbchar` 是 **NULL** 或它所指向的物件是寬字元 null 字元 \(L'\\0'\)，則函式會傳回 0。  如果 `mbchar` 所指向的物件不會在第一個字元 *count* 內的有效多位元組字元，會傳回 –1。  
  
## 備註  
 如果 `mbchar` 不是 **NULL**，`mbtowc` 函式轉換 `mbchar` 指向的 *count* 或少量位元組至對應的寬字元。  如果 *wchar* 不是 **NULL**，`mbtowc` 儲存產生的寬字元至 *wchar*。  `mbtowc` 不會檢查多餘 `MB_CUR_MAX` 個位元組。 `mbtowc` 使用目前地區設定地區相關行為; `_mbtowc_l` 作用相同，但是使用傳進的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`mbtowc`|\<stdlib.h\>|  
|**\_mbtowc\_l**|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_mbtowc.c  
/* Illustrates the behavior of the mbtowc function  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    int      i;  
    char    *pmbc    = (char *)malloc( sizeof( char ) );  
    wchar_t  wc      = L'a';  
    wchar_t *pwcnull = NULL;  
    wchar_t *pwc     = (wchar_t *)malloc( sizeof( wchar_t ) );  
    printf( "Convert a wide character to multibyte character:\n" );  
    wctomb_s( &i, pmbc, sizeof(char), wc );  
    printf( "  Characters converted: %u\n", i );  
    printf( "  Multibyte character: %x\n\n", *pmbc );  
  
    printf( "Convert multibyte character back to a wide "  
            "character:\n" );  
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );  
    printf( "  Bytes converted: %u\n", i );  
    printf( "  Wide character: %x\n\n", *pwc );  
    printf( "Attempt to convert when target is NULL\n" );  
    printf( "  returns the length of the multibyte character:\n" );  
    i = mbtowc( pwcnull, pmbc, MB_CUR_MAX );  
    printf( "  Length of multibyte character: %u\n\n", i );  
  
    printf( "Attempt to convert a NULL pointer to a" );  
    printf( " wide character:\n" );  
    pmbc = NULL;  
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );  
    printf( "  Bytes converted: %u\n", i );  
}  
```  
  
## Output  
  
```  
Convert a wide character to multibyte character:  
  Characters converted: 1  
  Multibyte character: 61  
  
Convert multibyte character back to a wide character:  
  Bytes converted: 1  
  Wide character: 61  
  
Attempt to convert when target is NULL  
  returns the length of the multibyte character:  
  Length of multibyte character: 1  
  
Attempt to convert a NULL pointer to a wide character:  
  Bytes converted: 0  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)