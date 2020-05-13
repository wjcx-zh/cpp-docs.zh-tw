---
title: qsort
ms.date: 4/2/2020
api_name:
- qsort
- _o_qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 3d9c3481b37e94dbb59ee7356caafc53501045ea
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913263"
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

*number*<br/>
陣列大小 (以項目計)。

*寬度*<br/>
元素大小 (以位元組為單位)。

*何*<br/>
使用者提供之常式的指標，該常式比較兩個陣列元素，然後傳回一個指定其關聯性的值。

## <a name="remarks"></a>備註

**Qsort**函式會執行快速排序演算法，以排序*數位*元素陣列，每個*寬度*為位元組。 引數*基底*是要排序之陣列基底的指標。 **qsort**會使用已排序的元素來覆寫此陣列。

**qsort**會在排序期間呼叫*比較*常式一或多次，並在每次呼叫時將指標傳遞至兩個陣列元素。

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

這個函式會驗證它的參數。 如果*compare*或*number*為**Null**，或*base*為**null** ，而*number*為非零，或*width*小於零，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回，而**errno**會設定為**EINVAL**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
