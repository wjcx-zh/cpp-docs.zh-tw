---
title: bsearch
ms.date: 4/2/2020
api_name:
- bsearch
- _o_bsearch
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3a6083f39e12182ae512f5327b5f7d8d89deb2a2
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039543"
---
# <a name="bsearch"></a>bsearch

對已排序陣列執行二進位搜尋。 這個函式已有更安全的版本可用；請參閱 [bsearch_s](bsearch-s.md)。

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

*關鍵*\
要搜尋之索引鍵的指標。

*基地*\
搜尋資料基底的指標。

*數量*\
項目數。

*寬度*\
項目的寬度。

*比較*\
比較兩個項目的回呼函式。 第一個是搜尋索引鍵的指標，而第二個則是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

**bsearch**會將指標傳回至*基底*所指向陣列中的索引*鍵*出現位置。 如果找不到索引 *鍵* ，則函數會傳回 **Null**。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。

## <a name="remarks"></a>備註

**Bsearch**函式會對*數位*元素的已排序陣列執行二進位搜尋，而每個大小的*寬度*位元組都是大小。 *基底*值是要搜尋之陣列基底的指標，而索引*鍵*是要搜尋的值。 *Compare*參數是使用者所提供之常式的指標，可比較所要求的索引鍵與陣列元素。 它會傳回下列其中一個指定其關聯性的值：

|*比較*常式傳回的值|描述|
|-----------------------------------------|-----------------|
|`< 0`|索引鍵小於陣列項目。|
|`0`|索引鍵等於陣列項目。|
|`> 0`|索引鍵大於陣列項目。|

這個函式會驗證它的參數。 如果 *比較*、索引 *鍵* 或 *數位* 為 **null**，或 *base* 為 **null** 且 *數位* 為非零值，或 *寬度* 為零，則此函式會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno** 會設為， `EINVAL` 且函數會傳回 **Null**。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> 和 \<search.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另請參閱

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
