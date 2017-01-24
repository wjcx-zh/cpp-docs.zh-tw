---
title: "wctype | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wctype"
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
apitype: "DLLExport"
f1_keywords: 
  - "wctype"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wctype 函式"
  - "寬字元"
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wctype
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷寬字元程式碼的排序規則。  
  
## 語法  
  
```  
wctype_t wctype(  
   const char * property   
);  
```  
  
#### 參數  
 `property`  
 String 屬性  
  
## 傳回值  
 如果目前地區設定的 `LC_CTYPE` 分類不定義名稱符合 `property`屬性字串的排序規則，函式會傳回零。  否則，會傳回非零值適合做為第二個引數的後續對 [towctrans](../../c-runtime-library/reference/towctrans.md)。  
  
## 備註  
 函式會判斷寬字元程式碼的排序規則。  下列在所有地區設定的呼叫有相同的行為 \(但實作可以定義其他分類規則是在「C」地區設定\)：  
  
|功能|相同|  
|--------|--------|  
|`iswalnum(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alnum" ) )`|  
|`iswalpha(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alpha" ) )`|  
|`iswcntrl(`  `c`  `)`|`iswctype(`  `c` `, wctype( "cntrl" ) )`|  
|`iswdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "digit" ) )`|  
|`iswgraph(`  `c`  `)`|`iswctype(`  `c` `, wctype( "graph" ) )`|  
|`iswlower(`  `c`  `)`|`iswctype(`  `c` `, wctype( "lower" ) )`|  
|`iswprint(`  `c`  `)`|`iswctype(`  `c` `, wctype( "print" ) )`|  
|`iswpunct(`  `c`  `)`|`iswctype(`  `c` `, wctype( "punct" ) )`|  
|`iswspace(`  `c`  `)`|`iswctype(`  `c` `, wctype( "space" ) )`|  
|`iswupper(`  `c`  `)`|`iswctype(`  `c` `, wctype( "upper" ) )`|  
|`iswxdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "xdigit" ) )`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`wctype`|\<wctype.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)