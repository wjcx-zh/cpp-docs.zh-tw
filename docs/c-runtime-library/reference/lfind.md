---
title: _lfind
ms.date: 11/04/2016
apiname:
- _lfind
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
- lfind
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 1508d54d6b2f2566e4aee3afef02af45b28e4f48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286488"
---
# <a name="lfind"></a>_lfind

執行所指定索引鍵的線性搜尋。 已有比這個函式更安全的版本；請參閱 [_lfind_s](lfind-s.md)。

## <a name="syntax"></a>語法

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>參數

*key*<br/>
要搜尋的物件。

*base*<br/>
搜尋資料基底的指標。

*number*<br/>
陣列元素數目。

*width*<br/>
陣列元素的寬度。

*compare*<br/>
比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

如果找到索引鍵，則 **_lfind**傳回的項目處之陣列的指標*基底*符合*金鑰*。 如果找不到索引鍵， **_lfind**會傳回**NULL**。

## <a name="remarks"></a>備註

**_Lfind**函式會執行值的線性搜尋*金鑰*陣列中的*號碼*項目，每個*寬度*位元組。 不同於**bsearch**， **_lfind**不需要排序陣列。 *基底*引數是要搜尋之陣列的基底的指標。 *比較*引數是使用者所提供的常式比較兩個陣列元素，則會傳回值，指定其關聯性的指標。 **_lfind**呼叫*比較*在搜尋期間，將指標傳遞至兩個陣列元素中，每次呼叫的常式一或多次。 *比較*常式必須比較項目，然後傳回非零 （表示元素不同） 或 0 （表示元素完全相同）。

這個函式會驗證它的參數。 如果*比較*，*金鑰*或*號碼*是**NULL**，或如果*基底*是**NULL**及*數字*為非零值，或如果*寬度*小於零，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回**NULL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lfind**|\<search.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>另請參閱

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
