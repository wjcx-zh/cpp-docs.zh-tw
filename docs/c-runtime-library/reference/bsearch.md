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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: efad391eb2512cfa59cc3597430a84727676f27e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333809"
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
指向要搜索的鍵的指標。

*基地*\
指向搜索數據的基礎。

*數量*\
項目數。

*寬度*\
項目的寬度。

*比較*\
比較兩個項目的回呼函式。 第一個是指向搜索鍵的指標,第二個是指向要與鍵進行比較的陣組元素的指標。

## <a name="return-value"></a>傳回值

**bsearch**傳回指向*基*指向的陣列中*鍵*事件的指標。 如果未找到*鍵*,則函數會傳回**NULL**。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。

## <a name="remarks"></a>備註

**bsearch**函數對*數位*元素的已排序數位執行二進位搜索,每個陣列的大小都是*寬度*位元組。 *基*值是指向要搜尋的陣元基礎的指標,*鍵*是要查找的值。 *比較*參數是指向使用者提供的例程的指標,該例程將請求的鍵與陣組元素進行比較。 指定指定其關係的以下值之一:

|*預設*常返回的值|描述|
|-----------------------------------------|-----------------|
|\< 0|索引鍵小於陣列項目。|
|0|索引鍵等於陣列項目。|
|> 0|索引鍵大於陣列項目。|

這個函式會驗證它的參數。 如果*比較*,*鍵*或*數位*為**NULL,** 或者如果*基*為**NULL**且*數位*為非零,或者如果*寬度*為零,則函數將呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則**將 errno**`EINVAL`設定為 ,函數傳回**NULL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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

[搜尋及排序](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
