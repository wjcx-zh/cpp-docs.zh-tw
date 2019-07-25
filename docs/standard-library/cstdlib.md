---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 298d6a512b2863a326bda0670f33fe8f1bda0688
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449401"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

包含 C 標準程式庫標\<頭 stdlib.h> >, 並將相關聯的名稱加入`std`至命名空間。 包含此標頭可確保在 C 標準程式庫標頭中使用外部連結宣告的名稱會`std`在命名空間中宣告。

> [!NOTE]
> \<stdlib.h> > 不包含**wchar_t**類型。

## <a name="requirements"></a>需求

**標頭**: \<b >

**命名空間：** std

## <a name="namespace-and-macros"></a>命名空間和宏

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>僅展示函式

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>開始和終止函式

|功能|說明|
|-|-|
|[_Exit](#_exit)|終止程式, 而不使用析構函數或已註冊的函式。|
|[abort](#abort)|終止程式而不使用析構函數。|
|[atexit](#atexit)|註冊程式終止的函式。|
|[exit](#exit)|使用執行緒和靜態儲存體終結物件, 然後傳回 control。|
|[at_quick_exit](#at_quick_exit)|註冊函式, 但不包含程式終止的引數。|
|[quick_exit](#quick_exit)|使用保留的物件註冊函式, 以進行程式終止。|
|[getenv](#getenv)|請參閱 C 標準程式庫參考。|
|[system](#system)|請參閱 C 標準程式庫參考。|

### <a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>備註

程式會終止, 而不會針對自動、執行緒或靜態儲存期間的物件執行析構函式, 而且不`atexit()`會呼叫傳遞至的函式。 函式`_Exit`為信號安全。

### <a name="abort"></a>abort

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>備註

程式會終止, 而不會針對自動、執行緒或靜態儲存期間的物件執行析構函式, 而且不`atexit()`會呼叫傳遞至的函式。 函式`abort`為信號安全。

### <a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>傳回值

如果註冊成功, 則為零, 如果失敗, 則為非零。

#### <a name="remarks"></a>備註

當呼叫時`quick_exit` , 函式會在不使用引數的情況下註冊 func 所指向的函式。  `at_quick_exit()` 在所有`at_quick_exit()` `quick_exit`呼叫都成功且`at_quick_exit()`函式不會引進資料競爭情況之前, 不會指定是否呼叫。 如果`at_quick_exit`從多個執行緒呼叫, `at_quick_exit`且註冊與`atexit`註冊不同, 則登錄的順序可能不確定, 應用程式可能需要呼叫這兩個註冊函式, 並使用相同的引數。 此實作為必須支援至少32個函數的註冊。

### <a name="atexit"></a>atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>備註

函`atexit()`式會在正常程式終止時 , 以不含引數的方式來註冊要呼叫的函式。 未指定是否在`atexit()` `exit()`呼叫之前不會發生呼叫, 而且`atexit()`函數不會引進資料競爭。此實作為必須支援至少32個函數的註冊。

#### <a name="return-value"></a>傳回值

如果註冊成功, 則傳回零, 如果失敗, 則傳回非零。

### <a name="exit"></a>退出

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>備註

首先, 具有線程儲存期且與目前線程相關聯的物件會被終結。

接下來, 系統會終結具有靜態儲存期的物件, 並`atexit`呼叫透過呼叫註冊的函式。 自動物件不會因呼叫`exit()`而遭到終結。 如果控制項離開由呼叫的已註冊`exit`函式, 因為函式未提供所擲回例外`std::terminate()`狀況的處理常式, 則應呼叫。 函式會在每次註冊時呼叫。 具有自動儲存期的物件會在主要函式未包含任何自動物件的程式中終結, 並執行`exit()`對的呼叫。 您可以藉由擲回 main 中攔截到的例外狀況, 將控制項直接傳送到這類 main 函式。

接下來, 會清除所有開啟的 c 資料流程 (如中<cstdio>所宣告的函式簽章所 mediated) 和不成文緩衝的資料, 所有開啟的 c 資料流程都會關閉, 而且會移除所有以呼叫`tmpfile()`所建立的檔案。

最後, 會將控制權傳回給主機環境。 如果 status 為零或 EXIT_SUCCESS, 則會傳回實值定義形式的狀態成功終止。 如果狀態是 EXIT_FAILURE, 則會傳回執行定義的狀態不成功的形式。 否則, 傳回的狀態會是「執行定義」。

### <a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>備註

由的呼叫`at_quick_exit`所註冊的函式會以其註冊的反向順序呼叫, 不同之處在于函式必須在註冊後呼叫過的任何先前已註冊函式之後呼叫。 物件不應因呼叫`quick_exit`而終結。 如果控制項離開由呼叫的已註冊`quick_exit`函式, 因為函式未提供所擲回例外`std::terminate()`狀況的處理常式, 則應呼叫。 透過註冊`at_quick_exit`的函式是由呼叫的執行緒所`quick_exit`叫用, 它可以是與註冊它不同的執行緒, 因此, 已註冊的函式不應依賴具有線程儲存期的物件身分識別。 呼叫已註冊的函`quick_exit`式之後`_Exit(status)`, 應該會呼叫。 標準檔案緩衝區不會排清。 當使用`quick_exit` `at_quick_exit`註冊的函式為時, 函數是信號安全。

### <a name="system"></a>筆記本電腦

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>記憶體配置函數

```cpp
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

#### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>多位元組/寬字元串和字元轉換函式

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

## <a name="algorithm-functions"></a>演算法函式

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

## <a name="low-quality-random-number-generation-functions"></a>低品質的亂數字產生函數

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

## <a name="absolute-values"></a>絕對值

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

## <a name="functions"></a>函式

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
