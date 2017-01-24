---
title: "mbstowcs、_mbstowcs_l | Microsoft Docs"
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
  - "mbstowcs"
  - "_mbstowcs_l"
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
apitype: "DLLExport"
f1_keywords: 
  - "mbstowcs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbstowcs_l 函式"
  - "mbstowcs 函式"
  - "mbstowcs_l 函式"
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
caps.latest.revision: 30
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbstowcs、_mbstowcs_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元序列至對應的多位元組字元。  這些函式已有更安全的版本可用，請參閱 [mbstowcs\_s、\_mbstowcs\_s\_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)。  
  
## 語法  
  
```  
size_t mbstowcs(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count   
);  
size_t _mbstowcs_l(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t mbstowcs(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _mbstowcs_l(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 \[out\] `wcstr`  
 寬字元序列的位址。  
  
 \[in\] `mbstr`  
 空結尾多位元組字元序列的位址。  
  
 \[in\] `count`  
 要轉換的最大多位元字元數。  
  
 \[in\] `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果 `mbstowcs` 轉換成功來源字串，它會傳回轉換的多位元組字元數。  如果 `wcstr` 引數是 `NULL`，函式會傳回所需大小 \(以寬字元計算\) 的目的字串。  如果 `mbstowcs` 遇到無效的多位元組字元，則會傳回– 1。  如果傳回值是 `count`，寬字元字串不是以 null 終止。  
  
> [!IMPORTANT]
>  確認 `wcstr` 和 `mbstr` 不重疊，而 `count` 正確反映轉換寬字元的數目。  
  
## 備註  
 `mbstowcs` 函式轉換由 `count` 多位元組字元的最大數目指向 `mbstr` 套用至目前地區設定取決於對應的寬字元的字串。  它儲存產生的寬字元字串以 `wcstr`表示的位址*。*結果類似一系列呼叫於 `mbtowc`。  如果 `mbstowcs` 發生單一位元組 null 字元 \(「\\ 0 "\) 或前面，或當發生 `count` ，它會將 null 字元之寬字元 L null 字元 \(」\\ 0 "\) 和中止。  因此，在轉換期間，只有當遇到多位元 NULL 字元時 `wcstr` 的寬字元字串才是 NULL 結尾。  如果被 `wcstr` 和 `mbstr` 指向的序列重疊，行為是未定義。  
  
 如果 `wcstr` 引數是 `NULL`， `mbstowcs` 會傳回由轉換寬字元數目，包括 null 結束字元。  必須以 null 結束之來源字串才能傳回正確的值。  如果您需要產生的寬字元字串 NULL 結尾，請將傳回的值。  
  
 如果 `mbstr`引數為`NULL`，或如果 `count`是  \> `INT_MAX`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，errno會被設為 `EINVAL` ，函式並傳回 \-1。  
  
 `mbstowcs` 在區域設定相依的動作時使用任何的區域設定。 `_mbstowcs_l`  除了使用傳入的區域設定以外其餘相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`mbstowcs`|\<stdlib.h\>|  
|`_mbstowcs_l`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_mbstowcs.c  
// compile with: /W3  
// illustrates the behavior of the mbstowcs function  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main( void )  
{  
    size_t size;  
    int nChar = 2; // number of characters to convert  
    int requiredSize;  
  
    unsigned char    *pmbnull  = NULL;  
    unsigned char    *pmbhello = NULL;  
    char* localeInfo;  
  
    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters  
    wchar_t *pwc;  
  
    /* Enable the Japanese locale and codepage */  
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");  
    printf("Locale information set to %s\n", localeInfo);  
  
    printf( "Convert to multibyte string:\n" );  
  
    requiredSize = wcstombs( NULL, pwchello, 0); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    printf("  Required Size: %d\n", requiredSize);  
  
    /* Add one to leave room for the null terminator. */  
    pmbhello = (unsigned char *)malloc( requiredSize + 1);  
    if (! pmbhello)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    if (size == (size_t) (-1))  
    {  
        printf("Couldn't convert string. Code page 932 may"  
                " not be available.\n");  
        return 1;  
    }  
    printf( "  Number of bytes written to multibyte string: %u\n",  
            (unsigned int) size );  
    printf( "  Hex values of the " );  
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",  
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );  
    printf( "  Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");  
  
    printf( "Convert back to wide-character string:\n" );  
  
    /* Assume we don't know the length of the multibyte string.  
     Get the required size in characters, and allocate enough space. */  
  
    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996  
    /* Add one to leave room for the NULL terminator */  
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));  
    if (! pwc)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996  
    if (size == (size_t) (-1))  
    {  
       printf("Couldn't convert string--invalid multibyte character.\n");  
    }  
    printf( "  Characters converted: %u\n", (unsigned int)size );  
    printf( "  Hex value of first 2" );  
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );  
    free(pwc);  
    free(pmbhello);  
}  
```  
  
  **地區設定資訊設定為 Japanese\_Japan.932**  
**轉換為多位元字串：**  
 **要求的大小: 4**  
 **提供多位元組字串的位元組數目:4**  
 **多位元組字元的十六進位值:0x82 0xa0 0x82 0xa1**  
 **到 0x9f 的字碼頁 932 使用 0x81 當前導位元組。**  
**轉換回寬字元字串：**  
 **Characters converted: 2**  
 **前 2 寬字元的十六進位值:0x3042 0x3043**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)