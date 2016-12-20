---
title: "_lfind_s | Microsoft Docs"
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
  - "_lfind_s"
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
  - "lfind_s"
  - "_lfind_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lfind_s 函式"
  - "陣列 [CRT], 搜尋"
  - "索引鍵, 在陣列中尋找"
  - "lfind_s 函式"
  - "線性搜尋"
  - "搜尋, 線性"
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lfind_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行指定之索引鍵的線性搜尋。  這是 [\_lfind](../../c-runtime-library/reference/lfind.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
void *_lfind_s(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### 參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 指向要搜尋資料基底的指標。  
  
 `num`  
 陣列項目的數目。  
  
 `size`  
 陣列元素的大小 \(以位元組為單位\)。  
  
 `compare`  
 要比較常式的指標。  第一個參數是 `context` 指標。  第二個參數是指向搜尋的索引指標。  第三個參數是指向與索引鍵比較的陣列元素。  
  
 `context`  
 在比較函式可能被存取之物件的指標。  
  
## 傳回值  
 如果找到索引鍵，則 `_lfind_s` 會傳回與 `key`相符的`base` 陣列的項目的指標 。  如果索引鍵沒有找到，`_lfind_s` 就會傳回 `NULL`。  
  
 如果傳給函式無效的參數，無效參數處理常式將被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `NULL`。  
  
### 錯誤狀況  
  
|Key \- 索引鍵|base|compare|num|size|errno|  
|----------------|----------|-------------|---------|----------|-----------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|零|`EINVAL`|  
|any|any|`NULL`|一|any|`EINVAL`|  
  
## 備註  
 `_lfind_s` 函式在陣列中的 `num` 項目用 `key` 執行線性搜尋，每 `width` 位元組。  不同於 `bsearch_s`， `_lfind_s` 不需要先排序陣列。  `base` 引數是指向將搜尋陣列的基底。  `compare` 引數是指向比較兩個陣列元素和傳回指定其關聯性之值的使用者提供的常式。  在搜尋期間，`_lfind_s` 會呼叫 `compare` 常式一次或多次，每個呼叫傳遞 `context` 指標和兩個陣列元素指標。  `compare` 常式必須比較項目且傳回非零 \(表示項目是不同的\) 或 0 \(表示項目中相同\)。  
  
 `_lfind_s` 與 `_lfind` 類似，除了比較函式 `context` 指標與引數的加法以及函式的參數清單。  如果被搜尋的資料結構為物件的一部分，`context` 指標會很有用，而且 `compare` 函式需要存取物件的成員。  `compare` 函式可以將 null 指標轉型為適當的物件型別，然後存取該物件的成員。  因為其他內容可以用來避免關於使用靜態變數讓 `compare` 函式可以存取資料的可重入錯誤 ，則 `context` 參數加入使 `_lfind_s` 更安全。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_lfind_s`|\<search.h\>|  
  
 如需詳細資訊，請參閱介紹中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_lfind_s.cpp  
// This program uses _lfind_s to search a string array,  
// passing a locale as the context.  
// compile with: /EHsc  
#include <stdlib.h>  
#include <stdio.h>  
#include <search.h>  
#include <process.h>  
#include <locale.h>  
#include <locale>  
#include <windows.h>  
using namespace std;  
  
// The sort order is dependent on the code page.  Use 'chcp' at the  
// command line to change the codepage.  When executing this application,  
// the command prompt codepage must match the codepage used here:  
  
#define CODEPAGE_850  
  
#ifdef CODEPAGE_850  
// Codepage 850 is the OEM codepage used by the command line,  
// so \x00e1 is the German Sharp S  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char *s1 = *(char**)str1;  
    char *s2 = *(char**)str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
void find_it( char *key, char *array[], unsigned int num, locale &loc )  
{  
   char **result = (char **)_lfind_s( &key, array,   
                      &num, sizeof(char *), compare, &loc );  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "%s not found\n", key );  
}  
  
int main( )  
{  
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );  
}  
```  
  
  **weit found**   
## .NET Framework 對等用法  
 <xref:System.Collections.ArrayList.Contains%2A>  
  
## 請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort\_s](../../c-runtime-library/reference/qsort-s.md)   
 [\_lfind](../../c-runtime-library/reference/lfind.md)