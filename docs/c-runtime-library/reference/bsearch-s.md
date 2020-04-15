---
title: bsearch_s
ms.date: 4/2/2020
api_name:
- bsearch_s
- _o_bsearch_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: ef8a68f0db45e718af6b17fe0d08c33a6fd61d6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333839"
---
# <a name="bsearch_s"></a>bsearch_s

對已排序陣列執行二進位搜尋。 此功能是具有安全增強功能的[bsearch](bsearch.md)版本,如[CRT 中的安全功能中](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>語法

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
);
```

### <a name="parameters"></a>參數

*關鍵*\
指向要搜索的鍵的指標。

*基地*\
指向搜索數據的基礎。

*數量*\
項目數。

*寬度*\
項目的寬度。

*比較*\
比較兩個項目的回呼函式。 第一個參數是*上下文*指標。 第二個參數是指向搜索*鍵*的指標。 第三個參數是指向要與*鍵*進行比較的陣列元素的指標。

*內容*\
可以在比較函式中存取的物件指標。

## <a name="return-value"></a>傳回值

**bsearch_s**返回指向*基*指向陣列中*鍵*事件的指標。 如果未找到*鍵*,則函數會傳回**NULL**。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。

如果將無效參數傳遞給函數,它將調用無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,errno**將設定為**EINVAL,** 並且函數傳回**NULL**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤條件

|||||||
|-|-|-|-|-|-|
|*關鍵*|*base*|*比較*|*數量*|*寬度*|**errno**|
|**空**|任意|任意|任意|任意|**埃因瓦爾**|
|任意|**空**|任意|!= 0|任意|**埃因瓦爾**|
|任意|任意|任意|任意|= 0|**埃因瓦爾**|
|任意|任意|**空**|an|任意|**埃因瓦爾**|

## <a name="remarks"></a>備註

**bsearch_s**函數對*數位*元素的排序陣列執行二進位搜索,每個陣列的大小都是*寬度*位元組。 *基*值是指向要搜尋的陣元基礎的指標,*鍵*是要查找的值。 *比較*參數是指向使用者提供的例程的指標,該例程將請求的鍵與陣列元素進行比較,並返回指定其關係的以下值之一:

|*預設*常返回的值|描述|
|-----------------------------------------|-----------------|
|\< 0|索引鍵小於陣列項目。|
|0|索引鍵等於陣列項目。|
|> 0|索引鍵大於陣列項目。|

如果搜索的數據結構是物件的一部分,並且比較函數需要訪問對象的成員,則*上下文*指標可能很有用。 *比較*函數可能會將 void 指標轉換為相應的物件類型並造訪該物件的成員。 添加*上下文*參數使**bsearch_s更安全,** 因為可以使用其他上下文來避免與使用靜態變數使數據可用於*比較*函數相關的重入錯誤。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> 和 \<search.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

這個程式會以 [qsort_s](qsort-s.md) 來排序字串陣列，然後使用 bsearch_s 來尋找 "cat" 這個字。

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
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
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>另請參閱

[搜尋及排序](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
