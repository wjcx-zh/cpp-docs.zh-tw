---
title: qsort_s
ms.date: 4/2/2020
api_name:
- qsort_s
- _o_qsort_s
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
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: 934801531804345a8cede6ed1ac4abb06bae45b4
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913267"
---
# <a name="qsort_s"></a>qsort_s

執行快速排序。 這是 [qsort](qsort.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
void qsort_s(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>參數

*base*<br/>
目標陣列的開頭。

*number*<br/>
陣列大小 (以項目計)。

*寬度*<br/>
元素大小 (以位元組為單位)。

*何*<br/>
比較函式。 第一個引數是*內容*指標。 第二個引數是搜尋索引*鍵*的指標。 第三個引數是要與索引*鍵*比較之陣列元素的指標。

*內容*<br/>
內容的指標，可以是*比較*常式需要存取的任何物件。

## <a name="remarks"></a>備註

**Qsort_s**函式會執行快速排序演算法，以排序*數位*元素陣列，每個*寬度*為位元組。 引數*基底*是要排序之陣列基底的指標。 **qsort_s**會使用已排序的元素覆寫此陣列。 引數*比較*是使用者提供的常式指標，可比較兩個陣列元素，並傳回指定其關聯性的值。 **qsort_s**會在排序期間呼叫*比較*常式一或多次，並在每次呼叫時將指標傳遞至兩個陣列元素：

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

常式必須比較這些元素，然後傳回下列其中一個值：

|傳回值|描述|
|------------------|-----------------|
|< 0|**elem1**小於**elem2**|
|0|**elem1**相當於**elem2**|
|> 0|**elem1**大於**elem2**|

陣列是以比較函式所定義的遞增順序排序。 若要以遞減順序排序陣列，請將比較函式中的「大於」和「小於」意義反轉。

如果將不正確參數傳遞至函式，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回，而**errno**會設定為**EINVAL**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="error-conditions"></a>錯誤狀況

|索引鍵|base|compare|num|width|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**Null**|任意|任意|任意|任意|**EINVAL**|
|任意|**Null**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|<= 0|**EINVAL**|
|任意|任意|**Null**|任意|任意|**EINVAL**|

**qsort_s**的行為與**qsort**相同，但具有*內容*參數並設定**errno**。 藉由傳遞*內容*參數，比較函數可以使用物件指標來存取物件功能或其他無法透過專案指標存取的資訊。 加入*內容*參數會使**qsort_s**更安全，因為*內容*可以用來避免因為使用靜態變數而引進的重新進入 bug，使共用資訊可供*compare*函數使用。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**qsort_s**|\<stdlib.h> 和 \<search.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫︰** 所有版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

下列範例示範如何在**qsort_s**函數中使用*coNtext*參數。 *CoNtext*參數可讓您更輕鬆地執行安全線程排序。 不使用必須同步處理以確保執行緒安全性的靜態變數，而是在每個排序中傳遞不同的*內容*參數。 在此範例中，會使用地區設定物件做為*內容*參數。

```cpp
// crt_qsort_s.cpp
// compile with: /EHsc /MT
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
// so \x00e1 is the German Sharp S in that codepage and \x00a4
// is the n tilde.

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.850"
#define SPANISH_LOCALE "Spanish_Spain.850"
#define ENGLISH_LOCALE "English_US.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S and \x001f for the n tilde.
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.1252"
#define SPANISH_LOCALE "Spanish_Spain.1252"
#define ENGLISH_LOCALE "English_US.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making sort_array vulnerable to thread
// conflicts.

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char s1[256];
    char s2[256];
    strcpy_s(s1, 256, *(char**)str1);
    strcpy_s(s2, 256, *(char**)str2);
    _strlwr_s( s1, sizeof(s1) );
    _strlwr_s( s2, sizeof(s2) );

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(s1,
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);

}

void sort_array(char *array[], int num, locale &loc)
{
    qsort_s(array, num, sizeof(char*), compare, &loc);
}

void print_array(char *a[], int c)
{
   for (int i = 0; i < c; i++)
      printf("%s ", a[i]);
   printf("\n");

}

void sort_german(void * Dummy)
{
   sort_array(array1, 6, locale(GERMAN_LOCALE));
}

void sort_spanish(void * Dummy)
{
   sort_array(array2, 3, locale(SPANISH_LOCALE));
}

void sort_english(void * Dummy)
{
   sort_array(array3, 3, locale(ENGLISH_LOCALE));
}

int main( )
{
   int i;
   HANDLE threads[3];

   printf("Unsorted input:\n");
   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);

   // Create several threads that perform sorts in different
   // languages at the same time.

   threads[0] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_german , 0, NULL));
   threads[1] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_spanish, 0, NULL));
   threads[2] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_english, 0, NULL));

   for (i = 0; i < 3; i++)
   {
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
      {
         printf("Error creating threads.\n");
         exit(1);
      }
   }

   // Wait until all threads have terminated.
   WaitForMultipleObjects(3, threads, true, INFINITE);

   printf("Sorted output: \n");

   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);
}
```

### <a name="sample-output"></a>範例輸出

```Output
Unsorted input:
weiß weis annehmen weizen Zeit weit
Español España espantado
table tableux tablet
Sorted output:
annehmen weiß weis weit weizen Zeit
España Español espantado
table tablet tableux
```

## <a name="see-also"></a>另請參閱

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
