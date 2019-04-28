---
title: _lsearch
ms.date: 11/04/2016
apiname:
- _lsearch
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
- _lsearch
- lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 340e8ac382972b15acc52013d5d6a51352db969c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285652"
---
# <a name="lsearch"></a>_lsearch

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

*key*<br/>
要搜尋的物件。

*base*<br/>
要搜尋之陣列的基底指標。

*number*<br/>
項目數。

*width*<br/>
每個陣列元素的寬度。

*compare*<br/>
比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

如果找到索引鍵，則 **_lsearch**傳回的項目處之陣列的指標*基底*符合*金鑰*。 如果找不到索引鍵， **_lsearch**傳回新加入的項目，在陣列結尾的指標。

## <a name="remarks"></a>備註

**_Lsearch**函式會執行值的線性搜尋*金鑰*陣列中的*號碼*項目，每個*寬度*位元組。 不同於**bsearch**， **_lsearch**不需要排序陣列。 如果*金鑰*找不到， **_lsearch**將它新增至結尾陣列並遞增*數目*。

*比較*引數是使用者所提供的常式比較兩個陣列元素，並傳回值，指定其關聯性的指標。 **_lsearch**呼叫*比較*在搜尋期間，將指標傳遞至兩個陣列元素中，每次呼叫的常式一或多次。 *比較*必須比較項目，然後傳回非零 （表示元素不同） 或 0 （表示元素完全相同）。

這個函式會驗證它的參數。 如果*比較*，*金鑰*或*號碼*是**NULL**，或如果*基底*是**NULL**及*數字*為非零值，或如果*寬度*小於零，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回**NULL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
