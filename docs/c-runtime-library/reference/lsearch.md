---
title: _lsearch
ms.date: 4/2/2020
api_name:
- _lsearch
- _o__lsearch
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
- _lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: a6ef3d86ffe8f03da34d4a374bddda1452815672
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341642"
---
# <a name="_lsearch"></a>_lsearch

執行值的線性搜尋；如果找不到，則新增至清單結尾。 這個函式已有更安全的版本可用；請參閱 [_lsearch_s](lsearch-s.md)。

## <a name="syntax"></a>語法

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的物件。

*base*<br/>
要搜尋之陣列的基底指標。

*數量*<br/>
項目數。

*寬度*<br/>
每個陣列元素的寬度。

*比較*<br/>
比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

如果找到該鍵 **,_lsearch**返回指向*基中*與*鍵*匹配的陣組元素的指標。 如果未找到該鍵 **,_lsearch**將返回指向陣列末尾新添加的項的指標。

## <a name="remarks"></a>備註

**_lsearch**函數對*數位*元素陣列中的值*鍵*執行線性搜索,每個數位都是*寬度*位元組。 與**bsearch**不同 **,_lsearch**不需要對陣列進行排序。 如果未找到*鍵***,_lsearch**將列為陣列的末尾並遞增*編號*。

*比較*參數是指向使用者提供的例程的指標,該例程比較兩個陣組元素並返回指定其關係的值。 **_lsearch**在搜索期間調用*比較*例程一次或多次,將指標傳遞到每個調用上的兩個陣組元素。 *比較*必須比較元素並返回非零(表示元素不同)或 0(表示元素相同)。

這個函式會驗證它的參數。 如果*比較*,*鍵*或*數位*為**NULL,** 或者如果*基*為**NULL**且*數位*為非零,或者如果*寬度*小於零,則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,errno**將設定為**EINVAL,** 並且函數傳回**NULL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_lsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main(void)
{
   char * wordlist[4] = { "hello", "thanks", "bye" };
                            // leave room to grow...
   int n = 3;
   char **result;
   char *key = "extra";
   int i;

   printf( "wordlist before _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );

   result = (char **)_lsearch( &key, wordlist,
                      &n, sizeof(char *), compare );

   printf( "wordlist after _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );
}

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}
```

```Output
wordlist before _lsearch: hello thanks bye
wordlist after _lsearch: hello thanks bye extra
```

## <a name="see-also"></a>另請參閱

[搜尋及排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
