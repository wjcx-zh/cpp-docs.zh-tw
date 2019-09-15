---
title: _lfind
ms.date: 11/04/2016
api_name:
- _lfind
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 8fd2141caf8311844a90a6d12226bb7797ac4734
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953391"
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

如果找到索引鍵， **_lfind**會傳回符合索引*鍵*之*基底*陣列元素的指標。 如果找不到索引鍵， **_lfind**會傳回**Null**。

## <a name="remarks"></a>備註

**_Lfind**函式會在*數位*元素陣列中執行值索引*鍵*的線性搜尋，每個*寬度*為位元組。 不同于**bsearch**， **_lfind**不需要排序陣列。 *基底*引數是要搜尋之陣列基底的指標。 *Compare*引數是使用者所提供之常式的指標，可比較兩個陣列元素，然後傳回一個指定其關聯性的值。 **_lfind**會在搜尋期間呼叫*比較*常式一或多次，並在每次呼叫時將指標傳遞至兩個陣列元素。 *比較*常式必須比較元素，然後傳回非零（表示專案不同）或0（表示元素完全相同）。

這個函式會驗證它的參數。 如果*compare*、 *key*或*number*為**null**，或*base*為**null** ，而*number*為非零，或*Width*小於零，則會叫用不正確參數處理常式，如參數中所述[驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**Null**。

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
