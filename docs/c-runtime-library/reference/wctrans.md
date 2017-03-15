---
title: "wctrans | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wctrans"
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
  - "wctrans"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字元碼, wctrans"
  - "字元, 程式碼"
  - "字元, 轉換"
  - "wctrans 函式"
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# wctrans
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

決定從一組字元碼到另一個的對應。  
  
## 語法  
  
```  
wctrans_t wctrans(  
   const char *property   
);  
```  
  
#### 參數  
 `property`  
 指定其中一個有效的轉換字串。  
  
## 傳回值  
 如果目前地區設定的 `LC_CTYPE` 分類不定義名稱符合 `property`屬性字串的排序規則，函式會傳回零。  否則，會傳回適合做為後續對 [towctrans](../../c-runtime-library/reference/towctrans.md)呼叫的第二個引數的非零值。  
  
## 備註  
 這個函式決定從一組字元碼到另一個的對應。  
  
 下列呼叫的配對在所有地區設定中有相同的行為，不過，在「C」地區設定定義其他對應是可能的：  
  
|功能|相同|  
|--------|--------|  
|`tolower(`  `c`  `)`|`towctrans(`  `c` `, wctrans("towlower" ) )`|  
|`towupper(`  `c`  `)`|`towctrans(`  `c` `, wctrans( "toupper" ) )`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wctrans`|\<wctype.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_wctrans.cpp  
// compile with: /EHsc  
// This example determines a mapping from one set of character  
// codes to another.   
  
#include <wchar.h>  
#include <wctype.h>  
#include <stdio.h>  
#include <iostream>  
  
int main()   
{  
    wint_t c = 'a';  
    printf_s("%d\n",c);  
  
    wctrans_t i = wctrans("toupper");  
    printf_s("%d\n",i);  
  
    wctrans_t ii = wctrans("towlower");  
    printf_s("%d\n",ii);  
  
    wchar_t wc = towctrans(c, i);  
    printf_s("%d\n",wc);  
}  
```  
  
  **97**  
**1**  
**0**  
**65**   
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)