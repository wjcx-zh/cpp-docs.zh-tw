---
title: _lsearch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f38dd8a23cce652b93794f62c775962482fe159
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*數字*<br/>
項目數。

*width*<br/>
每個陣列元素的寬度。

*compare*<br/>
比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。

## <a name="return-value"></a>傳回值

如果找到機碼， **_lsearch**傳回的陣列元素的指標*基底*符合*金鑰*。 如果找不到索引鍵， **_lsearch**傳回新加入的項目，在陣列結尾的指標。

## <a name="remarks"></a>備註

**_Lsearch**函式會執行值的線性搜尋*金鑰*陣列中的*數目*項目，每個*寬度*位元組。 不同於**bsearch**， **_lsearch**不需要排序的陣列。 如果*金鑰*找不到， **_lsearch**將它加入至陣列和遞增端*數目*。

*比較*引數是在使用者提供的常式會比較兩個陣列項目並傳回值，指定其關聯性的指標。 **_lsearch**呼叫*比較*在搜尋期間，將指標傳遞至兩個陣列項目，每次呼叫常式的一或多次。 *比較*必須比較項目，並傳回非零 （表示元素為不同） 或 0 （表示項目完全相同）。

這個函式會驗證它的參數。 如果*比較*，*金鑰*或*數目*是**NULL**，或如果*基底*unll 和 **數目*非零，或如果*寬度*小於零，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**NULL**。

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
