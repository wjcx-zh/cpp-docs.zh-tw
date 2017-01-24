---
title: "qsort | Microsoft Docs"
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
  - "qsort"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "qsort"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "qsort 函式"
  - "快速排序演算法"
  - "排序陣列"
  - "陣列 [CRT]，排序"
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# qsort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行快速排序。  這些函式已有更安全的版本可用，請參閱 [qsort\_s](../../c-runtime-library/reference/qsort-s.md)。  
  
## 語法  
  
```  
void qsort(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(const void *, const void *)   
);  
```  
  
#### 參數  
 `base`  
 目標陣列的開頭。  
  
 `num`  
 陣列大小（以元素為單位）。  
  
 `width`  
 項目大小 \(以位元組為單位\)。  
  
 `compare`  
 比較的兩個陣列元素和傳回值指定其關聯性的使用者提供的常式的指標。  
  
## 備註  
 `qsort` 函式實作快速排序演算法來排序陣列中的 `num` 項目，以每個 `width` 位元組為單位。  `base` 引數是指向將排序陣列的基底。  `qsort` 使用已排序項目覆寫此陣列。  
  
 在排序過程中，`qsort` 會呼叫 `compare` 常式一次或多次，並於每次呼叫傳遞兩個陣列元素的指標。  
  
```  
compare( (void *) & elem1, (void *) & elem2 );  
```  
  
 常式比較項目並傳回下列其中一個值。  
  
|比較函式的傳回值|說明|  
|--------------|--------|  
|\< 0|`elem1` 小於 `elem2`|  
|0|`elem1` 相當於 `elem2`|  
|\> 0|`elem1` 大於 `elem2`|  
  
 陣列以比較函式所定義的遞增順序排序。  若要以遞減順序排序陣列，反轉在比較函式中關於大於或小於的運算符。  
  
 這個函式會驗證它的參數。  如果 `compare` 或 `num` 是 `NULL`，或是如果 `base` 為 `NULL` 且\*`num` 為非零，或是 `width` 小於零，將會叫用無效的參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則函式會回傳並將 `errno` 設定為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`qsort`|\<stdlib.h\> 和 \<search.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_qsort.c  
// arguments: every good boy deserves favor  
  
/* This program reads the command-line  
 * parameters and uses qsort to sort them. It  
 * then displays the sorted arguments.  
 */  
  
#include <stdlib.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main( int argc, char **argv )  
{  
   int i;  
   /* Eliminate argv[0] from sort: */  
   argv++;  
   argc--;  
  
   /* Sort remaining args using Quicksort algorithm: */  
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );  
  
   /* Output sorted list: */  
   for( i = 0; i < argc; ++i )  
      printf( " %s", argv[i] );  
   printf( "\n" );  
}  
  
int compare( const void *arg1, const void *arg2 )  
{  
   /* Compare all of both strings: */  
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );  
}  
```  
  
  **boy deserves every favor good**   
## .NET Framework 對等用法  
 [System::Collections::ArrayList::Sort](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)  
  
## 請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)