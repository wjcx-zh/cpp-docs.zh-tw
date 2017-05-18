---
title: qsort_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- qsort_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- qsort_s
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: e4ba4fcb5acc8c914cf240e5b858a945bd55cc86
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="qsorts"></a>qsort_s
執行快速排序。 這是 [qsort](../../c-runtime-library/reference/qsort.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
void qsort_s(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>參數  
 `base`  
 目標陣列的開頭。  
  
 `num`  
 陣列大小 (以項目計)。  
  
 `width`  
 元素大小 (以位元組為單位)。  
  
 `compare`  
 比較函式。 第一個引數是 `context` 指標。 第二個引數是搜尋用的 `key` 指標。 第三個引數是要與 `key`比較之陣列項目的指標。  
  
 `context`  
 內容的指標，可以是 `compare` 常式需要存取的任何物件。  
  
## <a name="remarks"></a>備註  
 `qsort_s` 函式會實作快速排序演算法，來排序 `num` 項目陣列，每個項目 `width` 個位元組。 `base` 引數是要排序之陣列基底的指標。 `qsort_s` 使用已排序的元素來覆寫這個陣列。 `compare` 引數是使用者所提供之常式的指標，該常式比較兩個陣列元素，然後傳回一個指定其關聯性的值。 `qsort_s` 在排序時會呼叫`compare` 常式一或多次，每次呼叫會將指標傳遞至兩個陣列元素：  
  
```  
compare( context, (void *) & elem1, (void *) & elem2 );  
```  
  
 常式必須比較這些元素，然後傳回下列其中一個值：  
  
|傳回值|描述|  
|------------------|-----------------|  
|< 0|`elem1` 小於 `elem2`|  
|0|`elem1` 相當於 `elem2`|  
|> 0|`elem1` 大於 `elem2`|  
  
 陣列是以比較函式所定義的遞增順序排序。 若要以遞減順序排序陣列，請將比較函式中的「大於」和「小於」意義反轉。  
  
 若傳遞了無效的參數到此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回此函式，並將 `errno` 設為 `EINVAL`。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|key|base|compare|num|寬度|errno|  
|---------|----------|-------------|---------|-----------|-----------|  
|`NULL`|任何|任何|任何|任何|`EINVAL`|  
|任何|`NULL`|任何|!= 0|任何|`EINVAL`|  
|任何|任何|任何|any|<= 0|`EINVAL`|  
|任何|任何|`NULL`|任何|任何|`EINVAL`|  
  
 `qsort_s` 的行為與 `qsort` 相同，但具有 `context` 參數且會設定 `errno`。 藉由傳遞 `context` 參數，比較函式可以使用物件指標，來存取物件功能或其他無法透過元素指標存取的資訊。 新增`context`參數，會使`qsort_s`更安全，因為`context`可用來避免將共用的資訊提供給使用靜態變數所導入的重新進入 bug`compare`函式。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`qsort_s`|\<stdlib.h> 和 \<search.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫︰**所有版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`context`中的參數`qsort_s`函式。 `context` 參數可讓您更輕鬆地執行安全執行緒的排序。 請傳遞每個排序中的不同 `context` 參數，而不是使用必須同步處理以確保執行緒安全性的靜態變數。 在此範例中，會使用地區設定物件作為 `context` 參數。  
  
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
  
## <a name="sample-output"></a>範例輸出  
  
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
  
## <a name="see-also"></a>另請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s](../../c-runtime-library/reference/bsearch-s.md)   
 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)
