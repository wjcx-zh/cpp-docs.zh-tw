---
title: _lfind_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lfind_s
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
- lfind_s
- _lfind_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 963b657a009f7376a17706b4ac1e5fb4e8b69237
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404814"
---
# <a name="lfinds"></a>_lfind_s

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

*數字*<br/>
陣列元素數目。

*size*<br/>
陣列元素的大小，以位元組為單位。

*compare*<br/>
比較常式的指標。 第一個參數是*內容*指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。

*context*<br/>
可能在比較函式中存取之物件的指標。

## <a name="return-value"></a>傳回值

如果找到機碼， **_lfind_s**傳回的陣列元素的指標*基底*符合*金鑰*。 如果找不到索引鍵， **_lfind_s**傳回**NULL**。

若傳遞了無效的參數到此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**NULL**。

### <a name="error-conditions"></a>錯誤狀況

|key|base|compare|num|大小|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|任何|任何|任何|任何|**EINVAL**|
|任何|**NULL**|任何|!= 0|任何|**EINVAL**|
|任何|任何|任何|任何|零|**EINVAL**|
|任何|任何|**NULL**|an|任何|**EINVAL**|

## <a name="remarks"></a>備註

**_Lfind_s**函式會執行值的線性搜尋*金鑰*陣列中的*數目*項目，每個*寬度*位元組。 不同於**bsearch_s**， **_lfind_s**不需要排序的陣列。 *基底*引數是要搜尋之陣列的基底指標。 *比較*引數是指標，以使用者提供的常式會比較兩個陣列項目，並會傳回值，指定其關聯性。 **_lfind_s**呼叫*比較*在搜尋期間，將例行的一或多次*內容*指標並在每次呼叫的兩個陣列項目的指標。 *比較*常式必須比較項目，然後再傳回則為非零 （表示元素在不同） 或 0 （表示項目完全相同）。

**_lfind_s**類似於 **_lfind**除了新增*內容*比較函式的引數和函式的參數清單的指標。 *內容*指標很有用，如果搜尋的資料結構是物件的一部分而*比較*函式需要存取物件的成員。 *比較*函式可以將 void 指標轉換成適當的物件類型，並存取成員，該物件。 新增*內容*參數，會使 **_lfind_s**更安全，因為其他內容可用來避免重新進入 bug 將資料提供給使用靜態變數相關聯*比較*函式。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
