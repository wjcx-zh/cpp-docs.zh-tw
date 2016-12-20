---
title: "_mbclen、mblen、_mblen_l | Microsoft Docs"
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
  - "_mbclen"
  - "mblen"
  - "_mblen_l"
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
  - "mblen"
  - "ftclen"
  - "_mbclen"
  - "tclen"
  - "_ftclen"
  - "_tclen"
  - "mbclen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbclen 函式"
  - "_mblen_l 函式"
  - "_tclen 函式"
  - "mbclen 函式"
  - "mblen 函式"
  - "mblen_l 函式"
  - "tclen 函式"
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbclen、mblen、_mblen_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得長度並判斷多位元組字元的有效性。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
size_t _mbclen(  
   const unsigned char *c   
);  
int mblen(  
   const char *mbstr,  
   size_t count   
);  
int _mblen_l(  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 多位元組字元。  
  
 `mbstr`  
 多位元組字元位元組序列的位址。  
  
 `count`  
 要檢查的位元組數目。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_mbclen` 會傳回 1 或 2，而定，可能的選取多位元組字元 `c` 的長度為 1 或 2 位元組。  不會回傳錯誤給`_mbclen`。  如果 `mbstr` 不是 `NULL`， `mblen` 傳回長度，以位元組為單位，多位元組字元。  如果 `mbstr` 是 `NULL` 或它指向寬字元， `mblen` 會傳回 0。  如果 `mbstr` 所指向的物件不會在第一個字元 `count` 內的有效多位元組字元， `mblen` 會傳回– 1。  
  
## 備註  
 `_mbclen` 函式會傳回長度，以位元組為單位，多位元組字元 `c`。  如果未指向多位元組字元的前導位元組， 如隱含呼叫取決於 `c` 為 `_ismbblead`，則 `_mbclen` 的結果無法預期。  
  
 `mblen` 會傳回位元組長度則為 `mbstr` ，如果它是有效的多位元組字元並判斷多位元組字元有效性與字碼頁。  `mblen` 提供比 `MB_CUR_MAX` 位元組檢查 `mbstr`或更少的位元組包含，則為 `count` ，但不是詳細。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tclen`|巨集或內嵌函式的對應|`_mbclen`|巨集或內嵌函式的對應|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbclen`|\<mbstring.h\>|  
|`mblen`|\<stdlib.h\>|  
|`_mblen_l`|\<stdlib.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_mblen.c  
/* illustrates the behavior of the mblen function  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    int      i;  
    char    *pmbc = (char *)malloc( sizeof( char ) );  
    wchar_t  wc   = L'a';  
  
    printf( "Convert wide character to multibyte character:\n" );  
    wctomb_s( &i, pmbc, sizeof(char), wc );  
    printf( "  Characters converted: %u\n", i );  
    printf( "  Multibyte character: %x\n\n", *pmbc );  
  
    i = mblen( pmbc, MB_CUR_MAX );  
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );  
  
    pmbc = NULL;  
    i = mblen( pmbc, MB_CUR_MAX );  
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );  
}  
```  
  
## Output  
  
```  
Convert wide character to multibyte character:  
  Characters converted: 1  
  Multibyte character: 61  
  
Length in bytes of multibyte character 61: 1  
Length in bytes of NULL multibyte character 0: 0  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbccpy、\_mbccpy\_l](../../c-runtime-library/reference/mbccpy-mbccpy-l.md)   
 [strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)