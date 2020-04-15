---
title: _lfind
ms.date: 4/2/2020
api_name:
- _lfind
- _o__lfind
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 287cbd8bc9cc567a4a0d5b9505d57098197bc545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342167"
---
# <a name="_lfind"></a>_lfind

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

*關鍵*<br/>
要搜尋的物件。

*base*<br/>
搜尋資料基底的指標。

*數量*<br/>
陣列元素數目。

*寬度*<br/>
陣列元素的寬度。

*比較*<br/>
比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

如果找到該鍵 **,_lfind**返回指向*基中*與*鍵*匹配的陣列元素的指標。 如果未找到這個鍵 **,_lfind**傳回**NULL**。

## <a name="remarks"></a>備註

**_lfind**函數對*數位*元素陣列中的值*鍵*執行線性搜索,每個數位都是*寬度*位元組。 與**bsearch**不同 **,_lfind**不需要對陣列進行排序。 *基*參數是指向要搜索的陣列基礎的指標。 *比較*參數是指向使用者提供的例程的指標,該例程比較兩個陣列元素,然後返回指定其關係的值。 **_lfind**在搜索期間調用*比較*例程一次或多次,將指標傳遞到每個調用上的兩個陣組元素。 *比較*例程必須比較元素,然後返回非零(表示元素不同)或 0(表示元素相同)。

這個函式會驗證它的參數。 如果*比較*,*鍵*或*數位*為**NULL,** 或者如果*基*為**NULL**且*數位*為非零,或者如果*寬度*小於零,則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,errno**將設定為**EINVAL,** 並且函數傳回**NULL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lfind**|\<search.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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

[搜尋及排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
