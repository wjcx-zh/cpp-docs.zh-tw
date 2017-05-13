---
title: bsearch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- bsearch
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
- bsearch
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 431bb94e27397f8a0242c45db83e00250e5c82f3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="bsearch"></a>bsearch
對已排序陣列執行二進位搜尋。 這個函式已有更安全的版本可用；請參閱 [bsearch_s](../../c-runtime-library/reference/bsearch-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void *bsearch(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) (const void *key, const void *datum)   
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
 比較兩個項目的回呼函式。 第一個是搜尋索引鍵的指標，第二個是要與索引鍵比較的陣列項目的指標。  
  
## <a name="return-value"></a>傳回值  
 `bsearch` 會傳回 `base` 所指陣列中，`key` 的指標 。 如果找不到 `key` ，則函式會傳回 `NULL`。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。  
  
## <a name="remarks"></a>備註  
 `bsearch` 函式會執行 `num` 項目已排序陣列的二進位搜尋，每個的大小為 `width` 個位元組。 `base` 值是要搜尋之陣列的基底指標， `key` 是要搜尋的值。 `compare` 參數是使用者提供的常式指標，這個常式會比較要求的索引鍵與陣列項目，並傳回下列其中一個指定其關聯性的值：  
  
|`compare` 常式傳回的值|描述|  
|-----------------------------------------|-----------------|  
|\< 0|索引鍵小於陣列項目。|  
|0|索引鍵等於陣列項目。|  
|> 0|索引鍵大於陣列項目。|  
  
 這個函式會驗證它的參數。 如果找不到 `compare`、 `key` 或 `num` 為 `NULL`，或是如果 `base` 為 `NULL` 且 *`num` 非零，或是如果 `width` 為零，則叫用的參數處理常式無效，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)。 若允許繼續執行， `errno` 會設為 `EINVAL` ，且此函式會傳回 `NULL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`bsearch`|\<stdlib.h> 和 \<search.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 這個程式會以 qsort 來排序字串陣列，然後使用 bsearch 來尋找 cat 這個字。  
  
```  
// crt_bsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( char **arg1, char **arg2 )  
{  
   /* Compare all of both strings: */  
   return _strcmpi( *arg1, *arg2 );  
}  
  
int main( void )  
{  
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};  
   char **result;  
   char *key = "cat";  
   int i;  
  
   /* Sort using Quicksort algorithm: */  
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const   
   void*, const void*))compare );  
  
   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */  
      printf( "%s ", arr[i] );  
  
   /* Find the word "cat" using a binary search algorithm: */  
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),  
                              sizeof( char * ), (int (*)(const void*, const void*))compare );  
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
  
## <a name="see-also"></a>另請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)
