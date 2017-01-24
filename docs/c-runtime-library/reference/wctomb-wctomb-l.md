---
title: "wctomb、_wctomb_l | Microsoft Docs"
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
  - "_wctomb_l"
  - "wctomb"
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
  - "wctomb"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wctomb_l 函式"
  - "字元, 轉換"
  - "字串轉換, 多位元組字元字串"
  - "字串轉換, 寬字元"
  - "wctomb 函式"
  - "wctomb_l 函式"
  - "寬字元, 轉換"
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wctomb、_wctomb_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元至對應的多位元組字元  這些函式已有更安全的版本可用，請參閱 [wctomb\_s、\_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)。  
  
## 語法  
  
```  
int wctomb(  
   char *mbchar,  
   wchar_t wchar   
);  
int _wctomb_l(  
   char *mbchar,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `mbchar`  
 多位元組字元的位址。  
  
 `wchar`  
 寬字元。  
  
## 傳回值  
 如果 `wctomb` 將寬字元轉換為多位元組字元，它會以寬字元傳回 \(絕不大於 `MB_CUR_MAX`\) 的位元組數目。  如果 `wchar` 是寬字元的 null 字元 \(L'\\0'\)\)，則`wctomb` 會傳回 1。  如果目標指標 `mbchar` 是NULL，則 `wctomb` 會傳回 0。  如果轉換在目前地區設定中不可行， `wctomb` 會傳回– 1 並將 `errno` 設定為 `EILSEQ`。  
  
## 備註  
 `wctomb` 函式轉換成其 `wchar` 引數對應的多位元組字元並將結果儲存在 `mbchar`。  您可以從任何點的函式在所有程式。  `wctomb` 在區域設定相依的動作時使用目前的區域設定，`_wctomb_l` 除了使用傳入的區域設定以外與`wctomb` 是相同的。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 `wctomb` 會驗證其參數。  如果 `mbchar` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，`errno` 會被設定為 `EINVAL` 且函式會傳回\-1 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wctomb`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 這個程式說明 wctomb函式的行為。  
  
```  
// crt_wctomb.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int i;  
   wchar_t wc = L'a';  
   char *pmb = (char *)malloc( MB_CUR_MAX );  
  
   printf( "Convert a wide character:\n" );  
   i = wctomb( pmb, wc ); // C4996  
   // Note: wctomb is deprecated; consider using wctomb_s  
   printf( "   Characters converted: %u\n", i );  
   printf( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
  **轉換寬字元:**  
 **要轉換的字元:1**  
 **多位元組字元：a**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)