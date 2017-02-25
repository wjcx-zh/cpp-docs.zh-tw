---
title: "wcrtomb_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcrtomb_s"
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
  - "wcrtomb_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "寬字元轉換"
  - "wcrtomb_s 函式"
  - "多位元組字元"
  - "轉換的字元"
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# wcrtomb_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寬字元轉換為多位元組字元表示法。 版本 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char *mbchar,  
   size_t sizeOfmbchar,  
   wchar_t *wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char (&mbchar)[size],  
   wchar_t *wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### 參數  
 \[輸出\] `pReturnValue`  
 如果發生錯誤則傳回寫入的位元組數目，則為\-1。  
  
 \[輸出\] `mbchar`  
 產生的多位元組轉換字元。  
  
 \[in\] `sizeOfmbchar`  
 大小 `mbchar` 變數，以位元組為單位。  
  
 \[in\] `wchar`  
 要轉換的寬字元。  
  
 \[in\] `mbstate`  
 `mbstate_t` 物件的指標。  
  
## 傳回值  
 傳回零或 `errno` 值發生錯誤。  
  
## 備註  
 `wcrtomb_s` 函式會將轉換寬字元，包含在指定的轉換狀態開始 `mbstate`, ，在所包含的值從 `wchar`, ，放入所代表的位址 `mbchar`。`pReturnValue` 值將會是數個位元組轉換，但不是超過 `MB_CUR_MAX` 個位元組，則為\-1，發生錯誤。  
  
 如果 `mbstate` 為 null，內部 `mbstate_t` 會使用轉換狀態。 如果字元包含在 `wchar` 沒有對應的多位元組字元，值 `pReturnValue` 是\-1，此函數會傳回 `errno` 值 `EILSEQ`。  
  
 `wcrtomb_s` 函式不同於 [wctomb\_s、\_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md) 能力。 針對相同或其他可重新啟動的函式的後續呼叫，轉換狀態會儲存在 `mbstate` 中。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，應用程式會使用 `wcsrlen` 而 `wcslen`, ，如果的後續呼叫 `wcsrtombs_s` 而不是使用 `wcstombs_s.`  
  
 C \+ \+ 中使用這個函式簡化了範本多載。多載可自動推斷緩衝區長度 （因而不須指定大小引數），也可以自動取代較舊、 不安全的函式成較新且安全的對應。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 例外狀況  
 `wcrtomb_s` 函式是多執行緒安全，因為沒有目前的執行緒中的函式呼叫 `setlocale` 時正在執行，此函式和 `mbstate` 為 null。  
  
## 範例  
  
```  
// crt_wcrtomb_s.c  
// This program converts a wide character  
// to its corresponding multibyte character.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    errno_t     returnValue;  
    size_t      pReturnValue;  
    mbstate_t   mbstate;  
    size_t      sizeOfmbStr = 1;  
    char        mbchar = 0;  
    wchar_t*    wchar = L"Q\0";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),  
                            *wchar, &mbstate);  
    if (returnValue == 0) {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wchar);  
        printf(" was converted to a the \"%c\" ", mbchar);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
```Output  
已轉換的對應寬字元"Q"的"Q"多位元組字元。  
```  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wcrtomb_s`|\<wchar.h\>|  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)