---
title: "qsort_s | Microsoft Docs"
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
  - "qsort_s"
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
  - "qsort_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "陣列 [C++], 排序"
  - "qsort_s 函式"
  - "快速排序演算法"
  - "排序陣列"
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# qsort_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行快速排序。  這是 [qsort](../../c-runtime-library/reference/qsort.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
void qsort_s(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(void *, const void *, const void *),  
   void * context  
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
 比較函式。  第一個引數是 `context` 指標。  第二個引數是指標進行搜尋的 `key` 。  第三個引數是指向陣列元素，會與 `key`比較。  
  
 `context`  
 對內容的指標，可以是任何物件定期的 `compare` 需要存取。  
  
## 備註  
 `qsort_s` 函式實作快速排序演算法來排序陣列中的 `num` 項目，以每個 `width` 位元組為單位。  `base` 引數是指向將排序陣列的基底。  `qsort_s` 表示要覆寫與排序的項目陣列。  `compare` 引數是指向比較兩個陣列元素和傳回指定其關聯性之值的使用者提供的常式。  在排序過程中，`qsort_s` 會呼叫 `compare` 常式一次或多次，並於每次呼叫傳遞兩個陣列元素的指標。  
  
```  
compare( context, (void *) & elem1, (void *) & elem2 );  
```  
  
 常式必須比較項目會傳回下列其中一個值:  
  
|傳回值|說明|  
|---------|--------|  
|\< 0|`elem1` 小於 `elem2`|  
|0|`elem1` 相當於 `elem2`|  
|\> 0|`elem1` 大於 `elem2`|  
  
 陣列以比較函式所定義的遞增順序排序。  若要以遞減順序排序陣列，反轉在比較函式中關於大於或小於的運算符。  
  
 如果傳給函式無效的參數，無效參數處理常式將被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  如果允許繼續執行，那麼這些函式會返回並將 `errno` 設為 `EINVAL`。  如需詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 錯誤狀況  
  
|Key \- 索引鍵|base|compare|num|width|errno|  
|----------------|----------|-------------|---------|-----------|-----------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|\<\= 0|`EINVAL`|  
|any|any|`NULL`|any|any|`EINVAL`|  
  
 `qsort_s` 具有與 `qsort` 相同的行為，但具有 `context` 參數並設定 `errno`。  您可以透過 `context` 參數，比較函式可以使用物件指標存取物件功能或其他資訊不可以透過項目指標。  因為 `context` 可避免重新 Bug 中引入使用靜態變數進行共用使資訊可以為 `compare` 函式，則 `context` 參數加入使 `qsort_s`更安全。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`qsort_s`|\<stdlib.h\> 和 \<search.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫:** [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 下列範例在 `qsort_s` `` 函式會示範如何使用 `context` 參數。  `context` 參數可讓您更輕鬆地執行安全執行緒排序。  除了使用必須同步確保執行緒安全的靜態變數，請在每個排序的不同的 `context` 參數。  在此範例中，地區設定物件做為 `context` 參數。  
  
```  
// crt_qsort_s.cpp  
// compile with: /EHsc /MT  
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
// so \x00e1 is the German Sharp S in that codepage and \x00a4  
// is the n tilde.  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
#define SPANISH_LOCALE "Spanish_Spain.850"  
#define ENGLISH_LOCALE "English_US.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S and \x001f for the n tilde.  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
#define SPANISH_LOCALE "Spanish_Spain.1252"  
#define ENGLISH_LOCALE "English_US.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making sort_array vulnerable to thread  
// conflicts.  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char s1[256];  
    char s2[256];  
    strcpy_s(s1, 256, *(char**)str1);  
    strcpy_s(s2, 256, *(char**)str2);  
    _strlwr_s( s1, sizeof(s1) );  
    _strlwr_s( s2, sizeof(s2) );  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(s1,   
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);  
  
}  
  
void sort_array(char *array[], int num, locale &loc)  
{  
    qsort_s(array, num, sizeof(char*), compare, &loc);  
}  
  
void print_array(char *a[], int c)  
{  
   for (int i = 0; i < c; i++)  
     printf("%s ", a[i]);  
   printf("\n");  
  
}  
  
void sort_german(void * Dummy)  
{  
   sort_array(array1, 6, locale(GERMAN_LOCALE));  
}  
  
void sort_spanish(void * Dummy)  
{     
   sort_array(array2, 3, locale(SPANISH_LOCALE));       
}  
  
void sort_english(void * Dummy)  
{     
   sort_array(array3, 3, locale(ENGLISH_LOCALE));     
}  
  
int main( )  
{  
  
   int i;  
   HANDLE threads[3];  
  
   printf("Unsorted input:\n");  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
   // Create several threads that perform sorts in different  
   // languages at the same time.   
  
   threads[0] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_german , 0, NULL));  
   threads[1] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_spanish, 0, NULL));  
   threads[2] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_english, 0, NULL));  
  
   for (i = 0; i < 3; i++)  
   {  
      if (threads[i] == reinterpret_cast<HANDLE>(-1))  
      {  
         printf("Error creating threads.\n");  
         exit(1);  
      }  
   }  
  
   // Wait until all threads have terminated.  
   WaitForMultipleObjects(3, threads, true, INFINITE);  
  
   printf("Sorted output: \n");  
  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
}  
```  
  
## 範例輸出  
  
```  
Unsorted input:  
weiß weis annehmen weizen Zeit weit   
Español España espantado   
table tableux tablet   
Sorted output:   
annehmen weiß weis weit weizen Zeit   
España Español espantado   
table tablet tableux  
```  
  
## .NET Framework 對等用法  
 <xref:System.Collections.ArrayList.Sort%2A>  
  
## 請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)