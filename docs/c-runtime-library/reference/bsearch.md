---
title: bsearch
ms.date: 11/04/2016
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
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: a5f4542623dfa503d7ec43dff0cf0de9e69ccec4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464840"
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

*key*<br/>
要搜尋的物件。

*base*<br/>
搜尋資料的基底指標。

*數字*<br/>
項目數。

*width*<br/>
項目的寬度。

*compare*<br/>
比較兩個項目的回呼函式。 第一個是搜尋索引鍵的指標，第二個是要與索引鍵比較的陣列項目的指標。

## <a name="return-value"></a>傳回值

**bsearch**讓指標回到一段*金鑰*所指陣列中*基底*。 如果*金鑰*找不到，則函數會傳回**NULL**。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。

## <a name="remarks"></a>備註

**Bsearch**函式會執行二進位搜尋的已排序陣列*數目*項目，每個*寬度*個位元組大小。 *基底*的值是要搜尋之陣列的基底的指標並*金鑰*是要搜尋的值。 *比較*參數是使用者所提供的常式會比較要求的索引鍵的陣列項目，並傳回其中一個指定其關聯性的下列值的指標：

|傳回值*比較*常式|描述|
|-----------------------------------------|-----------------|
|\< 0|索引鍵小於陣列項目。|
|0|索引鍵等於陣列項目。|
|> 0|索引鍵大於陣列項目。|

這個函式會驗證它的參數。 如果*比較*，*金鑰*或*號碼*是**NULL**，或如果*基底*是**NULL**並*數字*為非零值，或如果*寬度*為零，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為`EINVAL`和函式會傳回**NULL**。

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

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
