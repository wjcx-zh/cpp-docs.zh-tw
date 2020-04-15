---
title: _lfind_s
ms.date: 4/2/2020
api_name:
- _lfind_s
- _o__lfind_s
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
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 8f2983bee93c623eb936ed12422134281418076b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342191"
---
# <a name="_lfind_s"></a>_lfind_s

執行所指定索引鍵的線性搜尋。 這是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強的 [_lfind](lfind.md) 版本。

## <a name="syntax"></a>語法

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的物件。

*base*<br/>
搜尋資料基底的指標。

*數量*<br/>
陣列元素數目。

*大小*<br/>
陣列元素的大小，以位元組為單位。

*比較*<br/>
比較常式的指標。 第一個參數是*上下文*指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。

*內容*<br/>
可能在比較函式中存取之物件的指標。

## <a name="return-value"></a>傳回值

如果找到該鍵 **,_lfind_s**返回指向*基上*與*鍵*匹配的陣列元素的指標。 如果未找到這個鍵 **,_lfind_s**傳回**NULL**。

如果將無效參數傳遞給函數,則調用無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,errno**將設定為**EINVAL,** 並且函數傳回**NULL**。

### <a name="error-conditions"></a>錯誤狀況

|索引鍵|base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**空**|任意|任意|任意|任意|**埃因瓦爾**|
|任意|**空**|任意|!= 0|任意|**埃因瓦爾**|
|任意|任意|任意|任意|零|**埃因瓦爾**|
|任意|任意|**空**|an|任意|**埃因瓦爾**|

## <a name="remarks"></a>備註

**_lfind_s**函數對*數位*元素陣列中的值*鍵*執行線性搜索,每個數位都是*寬度*位元組。 與**bsearch_s**不同 **,_lfind_s**不需要對陣列進行排序。 *基*參數是指向要搜索的陣列基礎的指標。 *比較*參數是指向使用者提供的例程的指標,該例程比較兩個陣列元素,然後返回指定其關係的值。 **_lfind_s**在搜索期間調用*比較*例程一次或多次,將*上下文*指標和指標傳遞給每個調用上的兩個陣列元素。 *比較*例程必須比較元素,然後返回非零(表示元素不同)或 0(表示元素相同)。

**_lfind_s**與 **_lfind**類似,除了添加指向比較函數的參數和函數的參數清單的*上下文*指標。 如果搜索的數據結構是物件的一部分,並且*比較*函數需要訪問對象的成員,則*上下文*指標非常有用。 *比較*函數可以將 void 指標轉換為相應的物件類型並存取該物件的成員。 添加*上下文*參數使 **_lfind_s更安全,** 因為可以使用其他上下文來避免與使用靜態變數使數據可用於*比較*函數相關的重入錯誤。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_lfind_s.cpp
// This program uses _lfind_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char *s1 = *(char**)str1;
    char *s2 = *(char**)str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

void find_it( char *key, char *array[], unsigned int num, locale &loc )
{
   char **result = (char **)_lfind_s( &key, array,
                      &num, sizeof(char *), compare, &loc );
   if( result )
      printf( "%s found\n", *result );
   else
      printf( "%s not found\n", key );
}

int main( )
{
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );
}
```

```Output
weit found
```

## <a name="see-also"></a>另請參閱

[搜尋及排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
