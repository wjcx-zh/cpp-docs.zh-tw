---
title: qsort | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- qsort
dev_langs:
- C++
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 19
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
ms.openlocfilehash: b71bdc6b2b2bff50645a7ce8ae1ef88ad4d6dd91
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="qsort"></a>qsort
執行快速排序。 目前有比這個函式更安全的版本；請參閱 [qsort_s](../../c-runtime-library/reference/qsort-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void qsort(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>參數  
 `base`  
 目標陣列的開頭。  
  
 `num`  
 陣列大小 (以項目計)。  
  
 `width`  
 項目大小 (以位元組計)。  
  
 `compare`  
 使用者提供之常式的指標，該常式比較兩個陣列元素，然後傳回一個指定其關聯性的值。  
  
## <a name="remarks"></a>備註  
 `qsort` 函式會實作快速排序演算法，來排序 `num` 項目陣列，每個項目 `width` 個位元組。 `base` 引數是要排序之陣列基底的指標。 `qsort` 使用已排序的項目來覆寫這個陣列。  
  
 `qsort` 在搜尋時會呼叫 `compare` 常式一或多次，每次呼叫會將指標傳遞至兩個陣列元素。  
  
```  
compare( (void *) & elem1, (void *) & elem2 );  
```  
  
 常式會比較這些項目，然後傳回下列其中一個值。  
  
|比較函式傳回值|描述|  
|-----------------------------------|-----------------|  
|< 0|`elem1` 小於 `elem2`|  
|0|`elem1` 相當於 `elem2`|  
|> 0|`elem1` 大於 `elem2`|  
  
 陣列是以比較函式所定義的遞增順序排序。 若要以遞減順序排序陣列，請將比較函式中的「大於」和「小於」意義反轉。  
  
 這個函式會驗證它的參數。 如果 `compare` 或 `num` 是 `NULL`，或者如果 `base` 是 `NULL` 且 *`num` 為非零值，或如果 `width` 小於零，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回此函式，並將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`qsort`|\<stdlib.h> 和 \<search.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
boy deserves every favor good  
```  
  
## <a name="see-also"></a>另請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)
