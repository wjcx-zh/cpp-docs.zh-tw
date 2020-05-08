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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 91b015eb9005a9b447cdd9d74a38d7169bd90a73
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913384"
---
# <a name="bsearch_s"></a>bsearch_s

對已排序陣列執行二進位搜尋。 此函式是具有 CRT 中的[安全性功能中](../../c-runtime-library/security-features-in-the-crt.md)所述之安全性增強功能的[bsearch](bsearch.md)版本。

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

*擊鍵*\
要搜尋之索引鍵的指標。

*群體*\
搜尋資料基底的指標。

*項數*\
項目數。

*寬度*\
項目的寬度。

*何*\
比較兩個項目的回呼函式。 第一個引數是*內容*指標。 第二個引數是搜尋索引*鍵*的指標。 第三個引數是要與索引*鍵*比較之陣列元素的指標。

*內容*\
可以在比較函式中存取的物件指標。

## <a name="return-value"></a>傳回值

**bsearch_s**會傳回*基底*所指向陣列中索引*鍵*的出現指標。 如果找不到索引*鍵*，則函數會傳回**Null**。 如果陣列不是以遞增排序次序，或是包含具有相同索引鍵的重複記錄，則無法預測結果。

如果將不正確參數傳遞至函式，它會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**Null**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤條件

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*何*|*number*|*寬度*|**errno**|
|**Null**|任意|任意|任意|任意|**EINVAL**|
|任意|**Null**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|= 0|**EINVAL**|
|任意|任意|**Null**|an|任意|**EINVAL**|

## <a name="remarks"></a>備註

**Bsearch_s**函式會對已排序的*數位*元素陣列執行二進位搜尋，每個*寬度*的大小為。 *基底*值是要搜尋之陣列的基底指標，而*key*則是要尋找的值。 *Compare*參數是使用者提供的常式指標，可將所要求的索引鍵與陣列元素進行比較，並傳回下列其中一個指定其關聯性的值：

|*比較*常式傳回的值|描述|
|-----------------------------------------|-----------------|
|\< 0|索引鍵小於陣列項目。|
|0|索引鍵等於陣列項目。|
|> 0|索引鍵大於陣列項目。|

如果搜尋的資料結構是物件的一部分，且比較函式需要存取物件的成員，則*內容*指標可能會很有用。 *Compare*函數可以將 void 指標轉換成適當的物件類型，並存取該物件的成員。 新增*內容*參數會使**bsearch_s**更安全，因為可能會使用額外的內容來避免與使用靜態變數相關聯的重新進入 bug，讓資料可供*compare*函數使用。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
