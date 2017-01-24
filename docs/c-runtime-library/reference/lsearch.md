---
title: "_lsearch | Microsoft Docs"
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
  - "_lsearch"
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
  - "_lsearch"
  - "lsearch"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lsearch 函式"
  - "陣列 [CRT], 搜尋"
  - "索引鍵, 在陣列中尋找"
  - "線性搜尋"
  - "lsearch 函式"
  - "搜尋, 線性"
  - "值, 搜尋"
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lsearch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行值的線性搜尋;如果找不到，加入至清單結尾。  這個函式更安全的版本可用;請參閱 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)。  
  
## 語法  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### 參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 要搜尋的基底陣列的指標。  
  
 `num`  
 項目數。  
  
 `width`  
 每個陣列元素的寬度。  
  
 `compare`  
 要比較常式的指標。  第一個參數是指向搜尋的索引指標。  第二個參數是指向與索引鍵比較的陣列元素。  
  
## 傳回值  
 如果找到索引鍵，則 `_lsearch` 會傳回與 `key`相符的`base` 陣列的項目的指標 。  如果找不到關鍵， `_lsearch` 將指標傳回新加入的項目在陣列結尾。  
  
## 備註  
 `_lsearch` 函式在陣列中的 `num` 項目用 `key` 執行線性搜尋，每 `width` 位元組。  不同於 `bsearch`， `_lsearch` 不需要先排序陣列。  如果找不到 `key` ，則 `_lsearch` 將它加入至陣列結尾並加入 `num`。  
  
 `compare` 引數是指向比較兩個陣列元素和傳回指定其關聯性之值的使用者提供的常式。  在搜尋過程中，`_lsearch` 會呼叫 `compare` 常式一次或多次，並於每次呼叫傳遞兩個陣列元素的指標。  `compare` 必須比較項目且傳回非零 \(表示項目是不同的\) 或 0 \(表示項目中相同\)。  
  
 這個函式會驗證它的參數。  如果 `compare` 或 `key` 是 `num`，或是如果 `NULL` 為 `base` 且\*`num` 為非零，或是 `width` 小於零，將會叫用無效的參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `NULL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_lsearch`|\<search.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_lsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main(void)  
{  
   char * wordlist[4] = { "hello", "thanks", "bye" };  
                            // leave room to grow...  
   int n = 3;  
   char **result;  
   char *key = "extra";  
   int i;  
  
   printf( "wordlist before _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
  
   result = (char **)_lsearch( &key, wordlist,   
                      &n, sizeof(char *), compare );  
  
   printf( "wordlist after _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
}  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
```  
  
  **在 \_lsearch 前的單一字表:你好 謝謝 再見**  
**在 \_lsearch 之後的單一字表:你好 感謝 再見 重複。**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lfind](../../c-runtime-library/reference/lfind.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)