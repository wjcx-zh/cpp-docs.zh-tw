---
title: bsearch_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: bsearch_s
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
f1_keywords: bsearch_s
dev_langs: C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19d60e16ee896049318d8722b59ba124aad67a50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bsearchs"></a>bsearch_s
對已排序陣列執行二進位搜尋。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [bsearch](../../c-runtime-library/reference/bsearch.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
void *bsearch_s(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 搜尋資料的基底指標。  
  
 `num`  
 項目數。  
  
 `width`  
 項目的寬度。  
  
 `compare`  
 比較兩個項目的回呼函式。 第一個引數是 `context` 指標。 第二個引數是搜尋用的 `key` 指標。 第三個引數是要與 `key`比較之陣列項目的指標。  
  
 `context`  
 可以在比較函式中存取的物件指標。  
  
## <a name="return-value"></a>傳回值  
 `bsearch_s` 會傳回 `base` 所指陣列中，`key` 的指標 。 如果找不到 `key` ，則函式會傳回 `NULL`。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。  
  
 若傳遞了無效的參數到此函式，則會叫用無效參數處理常式，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行， `errno` 會設為 `EINVAL` ，且此函式會傳回 `NULL`。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|||||||  
|-|-|-|-|-|-|  
|`key`|`base`|`compare`|`num`|`width`|`errno`|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|!= 0|any|`EINVAL`|  
|any|any|any|any|= 0|`EINVAL`|  
|any|any|`NULL`|an|任何|`EINVAL`|  
  
## <a name="remarks"></a>備註  
 `bsearch_s` 函式會執行 `num` 項目已排序陣列的二進位搜尋，每個的大小為 `width` 個位元組。 `base` 值是要搜尋之陣列的基底指標， `key` 是要搜尋的值。 `compare` 參數是使用者提供的常式指標，這個常式會比較要求的索引鍵與陣列項目，並傳回下列其中一個指定其關聯性的值：  
  
|`compare` 常式傳回的值|描述|  
|-----------------------------------------|-----------------|  
|\< 0|索引鍵小於陣列項目。|  
|0|索引鍵等於陣列項目。|  
|> 0|索引鍵大於陣列項目。|  
  
 `context` 指標適用於搜尋的資料結構是物件的一部分，且比較函式需要存取物件成員的情況。 `compare` 函式可能會將 void 指標轉換成適當的物件類型，並存取該物件的成員。 新增 `context` 參數，會使 `bsearch_s` 更安全，因為可能會使用額外的內容以避免與使用靜態變數相關的重新進入 bug 將資料提供給 `compare` 函式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`bsearch_s`|\<stdlib.h> 和 \<search.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 這個程式會以 [qsort_s](../../c-runtime-library/reference/qsort-s.md)來排序字串陣列，然後使用 bsearch_s 來尋找 cat 這個字。  
  
```  
// crt_bsearch_s.cpp  
// This program uses bsearch_s to search a string array,  
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
#define ENGLISH_LOCALE "English_US.850"  
#endif  
  
#ifdef CODEPAGE_1252  
#define ENGLISH_LOCALE "English_US.1252"  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, char **str1, char **str2)  
{  
    char *s1 = *str1;  
    char *s2 = *str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
int main( void )  
{  
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};  
  
   char *key = "cat";  
   char **result;  
   int i;  
  
   /* Sort using Quicksort algorithm: */  
   qsort_s( arr,  
            sizeof(arr)/sizeof(arr[0]),  
            sizeof( char * ),  
            (int (*)(void*, const void*, const void*))compare,  
            &locale(ENGLISH_LOCALE) );  
  
   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */  
      printf( "%s ", arr[i] );  
  
   /* Find the word "cat" using a binary search algorithm: */  
   result = (char **)bsearch_s( &key,  
                                arr,  
                                sizeof(arr)/sizeof(arr[0]),  
                                sizeof( char * ),  
                                (int (*)(void*, const void*, const void*))compare,  
                                &locale(ENGLISH_LOCALE) );  
   if( result )  
      printf( "\n%s found at %Fp\n", *result, result );  
   else  
      printf( "\nCat not found!\n" );  
}  
```  
  
```Output  
cat cow dog goat horse human pig rat  
cat found at 002F0F04  
```  
  
## <a name="see-also"></a>請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)