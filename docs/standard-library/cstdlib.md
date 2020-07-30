---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 1b20e13a43c5d223332af70a91e096cedc284a43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230048"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

包含 C 標準程式庫標頭 \<stdlib.h> ，並將相關名稱新增至 `std` 命名空間。 包含此標頭可確保在 C 標準程式庫標頭中使用外部連結宣告的名稱會在 `std` 命名空間中宣告。

> [!NOTE]
> \<stdlib.h>不包含類型 **`wchar_t`** 。

## <a name="requirements"></a>需求

**標頭**：\<cstdlib>

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

|函式|說明|
|-|-|
|[_Exit](#_exit)|終止程式，而不使用析構函數或已註冊的函式。|
|[abort](#abort)|終止程式而不使用析構函數。|
|[atexit](#atexit)|註冊程式終止的函式。|
|[exit](#exit)|使用執行緒和靜態儲存體終結物件，然後傳回 control。|
|[at_quick_exit](#at_quick_exit)|註冊函式，但不包含程式終止的引數。|
|[quick_exit](#quick_exit)|使用保留的物件註冊函式，以進行程式終止。|
|[getenv](#getenv)|請參閱 C 標準程式庫參考。|
|[系統](#system)|請參閱 C 標準程式庫參考。|

### <a name="_exit"></a><a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>備註

程式會終止，而不會針對自動、執行緒或靜態儲存期間的物件執行析構函式，而且不會呼叫傳遞至的函式 `atexit()` 。 函 `_Exit` 式為信號安全。

### <a name="abort"></a><a name="abort"></a>abort

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>備註

程式會終止，而不會針對自動、執行緒或靜態儲存期間的物件執行析構函式，而且不會呼叫傳遞至的函式 `atexit()` 。 函 `abort` 式為信號安全。

### <a name="at_quick_exit"></a><a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>傳回值

如果註冊成功，則為零，如果失敗，則為非零。

#### <a name="remarks"></a>備註

函式會 `at_quick_exit()` 註冊函數*func*，當呼叫時，不需要引數就會呼叫它 `quick_exit` 。 對的呼叫不會 `at_quick_exit()` 在所有呼叫都成功之前發生 `quick_exit` 。 這些 `at_quick_exit()` 函數不會引進資料競爭。 如果從多個執行緒呼叫，則註冊的順序可能會是不確定的 `at_quick_exit` 。 由於 `at_quick_exit` 註冊與 `atexit` 註冊不同，因此應用程式可能需要使用相同的引數呼叫這兩個註冊函式。 MSVC 支援至少註冊32個函式。

### <a name="atexit"></a><a name="atexit"></a>atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>備註

函式 `atexit()` 會在正常程式終止時*func* ，以不含引數的方式來註冊要呼叫的函式。 呼叫不會在 `atexit()` 呼叫之前才會 `exit()` 成功。 這些 `atexit()` 函數不會引進資料競爭。

#### <a name="return-value"></a>傳回值

如果註冊成功，則傳回零，如果失敗，則傳回非零。

### <a name="exit"></a><a name="exit"></a>退出

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>備註

首先，具有線程儲存期且與目前線程相關聯的物件會被終結。

接下來，系統會終結具有靜態儲存期的物件，並呼叫透過呼叫註冊的函式 `atexit` 。 當呼叫時，自動物件不會損毀 `exit()` 。 如果控制項離開由呼叫的已註冊函式 `exit` ，因為函式未提供所擲回例外狀況的處理常式， `std::terminate()` 則會呼叫。 函式會在每次註冊時呼叫一次。 具有自動儲存期的物件會在其函式 `main` 未包含任何自動物件的程式中終結，並執行對的呼叫 `exit()` 。 控制項可以直接傳送到這類函式，方法是擲回中攔截到的 `main` 例外狀況 `main` 。

接下來，會清除所有開啟的 C 資料流程（如中所宣告的函式簽章所 mediated \<cstdio> ）和不成文緩衝的資料，所有開啟的 c 資料流程都會關閉，而且會移除所有以呼叫所建立的檔案 `tmpfile()` 。

最後，會將控制權傳回給主機環境。 當*status*為零或 EXIT_SUCCESS 時，會傳回實值定義形式的狀態成功終止。 MSVC 會傳回零值。 如果*status*為 EXIT_FAILURE，MSVC 會傳回值3。 否則，MSVC 會傳回*status*參數值。

### <a name="getenv"></a><a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a><a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>備註

一般來說，呼叫所註冊的函式 `at_quick_exit` 會以其註冊的反向順序呼叫。 此順序不適用於已呼叫其他已註冊函式之後註冊的函式。 呼叫時，不會終結任何物件 `quick_exit` 。 如果控制項離開由呼叫的已註冊函式 `quick_exit` ，因為函式未提供所擲回例外狀況的處理常式， `std::terminate()` 則會呼叫。 透過註冊的函式 `at_quick_exit` 是由呼叫的執行緒所叫用 `quick_exit` ，它可以是與註冊它不同的執行緒。 這表示已註冊的函式不應依賴具有線程儲存期的物件身分識別。 呼叫已註冊的函式之後，會 `quick_exit` 呼叫 `_Exit(status)` 。 標準檔案緩衝區不會排清。 `quick_exit`當使用註冊的函式為時，函數是信號安全 `at_quick_exit` 。

### <a name="system"></a><a name="system"></a>筆記本電腦

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>記憶體配置函數

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。 MSVC 不支援 `aligned_alloc` 函數。 C11 指定的 `aligned_alloc()` 方式與 Microsoft 的實作為不相容 `free()` ，亦即 `free()` 必須能夠處理高度對齊的配置。

## <a name="numeric-string-conversions"></a>數值字串轉換

```cpp
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

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>多位元組/寬字元串和字元轉換函式

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
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

## <a name="integer-division"></a>整數除數

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中指定的語法。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫總覽](../standard-library/cpp-standard-library-overview.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
