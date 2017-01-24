---
title: "wctomb_s、_wctomb_s_l | Microsoft Docs"
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
  - "_wctomb_s_l"
  - "wctomb_s"
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
  - "wctomb_s"
  - "_wctomb_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wctomb_s_l 函式"
  - "字元, 轉換"
  - "字串轉換, 多位元組字元字串"
  - "字串轉換, 寬字元"
  - "wctomb_s 函式"
  - "wctomb_s_l 函式"
  - "寬字元, 轉換"
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wctomb_s、_wctomb_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元至對應的多位元組字元。  這是 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### 參數  
 \[out\] `pRetValue`  
 位元組數目或表示結果的程式碼。  
  
 \[out\] `mbchar`  
 多位元組字元的位址。  
  
 \[in\] `sizeInBytes`  
 緩衝區 `mbchar` 的大小。  
  
 \[in\] `wchar`  
 寬字元。  
  
 \[in\] `locale`  
 要使用的地區設定。  
  
## 傳回值  
 若成功則為零，失敗則為錯誤碼。  
  
 錯誤狀況  
  
|`mbchar`|`sizeInBytes`|傳回值|`pRetValue`|  
|--------------|-------------------|---------|-----------------|  
|`NULL`|\>0|`EINVAL`|未修改|  
|any|\>`INT_MAX`|`EINVAL`|未修改|  
|any|太小|`EINVAL`|未修改|  
  
 如果以上任何一個錯誤情況發生，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行， `wctomb` 會傳回 `EINVAL` 並設定 `errno` 為 `EINVAL`。  
  
## 備註  
 `wctomb_s` 函式轉換成其 `wchar` 引數對應的多位元組字元並將結果儲存在 `mbchar`。  您可以從任何點的函式在所有程式。  
  
 如果 `wctomb_s` 轉換寬字元給多位元組字元，它在寬字元放 \(絕不會是大於 `MB_CUR_MAX`\) 的位元組數至整數所指向的 `pRetValue`。  如果 `wchar` 是寬字元 null 字元 \(L \\ 0 "\)， `wctomb_s` 表示 1. 填入 `pRetValue` 。  如果目標指標 `mbchar` 是空的， `wctomb_s` 在 `pRetValue`將 0。  如果轉換不會在目前地區設定中，將 `wctomb_s` – 1 的 `pRetValue`。  
  
 `wctomb_s` 在區域設定相依的動作時使用目前的區域資訊。 `_wctomb_s_l` 除了使用傳入的區域設定以外其餘相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wctomb_s`|\<stdlib.h\>|  
|`_wctomb_s_l`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 這個程式說明 `wctomb` 函式的行為。  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
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