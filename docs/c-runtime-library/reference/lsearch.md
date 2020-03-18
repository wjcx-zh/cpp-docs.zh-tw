---
title: _lsearch
ms.date: 11/04/2016
api_name:
- _lsearch
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
ms.openlocfilehash: 6dc610c4ab120d81bfb2b3b5e64a54a104bea97f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438152"
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

*key*<br/>
要搜尋的物件。

*base*<br/>
要搜尋之陣列的基底指標。

*number*<br/>
項目數。

*寬度*<br/>
每個陣列元素的寬度。

*compare*<br/>
比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

如果找到索引鍵， **_lsearch**會傳回符合索引*鍵*之*基底*陣列元素的指標。 如果找不到索引鍵， **_lsearch**會傳回陣列結尾新增專案的指標。

## <a name="remarks"></a>備註

**_Lsearch**函式會在*數位*元素陣列中執行值索引*鍵*的線性搜尋，每個*寬度*為位元組。 不同于**bsearch**， **_lsearch**不需要排序陣列。 如果找不到索引*鍵*， **_lsearch**會將它新增至陣列結尾，並遞增*數位*。

*Compare*引數是使用者所提供之常式的指標，可比較兩個陣列元素，並傳回指定其關聯性的值。 **_lsearch**在搜尋期間呼叫*比較*常式一或多次，並在每次呼叫時將指標傳遞至兩個陣列元素。 「*比較*」必須比較元素，並傳回非零（表示元素不同）或0（表示專案完全相同）。

這個函式會驗證它的參數。 如果*compare*、 *key*或*number*為**null**，或*base*為**null** ，而*number*為非零，或*Width*小於零，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**Null**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
