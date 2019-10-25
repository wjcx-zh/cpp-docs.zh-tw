---
title: bsearch
ms.date: 10/22/2019
api_name:
- bsearch
api_location:
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: 6b476cbdd5e9c072cae03ad1091a96e2d0b7422b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811096"
---
# <a name="bsearch"></a>bsearch

對已排序陣列執行二進位搜尋。 目前有比這個函式更安全的版本；請參閱 [bsearch_s](bsearch-s.md)。

## <a name="syntax"></a>語法

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>參數

*金鑰*\
要搜尋之索引鍵的指標。

*base*\
搜尋資料基底的指標。

\*數目*
項目數。

*寬度*\
項目的寬度。

*比較*\
比較兩個項目的回呼函式。 第一個是搜尋索引鍵的指標，而第二個是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

**bsearch**會傳回*基底*所指向陣列中索引*鍵*的出現指標。 如果找不到索引*鍵*，則函數會傳回**Null**。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。

## <a name="remarks"></a>備註

**Bsearch**函式會對已排序的*數位*元素陣列執行二進位搜尋，每個*寬度*的大小為。 *基底*值是要搜尋之陣列的基底指標，而*key*則是要尋找的值。 *Compare*參數是使用者提供的常式指標，可將所要求的索引鍵與陣列元素進行比較。 它會傳回下列其中一個指定其關聯性的值：

|*比較*常式傳回的值|描述|
|-----------------------------------------|-----------------|
|\< 0|索引鍵小於陣列項目。|
|0|索引鍵等於陣列項目。|
|> 0|索引鍵大於陣列項目。|

這個函式會驗證它的參數。 如果*compare*、 *key*或*number*為**null**，或*base*為**null** ，而*number*為非零，或*width*為零，則函式會叫用不正確參數處理常式，如參數中所述[驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行， **errno**會設為 `EINVAL`，而函式會傳回**Null**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> 和 \<search.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

這個程式會以 qsort 來排序字串陣列，然後使用 bsearch 來尋找 cat 這個字。

```C
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

## <a name="see-also"></a>請參閱

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
