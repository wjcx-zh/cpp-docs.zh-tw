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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 589a413c9f1fb49fbfe8cd1b5eacb9d452716523
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916510"
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

*key*<br/>
要搜尋的物件。

*base*<br/>
搜尋資料基底的指標。

*number*<br/>
陣列元素數目。

*size*<br/>
陣列元素的大小，以位元組為單位。

*何*<br/>
比較常式的指標。 第一個參數是*內容*指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。

*內容*<br/>
可能在比較函式中存取之物件的指標。

## <a name="return-value"></a>傳回值

如果找到索引鍵， **_lfind_s**會傳回符合索引*鍵*之*基底*陣列元素的指標。 如果找不到索引鍵， **_lfind_s**會傳回**Null**。

如果將不正確參數傳遞至函式，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**Null**。

### <a name="error-conditions"></a>錯誤狀況

|索引鍵|base|compare|num|大小|errno|
|---------|----------|-------------|---------|----------|-----------|
|**Null**|任意|任意|任意|任意|**EINVAL**|
|任意|**Null**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|零|**EINVAL**|
|任意|任意|**Null**|an|任意|**EINVAL**|

## <a name="remarks"></a>備註

**_Lfind_s**函式會在*數位*元素陣列中執行值索引*鍵*的線性搜尋，每個*寬度*為位元組。 不同于**bsearch_s**， **_lfind_s**不需要排序陣列。 *基底*引數是要搜尋之陣列基底的指標。 *Compare*引數是使用者所提供之常式的指標，可比較兩個陣列元素，然後傳回一個指定其關聯性的值。 **_lfind_s**在搜尋期間呼叫*比較*常式一或多次，並在每次呼叫時將*內容*指標和指標傳遞至兩個陣列元素。 *比較*常式必須比較元素，然後傳回非零（表示專案不同）或0（表示元素完全相同）。

除了將*內容*指標新增至比較函式的引數和函式的參數清單之外， **_lfind_s**類似 **_lfind** 。 如果搜尋的資料結構是物件的一部分，而且*compare*函式需要存取物件的成員，則*內容*指標可能會很有用。 *Compare*函數可以將 void 指標轉換成適當的物件類型，並存取該物件的成員。 加入*內容*參數會使 **_lfind_s**更安全，因為可以使用額外的內容來避免與使用靜態變數相關聯的重新進入 bug，讓資料可供*compare*函數使用。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
