---
title: "wcrtomb | Microsoft Docs"
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
  - "wcrtomb"
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
  - "wcrtomb"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字元, 轉換"
  - "多位元組字元"
  - "wcrtomb 函式"
  - "寬字元, 轉換"
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcrtomb
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元複製到其中的多位元組字元表示。  這些函式已有更安全的版本可用，請參閱 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)。  
  
## 語法  
  
```  
size_t wcrtomb(  
   char *mbchar,  
   wchar_t wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcrtomb(  
   char (&mbchar)[size],  
   wchar_t wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### 參數  
 \[out\] `mbchar`  
 產生的多個位元組所轉換的字元。  
  
 \[in\] `wchar`  
 要進行轉換的寬字元。  
  
 \[in\] `mbstate`  
 `mbstate_t` 物件的指標。  
  
## 傳回值  
 如果發生錯誤，傳回要求的位元組數表示這個轉換的多位元組字元，否則則為。  
  
## 備註  
 `wcrtomb` 函式轉換寬字元開始，包含在 `mbstate`中指定的轉換狀態，從 `wchar`中包含的值，將 `mbchar`物件的位址。  傳回值是所需的位元組數表示對應的多位元組字元，不過，它比 `MB_CUR_MAX` 位元組不會傳回。  
  
 如果 `mbstate` 是 null，則會使用包含 `mbchar` 的呈現狀態內部 `mbstate_t` 物件。  如果字元順序 `wchar` 沒有對應的多位元組字元表示，則傳回 \-1，而且 `errno` 設定為 `EILSEQ`。  
  
 `wcrtomb` 函式與 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) 不同於其重新開始的能力。  轉換狀態儲存於 `mbstate` 讓後續呼叫的相同或其他可重新啟動的函式能夠使用。  當混合使用可重新開始和不可重新開始的函式時，結果會是未定義的。  例如，如果後續呼叫 `wcsrtombs` 而不是 `wcstombs`，應用程式可能會使用 `wcsrlen` ，而不是 `wcsnlen`。  
  
 在 C\+\+ 中，這個函式會叫用的範本多載越新，保護這個對應的函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 例外狀況  
 `wcrtomb` 函式是多執行緒安全，只要在目前執行緒的函式不呼叫 `setlocale` ，當函式執行時， `mbstate` 是空的。  
  
## 範例  
  
```  
// crt_wcrtomb.c  
// compile with: /W3  
// This program converts a wide character  
// to its corresponding multibyte character.  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    size_t      sizeOfCovertion = 0;  
    mbstate_t   mbstate;  
    char        mbStr = 0;  
    wchar_t*    wcStr = L"Q";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996  
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead  
    if (sizeOfCovertion > 0)  
    {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wcStr);  
        printf(" was converted to the \"%c\" ", mbStr);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
  **對應的寬字元「、」轉換為「、」多位元組字元。**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wcrtomb`|\<wchar.h\>|  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)