---
title: "_TRUNCATE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_TRUNCATE"
  - "TRUNCATE"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_TRUNCATE 常數"
  - "TRUNCATE 常數"
ms.assetid: ad093dbf-1aa5-4bd2-9268-efc68afd8434
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _TRUNCATE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定字串的行為。  
  
## 語法  
  
```  
#include <stdlib.h>  
```  
  
## 備註  
 `_TRUNCATE` 可攔截的行為，則會當做 `count` 參數傳遞給這些函式:  
  
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)  
  
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)  
  
 [mbstowcs\_s、\_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)  
  
 [mbsrtowcs\_s](../c-runtime-library/reference/mbsrtowcs-s.md)  
  
 [wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)  
  
 [wcsrtombs\_s](../c-runtime-library/reference/wcsrtombs-s.md)  
  
 [\_snprintf\_s、\_snprintf\_s\_l、\_snwprintf\_s、\_snwprintf\_s\_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)  
  
 [vsnprintf\_s、\_vsnprintf\_s、\_vsnprintf\_s\_l、\_vsnwprintf\_s、\_vsnwprintf\_s\_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)  
  
 如果目的緩衝區太小而無法容納整個字串，這些函式一般行為是將其視為錯誤情況 \(請參閱 [參數驗證](../c-runtime-library/parameter-validation.md)\)。  不過，如果字串截斷傳遞 `_TRUNCATE`啟用，這些函式會複製相同只許多像字串符合，將目的端緩衝區空間結束，並成功傳回。  
  
 字串截斷變更受影響的函式的傳回值。  如果攔截未發生，下列函式會傳回 0，如果攔截發生，則為 `STRUNCATE` :  
  
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)  
  
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)  
  
 [wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)  
  
 [mbstowcs\_s、\_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)  
  
 如果攔截未發生，下列函式傳回複製的數字字元，如果發生截斷 \(符合原始 snprintf 函式的行為\)則為 \-1:  
  
 [\_snprintf\_s、\_snprintf\_s\_l、\_snwprintf\_s、\_snwprintf\_s\_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)  
  
 [vsnprintf\_s、\_vsnprintf\_s、\_vsnprintf\_s\_l、\_vsnwprintf\_s、\_vsnwprintf\_s\_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)  
  
## 範例  
  
```  
// crt_truncate.c  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
   char src[] = "1234567890";  
   char dst[5];  
   errno_t err = strncpy_s(dst, _countof(dst), src, _TRUNCATE);  
   if ( err == STRUNCATE )  
      printf( "truncation occurred!\n" );  
   printf( "'%s'\n", dst );  
}  
```  
  
  **攔截發生了\!**  
**'1234'**   
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)