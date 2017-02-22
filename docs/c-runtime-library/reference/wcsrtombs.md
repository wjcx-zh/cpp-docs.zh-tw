---
title: "wcsrtombs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcsrtombs"
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
  - "wcsrtombs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wcsrtombs 函式"
  - "字串轉換, 寬字元"
  - "寬字元, 字串"
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# wcsrtombs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元字串對其多位元組字串表示。  這些函式已有更安全的版本可用，請參閱 [wcsrtombs\_s](../../c-runtime-library/reference/wcsrtombs-s.md)。  
  
## 語法  
  
```  
size_t wcsrtombs(  
   char *mbstr,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcsrtombs(  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### 參數  
 \[out\] `mbstr`  
 產生的轉換的多位元組字元字串的位址的位置。  
  
 \[in\] `wcstr`  
 要轉換的寬字元字串位置的間接點。  
  
 \[in\] `count`  
 要轉換的字元數目。  
  
 \[in\] `mbstate`  
 `mbstate_t` 轉換狀態物件的指標。  
  
## 傳回值  
 傳回成功轉換的位元組數目，不含結尾的 NULL 位元組 \(如果有的話\)，否則當錯誤發生時，傳回\-1。  
  
## 備註  
 `wcsrtombs` 函式轉換寬字元字串開始，包含在 `mbstate`中指定的轉換狀態，從值間接滿足屬性加入至 `wcstr`，到 `mbstr`的位址。  轉換會繼續每個字元直到:寬字元為空之後，當非對應的字元發生，或是在下一個字元會超出 `count`中包含的限制。  如果 `wcsrtombs` 發生寬字元 null 字元 \(L \\ 0 "\) 或前面，或當發生 `count` ，則將它轉換成 8 位元 0 並停止。  
  
 因此，在轉換期間，只有當 `wcsrtombs` 遇到寬字元 Null 字元在 `mbstr` 的多位元組字元字串 NULL 結尾。  如果序列中所指向的 `wcstr` 和 `mbstr` 重疊， `wcsrtombs` 行為是未定義。  `wcsrtombs` 受目前地區設定的 LC\_TYPE 分類的影響。  
  
 `wcsrtombs` 函式與 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) 不同於其重新開始的能力。  轉換狀態儲存於 `mbstate` 讓後續呼叫的相同或其他可重新啟動的函式能夠使用。  當混合使用可重新開始和不可重新開始的函式時，結果會是未定義的。例如，如果後續呼叫 `wcsrtombs` 而不是 `wcstombs`，應用程式可能會使用 `wcsrlen` ，而不是 `wcsnlen`。  
  
 如果 `mbstr` 引數是 `NULL`， `wcsrtombs` 在目的資料的位元組傳回所需大小。  如果 `mbstate` 是 null，則會使用內部 `mbstate_t` 轉換狀態。  如果字元順序 `wchar` 沒有對應的多位元組字元表示，則傳回 \-1，而且 `errno` 設定為 `EILSEQ`。  
  
 在 C\+\+ 中，這個函式會叫用的範本多載越新，保護這個對應的函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 例外狀況  
 `wcsrtombs` 函式是多執行緒安全，只要在目前執行緒的函式不呼叫 `setlocale` ，當函式執行時， `mbstate` 是不會是空的。  
  
## 範例  
  
```  
// crt_wcsrtombs.cpp  
// compile with: /W3  
// This code example converts a wide  
// character string into a multibyte  
// character string.  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
int main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    countConverted = wcsrtombs(mbString, &wcsIndirectString,  
                               MB_BUFFER_SIZE, &mbstate); // C4996  
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s  
    if (errno == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfuly converted.\n" );  
    }  
}  
```  
  
  **字串成功地轉換。**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wcsrtombs`|\<wchar.h\>|  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)