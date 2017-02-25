---
title: "wcstombs、_wcstombs_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcstombs"
  - "_wcstombs_l"
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
  - "wcstombs"
  - "_wcstombs_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wcstombs_l 函式"
  - "字元, 轉換"
  - "字串轉換, 多位元組字元字串"
  - "字串轉換, 寬字元"
  - "wcstombs 函式"
  - "wcstombs_l 函式"
  - "寬字元, 轉換"
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# wcstombs、_wcstombs_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元序列至對應的多位元組字元。  這些函式已有更安全的版本可用，請參閱 [wcstombs\_s、\_wcstombs\_s\_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)。  
  
## 語法  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `mbstr`  
 多位元組字元序列的位址。  
  
 `wcstr`  
 寬字元序列的位址。  
  
 `count`  
 在多位元組可以儲存的最大位元組數輸出字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果 `wcstombs` 轉換成功多位元組字串，它會傳回位元組數目寫入多位元組輸出資料，不包括終止的 `NULL` \(如果有的話\)。  如果 `mbstr` 引數是 `NULL`， `wcstombs` 在目的資料的位元組傳回所需大小。  如果無法轉換到多位元組字元的 `wcstombs` 遇到寬字元，它會傳回所轉換的 1 輸入 `size_t` 和 `errno` 設為 `EILSEQ`。  
  
## 備註  
 `wcstombs` 函式在 `mbstr` 陣列轉換寬字元字串指向 `wcstr` 對應的多位元組字元並儲存結果。  `count` 參數表示即在多位元組輸出字串的最大位元組數 \(大小可以儲存為 `mbstr`\)。  一般而言，不知道需要多少位元組，而轉換寬字元字串時。  一些寬字元只需要在輸出字串的位元組;其他兩個要求。  如果在多位元組的兩個位元組輸出每個寬字元字串在輸入字串包含寬字元 \( `NULL`\)，則結果保證相容。  
  
 如果 `wcstombs` 發生寬字元 null 字元 \(L \\ 0 "\) 或前面，或當發生 `count` ，則將它轉換成 8 位元 0 並停止。  因此，在轉換期間，只有當 `wcstombs` 遇到寬字元 Null 字元在 `mbstr` 的多位元組字元字串 NULL 結尾。  如果序列中所指向的 `wcstr` 和 `mbstr` 重疊， `wcstombs` 行為是未定義。  
  
 如果 `mbstr` 引數是 `NULL`， `wcstombs` 在目的資料的位元組傳回所需大小。  
  
 `wcstombs` 會驗證其參數。  如果 `wcstr` 是 `NULL`，或者，如果 `count` 大於`INT_MAX`，這個函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，則函式會將 `errno` 設定為 `EINVAL`並傳回 \-1。  
  
 `wcstombs` 在區域設定相依的動作時使用任何的區域設定。 `_wcstombs_l` 除了使用傳入的區域設定以外其餘相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wcstombs`|\<stdlib.h\>|  
|`_wcstombs_l`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 這個程式說明 `wcstombs` 函式的行為。  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
  **Convert wide\-character string:**  
 **Characters converted: 13**  
 **Multibyte character: Hello, world.**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)