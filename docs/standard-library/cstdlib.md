---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 70e05ad734fa49ba8cb96e4bf83bc05b99c5f55c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246520"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

包含標準 C 程式庫標頭\<stdlib.h> >，並將關聯的名稱加入`std`命名空間。 包含此標頭中宣告的宣告 C 標準程式庫標頭中使用外部連結的名稱可確保`std`命名空間。

> [!NOTE]
> \<stdlib.h> > 不包含型別**wchar_t**。

## <a name="requirements"></a>需求

**標頭**: \<cstdlib> >

**命名空間：** std

## <a name="namespace-and-macros"></a>命名空間和巨集

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

## <a name="exposition-only-functions"></a>Exposition 唯一函式

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>啟動和終止函式

|功能|描述|
|-|-|
|[_Exit](#_exit)|終止程式，而不使用解構函式或已註冊的函式。|
|[abort](#abort)|終止程式，而不使用解構函式。|
|[atexit](#atexit)|程式終止的暫存器函式。|
|[exit](#exit)|終結執行緒與靜態儲存區，然後傳回控制項的物件。|
|[at_quick_exit](#at_quick_exit)|不含程式終止的引數的暫存器函式。|
|[quick_exit](#quick_exit)|程式終止的保留物件的暫存器函式。|
|[getenv](#getenv)|請參閱 C 標準程式庫參考。|
|[system](#system)|請參閱 C 標準程式庫參考。|

### <a name="_exit"></a> _Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>備註

程式會終止，但不會執行物件的自動、 執行緒或靜態儲存期的解構函式，而不需要呼叫函式傳遞至`atexit()`。 此函式`_Exit`是訊號安全。

### <a name="abort"></a> 中止

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>備註

程式會終止，但不會執行物件的自動、 執行緒或靜態儲存期的解構函式，而不需要呼叫函式傳遞至`atexit()`。 此函式`abort`是訊號安全。

### <a name="at_quick_exit"></a> at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>傳回值

如果註冊成功時，如果失敗，則為零。

#### <a name="remarks"></a>備註

`at_quick_exit()`函式註冊所指向之函式*func*呼叫不含引數時`quick_exit`呼叫。 它具有未指定是否呼叫`at_quick_exit()`，不會發生的所有呼叫之前`quick_exit`將會成功，`at_quick_exit()`函式不會產生資料競爭的情形。 註冊的順序可能會不確定如果`at_quick_exit`已從多個比一個執行緒，而由於呼叫`at_quick_exit`註冊是不同的`atexit`註冊，應用程式可能需要呼叫具有這兩種註冊函式相同的引數。 實作必須支援至少 32 函式的註冊。

### <a name="atexit"></a> atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>備註

`atexit()`函式註冊所指向之函式*func*呼叫不含引數，在正常程式終止。 它具有未指定是否呼叫`atexit()`，不會發生之前呼叫`exit()`將會成功，`atexit()`函式不會產生資料競爭的情形。實作必須支援至少 32 函式的註冊。

#### <a name="return-value"></a>傳回值

如果註冊成功，失敗時，非零值，則傳回零。

### <a name="exit"></a> 結束

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>備註

首先，物件具有執行緒儲存期，並與目前相關聯的執行緒會被終結。

接下來，會終結具有靜態儲存期的物件，並藉由呼叫的函式註冊`atexit`稱為。 自動物件不會終結呼叫的結果`exit()`。 如果在程式控制權脫離已註冊的函式呼叫之`exit`函式不會提供一個處理常式擲回的例外狀況，因為`std::terminate()`都應該呼叫。 每次它註冊為，呼叫函式。 具有自動儲存期的物件會終結在程式中的 main 函式不包含自動物件和執行的呼叫`exit()`。 控制項可以是直接傳送到這類 main 的函式所擲回例外狀況攔截到主要。

接下來，所有開啟的 C 資料流 (如中所宣告的函式簽章居中協調<cstdio>) 與不成文的緩衝資料都排清，為所有開啟 C 資料流已關閉和所有的檔案建立藉由呼叫`tmpfile()`會移除。

最後，控制項會傳回給主機環境。 如果狀態是零或 EXIT_SUCCESS 時，會傳回狀態成功終止的實作定義形式。 如果狀態是 exit_failure 時，會傳回實作定義的表單的狀態不成功終止。 否則傳回的狀態是由實作定義。

### <a name="getenv"></a> getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a> quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>備註

藉由呼叫的函式註冊`at_quick_exit`不同之處在於任何先前註冊的已註冊時呼叫的函式之後，應該會呼叫函式呼叫中的註冊，相反的順序。 物件應該不會終結呼叫的結果`quick_exit`。 如果在程式控制權脫離已註冊的函式呼叫之`quick_exit`函式不會提供一個處理常式擲回的例外狀況，因為`std::terminate()`都應該呼叫。 透過已註冊的函式`at_quick_exit`所呼叫的執行緒叫用`quick_exit`，比的註冊，因此註冊函式，它可以是不同的執行緒不應該依賴執行緒儲存期的物件的識別。 在呼叫已註冊的函式之後,`quick_exit`應該會呼叫`_Exit(status)`。 標準檔案不清除緩衝區。 此函式`quick_exit`向註冊函式時，是訊號安全`at_quick_exit`是。

### <a name="system"></a> 系統

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>記憶體配置函式

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

這些函式具有 C 標準程式庫中所指定的語意。

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>多位元組 / 寬字串和字元轉換函式

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中所指定的語意。

## <a name="algorithm-functions"></a>Algorithm 函式

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中所指定的語意。

## <a name="low-quality-random-number-generation-functions"></a>低品質隨機數字產生函式

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>備註

這些函式具有 C 標準程式庫中所指定的語意。

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

這些函式具有 C 標準程式庫中所指定的語意。

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

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
