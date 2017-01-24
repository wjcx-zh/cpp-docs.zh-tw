---
title: "wcsrtombs_s | Microsoft Docs"
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
  - "wcsrtombs_s"
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
  - "wcsrtombs_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字串轉換, 寬字元"
  - "wcsrtombs_s 函式"
  - "寬字元, 字串"
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
caps.latest.revision: 27
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcsrtombs_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元字串對其多位元組字串表示。  這是 [wcsrtombs](../../c-runtime-library/reference/wcsrtombs.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### 參數  
 \[out\] `pReturnValue`  
 要轉換的字元數。  
  
 \[out\] `mbstr`  
 產生的轉換多位元組字元字串的緩衝區位址。  
  
 \[out\] `sizeInBytes`  
 `mbstr` 緩衝區的大小 \(以位元組為單位\)。  
  
 \[in\] `wcstr`  
 要轉換的寬字元字串的點。  
  
 \[in\] `count`  
 在 `mbstr` 緩衝區中儲存的最大位元組數目或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in\] `mbstate`  
 `mbstate_t` 轉換狀態物件的指標。  
  
## 傳回值  
 若成功則為零，失敗則為錯誤碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|----------|------------------|  
|`mbstr` 為 `NULL` 而 `sizeInBytes`\> 為 0|`EINVAL`|  
|`wcstr` 為 `NULL`|`EINVAL`|  
|目的端緩衝區太小無法包含已轉換字串\(除非 `count` 是 `_TRUNCATE` 請參閱 \< 備註 \>\)|`ERANGE`|  
  
 如果其中一個錯誤情況發生，無效的參數叫用例外狀況，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續執行，函式會傳回錯誤碼並如表格中所示設定 `errno` 。  
  
## 備註  
 `wcsrtombs_s` 函式轉換寬字元字串指向 `wcstr` 輸入緩衝區中的多位元組字元所指向的 `mbstr`，使用 `mbstate`中所包含的轉換狀態。  每個字元的轉換會繼續，直到下列其中一個條件符合：  
  
-   遇到空寬字元  
  
-   遇到無法轉換的寬字元  
  
-   在 `mbstr` 緩衝區中位元組數目等於 `count`。  
  
 目的資料永遠以 null 結尾 \(即使在錯誤的情況下\)。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md)，則 `wcsrtombs_s` 盡量轉換能放入目的緩衝區的字串，同時保留 null 結束字元的空間。  
  
 如果 `wcsrtombs_s` 轉換成功來源字串，它在已轉換字串的位元組的大小，包括 null 結束字元，輸入 `*``pReturnValue` \(提供的 `pReturnValue` 不是 `NULL`\)。  發生這種情況，即使 `mbstr` 引數為 `NULL` 並提供方法來判斷所需的緩衝區大小。  請注意，如果 `mbstr` 是 `NULL`，會忽略 `count` 。  
  
 如果`wcsrtombs_s` 遇到無法轉換到多位元組字元的寬字元，它在 `*``pReturnValue`放\-1，將目的緩衝區初始化為空字串，將 `errno` 設為 `EILSEQ`，並傳回 `EILSEQ`。  
  
 如果序列中所指向的 `wcstr` 和 `mbstr` 重疊， `wcsrtombs_s` 行為是未定義。  `wcsrtombs_s` 受目前地區設定的 LC\_TYPE 分類的影響。  
  
> [!IMPORTANT]
>  確認 `wcstr` 和 `mbstr` 不重疊，而 `count` ，正確反映轉換寬字元的數目。  
  
 `wcsrtombs_s` 函式與 [wcstombs\_s、\_wcstombs\_s\_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md) 不同於其重新開始的能力。  轉換狀態儲存於 `mbstate` 讓後續呼叫的相同或其他可重新啟動的函式能夠使用。  當混合使用可重新開始和不可重新開始的函式時，結果會是未定義的。  例如，如果後續呼叫 `wcsrtombs_s` 而不是 `wcstombs_s.`，應用程式可能會使用 `wcsrlen` ，而不是 `wcslen`  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 例外狀況  
 `wcsrtombs_s` 函式是多執行緒安全，只要在目前執行緒的函式不呼叫 `setlocale` ，當函式執行時， `mbstate` 是空的。  
  
## 範例  
  
```  
// crt_wcsrtombs_s.cpp  
//   
// This code example converts a wide  
// character string into a multibyte  
// character string.  
//  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
void main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    errno_t         err;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,  
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);  
    if (err == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfully converted.\n" );  
    }  
}  
```  
  
  **字串成功地轉換。**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wcsrtombs_s`|\<wchar.h\>|  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)