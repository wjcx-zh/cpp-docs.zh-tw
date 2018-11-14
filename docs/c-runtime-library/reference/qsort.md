---
title: qsort
ms.date: 11/04/2016
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
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: dd2fc9cd789b02f1fa1e0b9969b597aa51aceedd
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327547"
---
# <a name="qsort"></a>qsort

執行快速排序。 目前有比這個函式更安全的版本；請參閱 [qsort_s](qsort-s.md)。

## <a name="syntax"></a>語法

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>參數

*base*<br/>
目標陣列的開頭。

*數字*<br/>
陣列大小 (以項目計)。

*width*<br/>
項目大小 (以位元組計)。

*compare*<br/>
使用者提供之常式的指標，該常式比較兩個陣列元素，然後傳回一個指定其關聯性的值。

## <a name="remarks"></a>備註

**Qsort**函式會實作快速排序演算法，來排序的陣列*數目*項目，每個*寬度*位元組。 引數*基底*是要排序之陣列的基底的指標。 **qsort**覆寫這個陣列所使用的已排序的項目。

**qsort**呼叫*比較*常式一或多次，並將指標傳遞至兩個陣列元素中，每次呼叫。

```C
compare( (void *) & elem1, (void *) & elem2 );
```

常式會比較這些項目，然後傳回下列其中一個值。

|比較函式傳回值|描述|
|-----------------------------------|-----------------|
|< 0|**elem1**小於**elem2**|
|0|**elem1**相當於**elem2**|
|> 0|**elem1**大於**elem2**|

陣列是以比較函式所定義的遞增順序排序。 若要以遞減順序排序陣列，請將比較函式中的「大於」和「小於」意義反轉。

這個函式會驗證它的參數。 如果*比較*或*數目*會**NULL**，或如果*基底*是**NULL**和*號碼*為非零值，或者如果*寬度*小於零，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則函數會傳回與**errno**設為**EINVAL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**qsort**|\<stdlib.h> 和 \<search.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
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

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
