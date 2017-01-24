---
title: "wcstombs_s、_wcstombs_s_l | Microsoft Docs"
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
  - "_wcstombs_s_l"
  - "wcstombs_s"
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
  - "wcstombs_s"
  - "_wcstombs_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcstombs_s 函式"
  - "字串轉換, 寬字元"
  - "寬字元轉換"
  - "_wcstombs_s_l 函式"
  - "wcstombs_s_l 函式"
  - "轉換的字元"
  - "字串轉換，多位元組字元字串"
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcstombs_s、_wcstombs_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一系列寬字元轉換成對應的多位元組字元序列。 版本 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count   
);  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 \[輸出\] `pReturnValue`  
 已轉換的字元數。  
  
 \[輸出\] `mbstr`  
 產生的已轉換的多位元組字元字串的緩衝區位址。  
  
 \[\] in`sizeInBytes`  
 以位元組為單位的大小 `mbstr` 緩衝區。  
  
 \[in\] `wcstr`  
 要轉換的寬字元字串的指標。  
  
 \[in\] `count`  
 要儲存的位元組數目上限 `mbstr` 緩衝區，不包括結束的 null 字元或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in\] `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果成功，失敗的錯誤代碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|----------|------------------|  
|`mbstr` 是 `NULL` 和 `sizeInBytes` \> 0|`EINVAL`|  
|`wcstr` 是 `NULL`|`EINVAL`|  
|目的緩衝區太小而無法包含已轉換的字串 \(除非 `count` 是 `_TRUNCATE`; 請參閱下面的備註\)|`ERANGE`|  
  
 如果上述任一種情況發生時，所述，會叫用無效參數例外狀況 [參數驗證](../../c-runtime-library/parameter-validation.md) 。 如果允許繼續執行，此函式會傳回錯誤碼，並將 `errno` 設為如表中所示。  
  
## 備註  
 `wcstombs_s` 函式所指向的寬字元字串，轉換為 `wcstr` 到儲存在緩衝區所指向的多位元組字元 `mbstr`。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：  
  
-   遇到 null 寬字元  
  
-   遇到無法轉換寬字元  
  
-   儲存在位元組數目 `mbstr` 緩衝等於 `count`。  
  
 目的地字串一律是以 null 結束 （即使發生錯誤）。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md), ，然後 `wcstombs_s` 的字串會盡量轉換符合目的緩衝區，同時仍留出空間給 null 結束字元。  
  
 如果 `wcstombs_s` 成功轉換來源字串中，以位元組為單位的已轉換的字串，包括 null 結束字元，置入大小 `*``pReturnValue` \(提供 `pReturnValue` 不 `NULL`\)。 發生這種情況即使 `mbstr` 引數是 `NULL` ，並提供方法來判斷所需的緩衝區大小。 請注意，如果 `mbstr` 是 `NULL`, ，`count` 會被忽略。  
  
 如果 `wcstombs_s` 遇到多位元組字元，不能轉換寬字元放在 0 `*``pReturnValue`, ，目的端緩衝區設定為空字串，設定 `errno` 至 `EILSEQ`, ，並傳回 `EILSEQ`。  
  
 如果 `wcstr` 和 `mbstr` 所指向的序列重疊，`wcstombs_s` 的行為不明。  
  
> [!IMPORTANT]
>  請確認 `wcstr` 和 `mbstr` 沒有重疊，而且 `count` 正確反映要轉換的寬字元數目。  
  
 `wcstombs_s` 使用目前的地區設定進行任何地區設定相關的行為。 `_wcstombs_s_l` 等同於 `wcstombs` 但會改用傳遞的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wcstombs_s`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 此程式說明的行為 `wcstombs_s` 函式。  
  
```  
// crt_wcstombs_s.c  
// This example converts a wide character  
// string to a multibyte character string.  
#include <stdio.h>  
#include <stdlib.h>  
#include <assert.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t   i;  
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t*pWCBuffer = L"Hello, world.";  
  
    printf( "Convert wide-character string:\n" );  
  
    // Conversion  
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,   
               pWCBuffer, (size_t)BUFFER_SIZE );  
  
    // Output  
    printf("   Characters converted: %u\n", i);  
    printf("    Multibyte character: %s\n\n",  
     pMBBuffer );  
  
    // Free multibyte character buffer  
    if (pMBBuffer)  
    {  
    free(pMBBuffer);  
    }  
}  
```  
  
```Output  
寬字元字串轉換︰ 轉換的字元︰ 14 的多位元組字元︰ Hello，world。  
```  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb\_s、\_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)