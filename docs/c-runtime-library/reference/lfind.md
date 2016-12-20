---
title: "_lfind | Microsoft Docs"
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
  - "_lfind"
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
  - "lfind"
  - "_lfind"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lfind 函式"
  - "陣列 [CRT], 搜尋"
  - "在陣列中尋找關鍵字"
  - "lfind 函式"
  - "線性搜尋"
  - "搜尋, 線性"
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lfind
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行指定之索引鍵的線性搜尋。  這些函式已有更安全的版本可用，請參閱 [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md)。  
  
## 語法  
  
```  
void *_lfind(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)  
);  
```  
  
#### 參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 指向要搜尋資料基底的指標。  
  
 `num`  
 陣列項目的數目。  
  
 `width`  
 陣列項目的寬度。  
  
 `compare`  
 要比較常式的指標。  第一個參數是指向搜尋的索引指標。  第二個參數是指向與索引鍵比較的陣列元素。  
  
## 傳回值  
 如果找到索引鍵，則 `_lfind` 會傳回與 `key`相符的`base` 陣列的項目的指標 。  如果索引鍵沒有找到，`_lfind` 就會傳回 `NULL`。  
  
## 備註  
 `_lfind` 函式在陣列中的 `num` 項目用 `key` 執行線性搜尋，每 `width` 位元組。  不同於 `bsearch`， `_lfind` 不需要先排序陣列。  `base` 引數是指向將搜尋陣列的基底。  `compare` 引數是指向比較兩個陣列元素和傳回指定其關聯性之值的使用者提供的常式。  在搜尋過程中，`_lfind` 會呼叫 `compare` 常式一次或多次，並於每次呼叫傳遞兩個陣列元素的指標。  `compare` 常式必須比較項目且傳回非零 \(表示項目是不同的\) 或 0 \(表示項目中相同\)。  
  
 這個函式會驗證它的參數。  如果 `compare` 或 `key` 是 `num`，或是如果 `NULL` 為 `base` 且\*`num` 為非零，或是 `width` 小於零，將會叫用無效的參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `NULL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_lfind`|\<search.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_lfind.c  
// This program uses _lfind to search a string array  
// for an occurrence of "hello".  
  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
  
int main( )  
{  
   char *arr[] = {"Hi", "Hello", "Bye"};  
   int n = sizeof(arr) / sizeof(char*);  
   char **result;  
   char *key = "hello";  
  
   result = (char **)_lfind( &key, arr,   
                      &n, sizeof(char *), compare );  
  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "hello not found!\n" );  
}  
```  
  
  **Hello 找到**   
## .NET Framework 對等用法  
 [System::Collections::ArrayList::Contains](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.contains.aspx)  
  
## 請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)