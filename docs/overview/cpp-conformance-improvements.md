---
title: C++ 一致性改善
ms.date: 08/04/2020
description: Visual Studio 的 Microsoft C++ 正在向完全符合 C++20 語言標準邁進。
ms.technology: cpp-language
ms.openlocfilehash: ea0b871651d1cf0c8719e8d5f22df5ab42e69e14
ms.sourcegitcommit: 68ae6f9ea17f32734b32bb06ffeec12d8d33f0fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87807819"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Visual Studio 中的 C++ 一致性改善

Microsoft C++ 在每個版本中都進行一致性改善和 Bug 修正。 本文依主要版次和版本的順序列出列出改善。 它也依版本列出重大 Bug 修正。 若要直接跳到特定版本的變更，請使用 [本文內容]**** 清單。

::: moniker range="vs-2019"

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a>Visual Studio 2019 RTW (版本16.0 中的一致性改進) 

Visual Studio 2019 RTW 包含下列的一致性改進、bug 修正和 Microsoft c + + 編譯器中的行為變更 (MSVC) 

**注意：** C + + 20 功能會在模式中提供， **`/std:c++latest`** 直到編譯器和 IntelliSense 的 c + + 20 執行完成為止。 此時， **`/std:c++20`** 將會引進編譯器模式。

### <a name="improved-modules-support-for-templates-and-error-detection"></a>改善的範本和錯誤偵測模組支援

模組現已正式使用 C++20 標準。 Visual Studio 2017 15.9 版已新增改善的支援。 如需詳細資訊，請參閱 [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/) (C++ 模組與 MSVC 2017 15.9 版的更佳範本支援和錯誤偵測)。

### <a name="modified-specification-of-aggregate-type"></a>已修改彙總類型的規格

C++20 已變更彙總類型的規格 (請參閱 [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1) (禁止使用使用者宣告的建構函式彙總))。 在 Visual Studio 2019 中，在之下 **`/std:c++latest`** ，具有任何使用者宣告之函式的類別 (例如，包括宣告的 `= default` 或 `= delete`) 的不是匯總。 過去，只有使用者所提供建構函式才可取消讓類別成為彙總的資格。 這項變更會對如何初始化這類類型的方式加諸額外限制。

下列程式碼會在 Visual Studio 2017 中編譯而不會發生錯誤，但會在 Visual Studio 2019 的下引發錯誤 C2280 和 C2440 **`/std:c++latest`** ：

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>部分支援 `operator <=>`

[P0515R3](https://wg21.link/p0515r3) C++20 引入 `<=>` 三向比較運算子，也稱為「太空船運算子」。 模式中的 Visual Studio 2019 **`/std:c++latest`** 會針對目前不允許的語法引發錯誤，藉以引進運算子的部分支援。 例如，下列程式碼會在 Visual Studio 2017 中編譯而不會發生錯誤，但會在 Visual Studio 2019 中引發多個錯誤 **`/std:c++latest`** ：

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

為避免發生錯誤，請在有問題程式行的最後一個角括弧前插入空格：`U<&S::operator<= > u;`。

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>參考具有不相符 cv 限定詞的類型

在過去，MSVC 允許直接從最高層級底下具有不相符 CV 限定詞的類型繫結參考。 此繫節可能允許修改參考應參考的 const 資料。 編譯器現在會如標準所要求建立暫存。 在 Visual Studio 2017 中，下列程式碼在編譯時不會發出警告。 在 Visual Studio 2019 中，編譯器會引發 warning C4172： `<func:#1 "?PData@X@@QBEABQBXXZ"> returning address of local variable or temporary.` ：

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>來自多載函式的 `reinterpret_cast`

的引數 **`reinterpret_cast`** 不是允許多載函式位址的其中一個內容。 下列程式碼會在 Visual Studio 2017 中編譯而不會發生錯誤，但在 Visual Studio 2019 中，它會引發錯誤 C2440： `cannot convert from 'overloaded-function' to 'fp'` ：

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

為避免此錯誤，此案例請使用允許的轉換：

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Lambda 終止

在 C++14 中，Lambda 終止類型不是常值。 此規則的主要結果是 lambda 可能不會指派給 **`constexpr`** 變數。 下列程式碼會在 Visual Studio 2017 中編譯而不會發生錯誤，但在 Visual Studio 2019 中，它會引發錯誤 C2127： `'l': illegal initialization of 'constexpr' entity with a non-constant expression` ：

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

若要避免此錯誤，請移除辨識 **`constexpr`** 符號，否則請將一致性模式變更為 **`/std:c++17`** 。

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory` 失敗碼

已從 C++20 無條件實作 [P1164](https://wg21.link/p1164r1)。 這會變更 `std::create_directory`，檢查目標在發生故障時是否即為目錄。 以前，所有 ERROR_ALREADY_EXISTS 類型錯誤都會轉換成成功但未建立目錄的程式碼。

### `operator<<(std::ostream, nullptr_t)`

依 [LWG 2221](https://cplusplus.github.io/LWG/issue2221)，已新增 `operator<<(std::ostream, nullptr_t)` 將 nullptrs 寫入資料流。

### <a name="additional-parallel-algorithms"></a>其他的平行演算法

新的平行版 `is_sorted`、`is_sorted_until`、`is_partitioned`、`set_difference`、`set_intersection`、`is_heap` 和 `is_heap_until`。

### <a name="atomic-initialization"></a>不可部分完成的初始化

[P0883 "Fixing atomic initialization"](https://wg21.link/p0883r1) (P0883「修正不可部分完成的初始化」) 將 `std::atomic` 變更為初始化包含 T 的值，而不是將它初始化的預設值。 使用 Clang/LLVM 與 Microsoft 標準程式庫時即啟用此修正。 Microsoft c + + 編譯器目前已停用此功能，作為處理中 bug 的因應措施 **`constexpr`** 。

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` 和 `remove_cvref_t`

已從 [P0550](https://wg21.link/p0550r2) 實作 `remove_cvref` 和 `remove_cvref_t` 類型特性。 它們會移除類型中的參考性質和 CV 限定性，但不衰減指標的函式和陣列 (不同於 `std::decay` 和 `std::decay_t`)。

### <a name="feature-test-macros"></a>功能測試巨集

[P0941R2 - 功能測試巨集](https://wg21.link/p0941r2)已完成，並支援 `__has_cpp_attribute`。 所有標準模式都支援功能測試巨集。

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>禁止使用使用者宣告的建構函式彙總

[C++20 P1008R1 - 禁止使用使用者宣告的建構函式彙總](https://wg21.link/p1008r1)已完成。

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a>16.1 中的一致性改善

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6)。 C++20 新增用來表示 UTF-8 字碼單位的新字元類型。 C++20 的 `u8` 字串常值具有類型 `const char8_t[N]` 而非 `const char[N]`，這是舊例。 [N2231](https://wg14.link/n2231) \(英文\) 已針對 C 標準建議類似的變更。 回溯 **`char8_t`** 相容性補救的建議會在[P1423r3](https://wg21.link/p1423r3)中提供。 **`char8_t`** 當您指定編譯器選項時，Microsoft c + + 編譯器會在 Visual Studio 2019 版本16.1 中新增的支援 **`/Zc:char8_t`** 。 在未來，將會支援 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ，它可以透過還原為 c + + 17 行為 **`/Zc:char8_t-`** 。 提供 IntelliSense 的 EDG 編譯器尚未支援它。 您可能會看到真正的僅限 IntelliSense 的錯誤，不會影響實際的編譯。

#### <a name="example"></a>範例

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>std::type_identity metafunction 和 std::identity 函式物件

[P0887R1 type_identity](https://wg21.link/p0887r1)。 已移除淘汰的 `std::identity` 類別範本副檔名，並已經以 C++20 `std::type_identity` metafunction 和 `std::identity` 函式物件取代。 兩者都只能在底下使用 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 。

下列範例會針對 `std::identity` \<type_traits> Visual Studio 2017 中) 定義的 (產生取代警告 C4996：

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

下列範例示範如何使用 `std::identity`) 中定義的新 (\<functional> 搭配新的 `std::type_identity` ：

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>泛型 Lambda 的語法檢查

新的 lambda 處理器會在泛型 lambda 中， [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 或在任何其他語言模式之下，啟用一些符合模式的語法檢查 **`/experimental:newLambdaProcessor`** 。

在 Visual Studio 2017 中，此程式碼會編譯而不發出警告，但在 Visual Studio 2019 中，它會產生錯誤 C2760 `syntax error: unexpected token '\<id-expr>', expected 'id-expression'` ：

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

下列範例示範正確的語法，現由編譯器強制執行：

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>函式呼叫的引數相依查閱

[P0846R0](https://wg21.link/p0846r0) (c + + 20) 透過明確樣板引數的函式呼叫運算式，透過與引數相依的查閱來尋找函式範本的功能。 需要 **`/std:c++latest`** 。

### <a name="designated-initialization"></a>指定的初始化

[P0329R4](https://wg21.link/p0329r4) (c + + 20) *指定的初始化*允許使用語法，在匯總初始化中選取特定成員 `Type t { .member = expr }` 。 需要 **`/std:c++latest`** 。

### <a name="new-and-updated-standard-library-functions-c20"></a>更新的新標準程式庫函式 (C++20)

- 用於 `basic_string` 和 `basic_string_view` 的 `starts_with()` 和 `ends_with()`。
- 關聯容器的 `contains()`。
- `list` 和 `forward_list` 的 `remove()`、`remove_if()` 與 `unique()` 現在會傳回 `size_type`。
- `shift_left()` 與 `shift_right()` 已新增到 \<algorithm>。

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a>16.2 中的一致性改善

### <a name="noexcept-constexpr-functions"></a>`noexcept` `constexpr` 函式

**`constexpr`** 在常數運算式中使用函式時，預設不會再考慮函數 **`noexcept`** 。 這項行為變更來自[CWG 1351](https://wg21.link/cwg1351)的解決方式，而且已在中啟用 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 。 下列範例會在 Visual Studio 2019 16.1 版和更早版本中進行編譯，但會在 Visual Studio 2019 版本16.2 中產生 C2338：

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

若要修正錯誤，請將 **`noexcept`** 運算式新增至函式宣告：

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>具有不同列舉類型的二進位運算式

C + + 20 已淘汰運算元的一般算術轉換，其中：

- 一個運算元是列舉型別，而

- 另一個則是不同的列舉類型或浮點類型。

如需詳細資訊，請參閱[P1120R0](https://wg21.link/p1120r0)。

在 Visual Studio 2019 16.2 版和更新版本中，下列 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 程式碼會在啟用編譯器選項時產生層級4警告：

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

若要避免出現警告，請使用[static_cast](../cpp/static-cast-operator.md)來轉換第二個運算元：

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

當編譯器選項啟用時，在列舉和浮點類型之間使用二元運算現在是警告 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ：

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

若要避免出現警告，請使用[static_cast](../cpp/static-cast-operator.md)來轉換第二個運算元：

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>陣列的相等和關聯式比較

在 c + + 20 ([P1120R0](https://wg21.link/p1120r0)) 中，陣列類型的兩個運算元之間的相等和關聯式比較已被取代。 換句話說，儘管順位和範圍相似性) ，兩個數組 (之間的比較作業現在是一項警告。 從 Visual Studio 2019 16.2 版開始，下列程式碼會產生 C5056： `operator '==': deprecated for array types` [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 啟用編譯器選項時：

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

若要避免這個警告，您可以比較第一個元素的位址：

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

若要判斷兩個數組的內容是否相等，請使用[std：：等於](../standard-library/algorithm-functions.md#equal)函數：

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>在和上定義太空船運算子的效果 `==``!=`

 () 單獨定義的太空船運算子， **`<=>`** 將不再重寫涉及 **`==`** 或的運算式， **`!=`** 除非太空船運算子標示為 **`= default`** ([P1185R2](https://wg21.link/p1185r2)) 。 下列範例會在 Visual Studio 2019 RTW 和16.1 版中進行編譯，但會在 Visual Studio 2019 版本16.2 中產生 C2678：

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

若要避免此錯誤，請定義 operator = =，或將它宣告為預設：

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>標準程式庫改良功能

- \<charconv>`to_chars()`具有固定/科學精確度。  (一般有效位數目前已規劃16.4。 ) 
- [P0020R6](https://wg21.link/p0020r6)：不可部分完成、不可部分完成、不可部分完成 \<float> \<double>\<long double>
- [P0463R1](https://wg21.link/p0463r1)： endian
- [P0482R6](https://wg21.link/p0482r6)： char8_t 的程式庫支援
- [P0600R1](https://wg21.link/p0600r1)： [ \[ Nodiscard]] 適用于 STL，第1部分
- [P0653R2](https://wg21.link/p0653r2)： to_address ( # A1
- [P0754R2](https://wg21.link/p0754r2)：\<version>
- [P0771R1](https://wg21.link/p0771r1)： std：： function 的 move 函數的 noexcept

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a>Visual Studio 2019 16.3 版中的一致性改善

### <a name="stream-extraction-operators-for-char-removed"></a>已移除 char * 的資料流程提取運算子

針對每個[P0487R1](https://wg21.link/p0487r1))  (的字元陣列，已移除和取代了指標到字元的資料流程提取運算子。 WG21 會將已移除的多載視為不安全。 在 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 模式中，下列範例現在會產生 C2679： `binary '>>': no operator found which takes a right-hand operand of type 'char*' (or there is no acceptable conversion)` ：

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

若要避免此錯誤，請使用具有 char [] 變數的抽取運算子：

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>新關鍵字 `requires` 和`concept`

新 **`requires`** 的關鍵字和 **`concept`** 已經加入 Microsoft c + + 編譯器中。 如果您嘗試在模式中使用其中一個做為識別碼 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ，編譯器會引發 C2059： `syntax error` 。

### <a name="constructors-as-type-names-disallowed"></a>不允許型別名稱的函式

在此情況下，編譯器不會再將函式名稱視為插入類別名稱：當它們以限定名稱出現在類別樣板特製化的別名之後。 之前，可將函式當做類型名稱使用，以宣告其他實體。 下列範例現在會產生 C3646： `'TotalDuration': unknown override specifier` ：

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

若要避免此錯誤，請宣告，如下 `TotalDuration` 所示：

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>更嚴格的函式檢查 `extern "C"`

如果函式 **`extern "C"`** 在不同的命名空間中宣告，舊版 Microsoft c + + 編譯器不會檢查宣告是否相容。 從 Visual Studio 2019 16.3 版開始，編譯器會檢查相容性。 在 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 模式中，下列程式碼會產生 C2371 `redefinition; different basic types` 和 C2733 錯誤 `you cannot overload a function with C linkage` ：

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
```

若要避免上述範例中的錯誤，請 **`bool`** `BOOL` 在這兩個宣告中使用，而不是一致的 `f` 。

### <a name="standard-library-improvements"></a>標準程式庫改良功能

非標準標頭 \<stdexcpt.h> 和已 \<typeinfo.h> 移除。 包含它們的程式碼應該改為分別包含標準標頭 \<exception> 和 \<typeinfo> 。

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a>Visual Studio 2019 16.4 版中的一致性改善

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>針對中的合格識別碼，更有效地強制執行兩階段名稱查閱`/permissive-`

兩階段名稱查閱需要讓範本能夠在定義時看到範本主體中使用的非相依名稱。 先前在範本具現化時，可能會發現這類名稱。 這項變更可讓您更輕鬆地在旗標底下的 MSVC 中撰寫可攜且符合規範的程式碼 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 。

在已設定旗標的 Visual Studio 2019 16.4 版中 **`/permissive-`** ，下列範例會產生錯誤，因為在 `N::f` 定義範本時看不到 `f<T>` ：

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

通常，您可以藉由包含遺漏的標頭或向前宣告函式或變數來修正此錯誤，如下列範例所示：

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>整數常數運算式隱含轉換成 null 指標

MSVC 編譯器現在會在一致性模式 () 中執行[CWG 問題 903](https://wg21.link/cwg903) **`/permissive-`** 。 除了整數常值 ' 0 ' ) 為 null 指標常數以外，此規則不允許對整數常數運算式進行隱含轉換 (。 下列範例會在一致性模式下產生 C2440：

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

若要修正錯誤，請使用， **`nullptr`** 而不是 **`false`** 。 仍然允許常值0：

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>整數常數值型別的標準規則

在一致性模式 (由) 啟用時 [`/permissive-`](../build/reference/permissive-standards-conformance.md) ，MSVC 會使用整數常數值型別的標準規則。 十進位常值太大，無法放入 **`signed int`** 先前指定的類型 **`unsigned int`** 。 現在，這類常值會得到下一個最大的 **`signed`** 整數類型 **`long long`** 。 此外，具有的尾碼的常值太大，無法放入類型中 **`signed`** **`unsigned long long`** 。

這種變更可能會產生不同的警告診斷，以及常值的算數運算行為差異。

下列範例顯示 Visual Studio 2019 16.4 版中的新行為。 `i`變數現在是型別 **`unsigned int`** 。 這就是為什麼會引發警告的原因。 變數的高序位位 `j` 會設定為0。

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

下列範例示範如何保留舊的行為，並避免警告和執行時間的行為變更：

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>遮蔽範本參數的函式參數

當函式參數遮蔽範本參數時，MSVC 編譯器現在會引發錯誤：

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

若要修正錯誤，請變更其中一個參數的名稱：

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>使用者提供之類型特性的特製化

在符合標準的*rqmts*子句時，MSVC 編譯器現在會在發現 `type_traits` 命名空間中指定的其中一個範本的使用者定義特製化時，引發錯誤 `std` 。 除非另有指定，否則這類特製化會導致未定義的行為。 下列範例有未定義的行為，因為它違反規則，而 **`static_assert`** 失敗併發生錯誤 C2338。

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

若要避免此錯誤，請定義繼承自慣用的結構，並將其 `type_trait` 特殊化：

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>編譯器提供之比較運算子的變更

當啟用此選項時，MSVC 編譯器現在會針對每個[P1630R1](https://wg21.link/p1630r1)的比較運算子執行下列變更 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ：

`operator==`如果運算式牽涉到不是的傳回型別，則編譯器不會再使用來重寫運算式 **`bool`** 。 下列程式碼現在會產生錯誤 C2088： `'!=': illegal for struct` ：

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

若要避免此錯誤，您必須明確定義所需的運算子：

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

如果編譯器是類似聯集類別的成員，則不會再定義預設的比較運算子。 下列範例現在會產生錯誤 C2120： `'void' illegal with all types` ：

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

若要避免此錯誤，請定義運算子的主體：

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const { ... }
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

如果類別包含參考成員，則編譯器不會再定義預設的比較運算子。 下列程式碼現在會產生錯誤 C2120： `'void' illegal with all types` ：

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

若要避免此錯誤，請定義運算子的主體：

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a>Visual Studio 2019 16.5 版中的一致性改善

### <a name="explicit-specialization-declaration-without-an-initializer-isnt-a-definition"></a>沒有初始化運算式的明確特製化宣告不是定義

在之下 `/permissive-` ，MSVC 現在會強制執行標準規則，而沒有初始化運算式的明確特製化宣告不是定義。 先前，宣告會被視為具有預設初始化運算式的定義。 此效果會在連結階段觀察到，因為根據此行為的程式，現在可能會有無法解析的符號。 這個範例現在會產生錯誤：

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration isn't a definition, and the program won't link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main
at link time.
```

若要解決此問題，請新增初始化運算式：

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>預處理器輸出保留分行符號

在使用或搭配時，實驗性預處理器現在會保留分行符號和空格 **`/P`** **`/E`** **`/experimental:preprocessor`** 。 您可以使用來停用這項變更 **`/d1experimental:preprocessor:oldWhitespace`** 。

假設有此範例來源，

```cpp
#define m()
line m(
) line
```

先前的輸出為 **`/E`** ：

```Output
line line
#line 2
```

的新輸出 **`/E`** 現在是：

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>「匯入」和「模組」關鍵字與內容相關

根據 P1857R1，匯入和模組預處理器指示詞對其語法有額外的限制。 這個範例不會再進行編譯：

```cpp
import // Invalid
m;
```

它會產生下列錯誤訊息：

```Output
error C2146: syntax error: missing ';' before identifier 'm'
```

若要解決此問題，請將匯入保留在同一行：

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>移除 std：： weak_equality 和 std：： strong_equality

P1959R0 的合併需要編譯器移除和類型的行為和參考 `std::weak_equality` `std::strong_equality` 。

此範例中的程式碼不會再進行編譯：

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

此範例現在會導致這些錯誤：

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

若要解決此問題，請將更新為偏好使用內建的關聯式運算子，並取代已移除的類型：

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>TLS 防護變更

先前 Dll 中的執行緒區域變數無法正確初始化。 除了載入 DLL 的執行緒以外，在載入 dll 之前的執行緒上第一次使用之前，它們不會初始化。 現在已更正此瑕疵。 這類 DLL 中的執行緒區域變數會在其第一次在這類執行緒上使用之前，立即初始化。

使用編譯器參數，可能會停用使用執行緒區域變數來測試初始化的這個新行為 **`/Zc:tlsGuards-`** 。 或者，將屬性加入 `[[msvc:no_tls_guard]]` 至特定執行緒區域變數。

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>對已刪除函式的呼叫進行更好的診斷

我們的編譯器更寬鬆先前已刪除函數的呼叫。 例如，如果在範本主體的內容中發生呼叫，我們就不會診斷呼叫。 此外，如果已刪除的函式有多個呼叫實例，我們只會發出一個診斷。 現在，我們會針對每個專案發出診斷。

新行為的其中一個結果可能會產生較小的重大變更：呼叫已刪除函式的程式碼不會收到程式碼產生所需的診斷。 接下來我們要進行診斷。

這個範例會顯示現在會產生錯誤的程式碼：

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

若要解決此問題，請移除對已刪除函數的呼叫：

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="conformance-improvements-in-visual-studio-2019-version-166"></a><a name="improvements_166"></a>Visual Studio 2019 16.6 版中的一致性改善

### <a name="standard-library-streams-reject-insertions-of-mis-encoded-character-types"></a>標準程式庫資料流程拒絕插入誤編碼的字元類型

傳統上，將插入 **`wchar_t`** `std::ostream` ，並將或插入或中 **`char16_t`** **`char32_t`** `std::ostream` `std::wostream` ，輸出其整數值。 插入這些字元類型的指標會輸出指標值。 程式設計人員找不到任何一種直覺。 它們通常會預期標準程式庫會改為轉碼字元或以 null 結束的字元字串，並輸出結果。

C + + 20 提案[P1423R3](https://wg21.link/p1423r3)會針對這些資料流程和字元或字元指標類型的組合，加入已刪除的資料流程插入運算子多載。 在之下，多載 **`/std:c++latest`** 會使這些插入格式不正確，而不是可能以非預期方式進行的行為。 當找到一個時，編譯器會引發錯誤 C2280。 您可以將「escape 影線」巨集定義 `_HAS_STREAM_INSERTION_OPERATORS_DELETED_IN_CXX20` 為， `1` 以還原舊的行為。  (提案也會刪除的資料流程插入運算子 **`char8_t`** 。 我們新增了支援時，我們的標準程式庫會執行類似的多載 **`char8_t`** ，因此，「錯誤」行為從未適用于 **`char8_t`** 。 ) 

這個範例會顯示此變更的行為：

```cpp
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << cw << ' ' << pw << '\n';
    std::cout << c16 << ' ' << p16 << '\n';
    std::cout << c32 << ' ' << p32 << '\n';
    std::wcout << c16 << ' ' << p16 << '\n';
    std::wcout << c32 << ' ' << p32 << '\n';
}
```

程式碼現在會產生下列診斷訊息：

```Output
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,wchar_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char32_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char32_t)': attempting to reference a deleted function
```

您可以藉由將字元類型轉換成 **`unsigned int`** ，或將指標轉成字元類型，以在所有語言模式中達到舊行為的效果 `const void*` ：

```c++
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << (unsigned)cw << ' ' << (const void*)pw << '\n'; // Outputs "120 0052B1C0"
    std::cout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::cout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
    std::wcout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::wcout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
}
```

### <a name="changed-return-type-of-stdpow-for-stdcomplex"></a>已 `std::pow()` 變更的傳回類型`std::complex`

先前，函式樣板之傳回類型的提升規則 MSVC 執行 `std::pow()` 不正確。 例如，先前 `pow(complex<float>, int)` 傳回的 `complex<float>` 。 現在它會正確地傳回 `complex<double>` 。 已針對 Visual Studio 2019 16.6 版中的所有標準模式，無條件地執行修正。

這種變更可能會造成編譯器錯誤。 例如，您先前可以將乘以 `pow(complex<float>, int)` **`float`** 。 因為 `complex<T> operator*` 預期會有相同類型的引數，所以下列範例現在會發出編譯器錯誤 C2676： `binary '*': 'std::complex<double>' does not define this operator or a conversion to a type acceptable to the predefined operator` ：

```cpp
// pow_error.cpp
// compile by using: cl /EHsc /nologo /W4 pow_error.cpp
#include <complex>

int main() {
    std::complex<float> cf(2.0f, 0.0f);
    (void) (std::pow(cf, -1) * 3.0f);
}
```

有許多可能的修正：

- 將被乘數的類型變更 **`float`** 為 **`double`** 。 這個引數可以直接轉換成 `complex<double>` ，以符合所傳回的型別 `pow` 。

- 藉由說，將的結果縮小 `pow` 至 `complex<float>` `complex<float>{pow(ARG, ARG)}` 。 然後您可以繼續乘以 **`float`** 值。

- 傳遞 **`float`** ，而不是 **`int`** `pow` 。 這種作業可能會變慢。

- 在某些情況下，您可以 `pow` 完全避免。 例如， `pow(cf, -1)` 可以由除法取代。

### <a name="switch-related-warnings-for-c"></a>C 的交換器相關警告

從 Visual Studio 2019 16.6 版開始，編譯器會針對編譯為 C 的程式碼，執行一些預先存在的 c + + 警告。下列警告現在會在不同的層級啟用： C4060、C4061、C4062、C4063 範例、C4064、C4065、C4808 和 C4809。 警告 C4065 和 C4060 在 C 中預設為停用。

警告會觸發遺漏的 **`case`** 語句、未定義 **`enum`** 和不正確的 **`bool`** 參數 (也就是包含太多) 的情況。 例如：

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
        default: break; // C4809: switch statement has redundant 'default' label;
                        // all possible 'case' labels are given
    }
}
```

若要修正此程式碼，請移除多餘的 **`default`** 案例：

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
    }
}
```

### <a name="unnamed-classes-in-typedef-declarations"></a>宣告中未命名的類別 `typedef`

從 Visual Studio 2019 16.6 版開始，宣告的行為已 **`typedef`** 限制為符合[P1766R1](https://wg21.link/P1766R1)。 在此更新中，宣告中未命名的類別 **`typedef`** 不能具有以外的任何成員：

- 非靜態資料成員，
- 成員類別，
- 成員列舉，
- 和預設成員初始化運算式。

相同的限制會以遞迴方式套用到每個嵌套的類別。 這項限制的目的是為了確保具有 **`typedef`** 連結名稱之結構的簡單性。 在編譯器取得連結的名稱之前，它們必須很簡單，才不需要任何連結計算 **`typedef`** 。

這項變更會影響編譯器的所有標準模式。 在預設 (**`/std:c++14`**) 和 **`/std:c++17`** 模式中，編譯器會針對不符合規範的程式碼發出警告 C5208。 如果 **`/permissive-`** 指定了，編譯器會發出警告 C5208 作為中的錯誤， **`/std:c++14`** 並在底下發出錯誤 C7626 **`/std:c++17`** 。 當指定時，編譯器會發出不符合規範之程式碼的錯誤 C7626 **`/std:c++latest`** 。

下列範例顯示未命名的結構中已不再允許的結構。 視指定的標準模式而定，會發出 C5208 或 C7626 錯誤或警告：

```cpp
struct B { };
typedef struct : B { // inheriting from 'B'; ill-formed
    void f(); // ill-formed
    static int i; // ill-formed
    struct U {
        void f(); // nested class has non-data member; ill-formed
    };
    int j = 10; // default member initializer; ill-formed
} S;
```

您可以藉由提供未命名的類別名稱來修正上述程式碼：

```cpp
struct B { };
typedef struct S_ : B {
    void f();
    static int i;
    struct U {
        void f();
    };
    int j = 10;
} S;
```

### <a name="default-argument-import-in-ccli"></a>C + +/CLI 中的預設引數匯入

越來越多的 Api 在 .NET Core 中有預設引數。 這就是為什麼我們現在支援 c + +/CLI 中的預設引數匯入 這項變更可能會中斷宣告多個多載的現有程式碼，如下列範例所示：

```cpp
public class R {
    public void Func(string s) {}   // overload 1
    public void Func(string s, string s2 = "") {} // overload 2;
}
```

當此類別匯入 c + +/CLI 時，呼叫其中一個多載會造成錯誤：

```cpp
    (gcnew R)->Func("abc"); // error C2668: 'R::Func' ambiguous call to overloaded function
```

編譯器會發出錯誤 C2668，因為這兩個多載都符合這個引數清單。 在第二個多載中，預設引數會填入第二個引數。 若要解決這個問題，您可以 (1) 刪除多餘的多載。 或者，使用完整引數清單，並明確提供預設引數。

## <a name="conformance-improvements-in-visual-studio-2019-version-167"></a><a name="improvements_167"></a>Visual Studio 2019 16.7 版中的一致性改善

### <a name="definition-of-is-trivially-copyable"></a>的定義*為完整可複製*

C + + 20 已變更的定義*為完整可複製*。 當類別具有具有限定類型的非靜態資料成員時 **`volatile`** ，不會再暗示任何編譯器產生的複製或移動程式或複製或移動指派運算子都是不常用的。 C + + 標準委員會將此變更追溯套用為瑕疵報告。 在 MSVC 中，編譯器行為不會在不同的語言模式中變更，例如 **`/std:c++14`** 或 **`/std:c++latest`** 。

以下是新行為的範例：

```cpp
#include <type_traits>

struct S
{
    volatile int m;
};

static_assert(std::is_trivially_copyable_v<S>, "Meow!");
```

在 Visual Studio 2019 16.7 版之前，此程式碼不會在 MSVC 版本中編譯。 您可以使用預設的編譯器警告來偵測這項變更。 如果您使用來編譯上述程式碼 **`cl /W4 /w45220`** ，您會看到下列警告：

警告 C5220：`'S::m': a non-static data member with a volatile qualified type no longer implies that compiler generated copy/move constructors and copy/move assignment operators are non trivial`

### <a name="pointer-to-member-and-string-literal-conversions-to-bool-are-narrowing"></a>要縮小的成員指標和字串常值轉換 `bool`

C + + 標準委員會最近採用了「瑕疵報告[P1957R2](https://wg21.link/p1957r2)，其視為 `T*`  ->  **`bool`** 縮小轉換。 MSVC 已修正其執行中的 bug，其先前會診斷 `T*`  ->  **`bool`** 為縮小，但不會診斷字串常值轉換為 **`bool`** 或成員指標至的問題 **`bool`** 。

下列程式在 Visual Studio 2019 版本16.7 中格式不正確：

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" }); // error: conversion from 'const char [8]' to 'bool' requires a narrowing conversion

    int (X::* p) = nullptr;
    f(X { p }); // error: conversion from 'int X::*' to 'bool' requires a narrowing conversion
}
```

若要更正這個程式碼，請加入明確的比較 **`nullptr`** ，或避免縮小轉換格式不正確的內容：

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" != nullptr }); // Absurd, but OK

    int (X::* p) = nullptr;
    f(X { p != nullptr }); // OK
}
```

### <a name="nullptr_t-is-only-convertible-to-bool-as-a-direct-initialization"></a>`nullptr_t`只能轉換成 `bool` 直接初始化

在 c + + 11 中， **`nullptr`** 只能轉換成 **`bool`** *直接轉換*; 例如，當您 **`bool`** 使用括弧初始化運算式-list 來初始化時。 MSVC 絕對不會強制執行這項限制。 MSVC 現在會在下執行規則 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 。 隱含轉換現在已被診斷成格式不正確的。 **`bool`** 仍然允許內容上的轉換，因為直接初始化 `bool b(nullptr)` 是有效的。

在大部分的情況下，您可以將取代為來修正錯誤 **`nullptr`** **`false`** ，如下列範例所示：

```cpp
struct S { bool b; };
void g(bool);
bool h() { return nullptr; } // error, should be 'return false;'

int main() {
    bool b1 = nullptr; // error: cannot convert from 'nullptr' to 'bool'
    S s { nullptr }; // error: cannot convert from 'nullptr' to 'bool'
    g(nullptr); // error: cannot convert argument 1 from 'nullptr' to 'bool'

    bool b2 { nullptr }; // OK: Direct-initialization
    if (!nullptr) {} // OK: Contextual conversion to bool
}
```

### <a name="conforming-initialization-behavior-for-array-initializations-with-missing-initializers"></a>符合具有遺漏初始化運算式之陣列初始化的初始設定行為

先前，MSVC 對於缺少初始化運算式的陣列初始化具有不一致的行為。 MSVC 一律會針對沒有初始化運算式的每個陣列元素，呼叫預設的函式。 標準行為是使用空的括弧初始化運算式-list () 來初始化每個元素 **`{}`** 。 空的括弧初始化運算式清單的初始化內容是複製初始化，這不允許呼叫明確的函式。 也可能會有執行時間差異，因為使用 `{}` 來初始化可能會呼叫接受的函式 `std::initializer_list` ，而不是預設的函式。 在下啟用符合規範的行為 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 。

以下是已變更行為的範例：

```cpp
struct B {
    explicit B() {}
};

void f() {
    B b1[1]{}; // Error in /permissive-, because aggregate init calls explicit ctor
    B b2[1]; // OK: calls default ctor for each array element
}
```

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a><a name="update_160"></a>Visual Studio 2019 中的 Bug 修正和行為變更

### <a name="reinterpret_cast-in-a-constexpr-function"></a>`reinterpret_cast`在函式中 `constexpr`

在函式 **`reinterpret_cast`** 中是不合法的 **`constexpr`** 。 Microsoft c + + 編譯器先前 **`reinterpret_cast`** 只有在內容中使用時，才會拒絕 **`constexpr`** 。 在 Visual Studio 2019 中，在所有語言標準模式中，編譯器會正確地在函式 **`reinterpret_cast`** 的定義中診斷 **`constexpr`** 。 下列程式碼現在會產生 C3615： `constexpr function 'f' cannot result in a constant expression` 。

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

若要避免此錯誤，請 **`constexpr`** 從函式宣告中移除修飾詞。

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>basic_string 範圍建構函式的正確診斷

在 Visual Studio 2019 中，範圍的函式 `basic_string` 不會再使用來隱藏編譯器診斷 **`static_cast`** 。 下列程式碼會在 Visual Studio 2017 中編譯而不發出警告，即使在初始化時可能會遺失的資料 **`wchar_t`** **`char`** `out` ：

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 正確地引發警告 C4244： `'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data` 。 為避免此警告，您可以初始化 std::string，如此範例所示：

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>`+=` `-=` `/clr` `/ZW` 現在已正確偵測到和底下的呼叫不正確

在 Visual Studio 2017 中引進 bug，這會導致編譯器以無訊息方式忽略錯誤，並不會針對在或之下的無效呼叫產生任何程式碼 **`+=`** **`-=`** **`/clr`** **`/ZW`** 。 下列程式碼會在 Visual Studio 2017 中編譯而不會發生錯誤，但在 Visual Studio 2019 中，它會正確引發錯誤 C2845： `'System::String ^': pointer arithmetic not allowed on this type` ：

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

若要避免在此範例中發生錯誤，請搭配使用 **`+=`** 運算子與 `ToString()` 方法： `s += E::e.ToString();` 。

### <a name="initializers-for-inline-static-data-members"></a>內嵌靜態資料成員的初始設定式

**`inline`** 現在會正確偵測到和初始化運算式中的成員存取無效 **`static constexpr`** 。 下列範例會在 Visual Studio 2017 中編譯而不會發生錯誤，但在模式下的 Visual Studio 2019 中， **`/std:c++17`** 它會引發錯誤 C2248： `cannot access private member declared in class 'X'` 。

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

為避免此錯誤，請將成員 `X::c` 宣告為受保護：

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>已重新啟用 C4800

MSVC 用來提供有關隱含轉換成的效能警告 C4800 **`bool`** 。 它太過雜訊且無法隱藏，因此我們在 Visual Studio 2017 中將其移除。 不過，Visual Studio 2017 在生命週期中獲得許多有助於解決案例問題的意見反應。 我們在 Visual Studio 2019 中重新加入，仔細設計的 C4800，以及說明性的 C4165。 這兩個警告都很容易隱藏：使用明確轉換，或與適當類型的0比較。 C4800 為預設關閉的層級 4 警告，C4165 是預設關閉的層級 3 警告。 這兩種方法都可以使用 **`/Wall`** 編譯器選項來探索。

下列範例會在底下引發 C4800 和 C4165 **`/Wall`** ：

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

為避免上例中的警告，您可以撰寫如下的程式碼：

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>區域類別成員函式沒有主體

在 Visual Studio 2017 中， `Local class member function doesn't have a body` 只有明確設定編譯器選項時，才會引發警告 C4822： **`/w14822`** 。 它不會顯示在 **`/Wall`** 中。 在 Visual Studio 2019 中，C4822 是預設的關閉警告，讓它可在下探索， **`/Wall`** 而不需要 **`/w14822`** 明確設定。

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-if-constexpr-statements"></a>包含語句的函式樣板主體 `if constexpr`

包含 **`if constexpr`** 語句的樣板函式主體會 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 啟用一些剖析相關的檢查。 例如，在 Visual Studio 2017 中，下列程式碼會產生 C7510： `'Type': use of dependent type name must be prefixed with 'typename'` 只有在 **`/permissive-`** 未設定選項時。 在 Visual Studio 2019 中，即使設定了選項，相同的程式碼也會引發錯誤 **`/permissive-`** ：

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

若要避免此錯誤，請將 **`typename`** 關鍵字新增至的宣告 `a` ： `typename T::Type a;` 。

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Lambda 運算式不支援內嵌組譯碼

Microsoft c + + 小組最近發現在 lambda 中使用內嵌組譯工具的安全性問題，可能會導致在執行時間 (傳回位址暫存器) 的損毀 `ebp` 。 惡意攻擊者可能利用這種情況。 內嵌組譯工具僅適用于 x86，而內嵌組譯工具與編譯器其餘部分之間的互動則不佳。 基於這些事實和問題的本質，此問題最安全的解決方法，就是不允許在 lambda 運算式內使用內嵌組譯工具。

我們所見唯一會在 Lambda 運算式內使用內嵌組譯工具的實際情況，是擷取傳回位址。 在此案例中，您可以擷取所有平台的寄件地址，只要使用編譯器內建 `_ReturnAddress()` 即可。

下列程式碼會產生 C7552： `inline assembler is not supported in a lambda` 在 Visual Studio 2017 15.9 和 Visual Studio 2019 中：

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

為避免此錯誤，請將組譯碼移入具名函式，如下列範例所示：

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>迭代器偵錯和 `std::move_iterator`

已教授迭代器偵錯功能正確解除包裝 `std::move_iterator`。 例如，`std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` 現可投入 `memcpy` 快速路徑。

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>\<xkeycheck.h>關鍵字強制的修正

已修正標準程式庫在 \<xkeycheck.h> for 宏取代關鍵字中的強制執行。 程式庫現在會發出偵測到的實際問題關鍵字，而不是一般訊息。 它也支援 C++20 的關鍵字，可避免誘騙 IntelliSense 說出隨機的巨集關鍵字。

### <a name="allocator-types-no-longer-deprecated"></a>配置器類型不再予以淘汰

`std::allocator<void>`、`std::allocator::size_type` 和 `std::allocator::difference_type` 不再予以淘汰。

### <a name="correct-warning-for-narrowing-string-conversions"></a>更正縮小字串轉換的警告

已 **`static_cast`** 從中移除未 `std::string` 針對標準所呼叫的偽，而且不小心隱藏了 C4244 縮小警告。 現在嘗試呼叫會 `std::string::string(const wchar_t*, const wchar_t*)` 正確發出 C4244 `narrowing a wchar_t into a char` 。

### <a name="various-fixes-for-filesystem-correctness"></a>各種正確性修正 \<filesystem>

- 已修正 `std::filesystem::last_write_time` 嘗試變更目錄的上次寫入時間時失敗的問題。
- 提供不存在的目標路徑時，`std::filesystem::directory_entry` 建構函式現在會儲存失敗的結果，而不是擲回例外狀況。
- `std::filesystem::create_directory` 的 2 個參數版本已變更為呼叫 1 個參數版本，因為當 `existing_p` 為符號連結時，基礎 `CreateDirectoryExW` 函式會使用 `copy_symlink`。
- 當發現符號連結中斷時，`std::filesystem::directory_iterator` 不會再失敗。
- `std::filesystem::space` 現在接受相對路徑。
- `std::filesystem::path::lexically_relative` 不再為句尾斜線困惑，回報為 [LWG 3096](https://cplusplus.github.io/LWG/issue3096)。
- 因應措施為 `CreateSymbolicLinkW` 拒絕在 `std::filesystem::create_symlink` 中有正斜線的路徑。
- 解決了 `delete` 存在於 Windows 10 LTSB 1609 中的 POSIX 刪除模式功能，但無法實際刪除檔案。
- `std::boyer_moore_searcher` 和 `std::boyer_moore_horspool_searcher` 的複製建構函式和複製指派運算子現都可實際複製項目。

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Windows 8 和更新版本中的平行演算法

平行演算法程式庫現可正確使用 Windows 8 和更新版本的真實 `WaitOnAddress` 系列，而不是一律使用 Windows 7 和舊版的假版本。

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()` 空白字元

`std::system_category::message()` 現在會修剪傳回訊息的尾端空格。

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine` 除以零

已修正會導致 `std::linear_congruential_engine` 觸發除以 0 的一些情況。

### <a name="fixes-for-iterator-unwrapping"></a>修正迭代器解除包裝

某些反覆運算器解除包裝的機械會先公開，以供 Visual Studio 2017 15.8 中的程式設計人員使用者整合。 本主題已在[VS 2017 15.8 中的 STL 功能和修正程式](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/)中說明。 此機制不再解除包裝衍生自標準程式庫反覆運算器的反覆運算器。 例如，衍生自 `std::vector<int>::iterator` 的使用者和嘗試自訂行為的使用者，現在都可在呼叫標準程式庫演算法時試取得其自訂的行為，而不是指標的行為。

未排序的容器 `reserve` 函式現在實際上都會保留以供 N 個元素使用，如 [LWG 2156](https://cplusplus.github.io/LWG/issue2156) \(英文\) 中所述。

### <a name="time-handling"></a>時間處理

- 過去，某些已傳遞給並行程式庫的時間值會溢位，例如 `condition_variable::wait_for(seconds::max())`。 現已修正，溢位過去似乎會以隨機的 29 日循環變更行為 (當基礎 Win32 API 接受的 uint32_t 毫秒溢位時)。

- \<ctime>標頭現在會 `timespec` 在命名空間中正確宣告和 `timespec_get` `std` ，而且也會在全域命名空間中宣告它們。

### <a name="various-fixes-for-containers"></a>容器的各種修正

- 許多標準程式庫的內部容器函式都已成為私用，以改善 IntelliSense 體驗。 MSVC 的較新版本預計會提供可將成員標記為私用的其他修正。

- 已修正 `list`、`map` 和 `unordered_map` 等節點型容器可能損毀的例外狀況安全正確性問題。 在 `propagate_on_container_copy_assignment` 或 `propagate_on_container_move_assignment` 重新指派作業期間，我們會使用舊的配置器來釋放容器的 sentinel 節點、透過舊的配置器執行 POCCA/pocma non-equal-allocator 案例指派，然後嘗試從新的配置器取得 sentinel 節點。 如果此配置失敗，則容器已損毀。 它甚至無法終結，因為擁有 sentinel 節點是一種不變的硬資料結構。 已修正此程式碼，以在終結現有的 sentinel 節點之前，使用來源容器的配置器來建立新的 sentinel 節點。

- 容器已修正為根據 `propagate_on_container_copy_assignment`、`propagate_on_container_move_assignment` 和 `propagate_on_container_swap`，甚至針對配置器宣告的 `is_always_equal` 來一律複製/移動/分頁配置器。

- 已新增可接受右值容器之容器合併和解壓縮成員函式的多載。 如需詳細資訊，請參閱[P0083 「接合對應和設定](https://wg21.link/p0083r3)」。

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read``\r\n`` => `\n ' 的處理

`std::basic_istream::read`已修正為不會在處理過程中暫時寫入提供的緩衝區部分 `\r\n`  =>  `\n` 。 此變更放棄 Visual Studio 2017 15.8 中大小大於 4K 之讀取的效能優勢。 不過，避免每個字元三次虛擬呼叫的效率改善仍存在。

### <a name="stdbitset-constructor"></a>`std::bitset` 建構函式

`std::bitset` 建構函式不會再反向讀取大型位元集的一和零。

### <a name="stdpairoperator-regression"></a>`std::pair::operator=` 迴歸

已修正實作 [LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729) 時，`std::pair` 指派運算子導入的迴歸。 它現在可以再次正確接受可轉換為 `std::pair` 的類型。

### <a name="non-deduced-contexts-for-add_const_t"></a>`add_const_t` 的非推算內容

已修正 `add_const_t` 和相關函式本該是非推算內容的次要類型特性 Bug。 換言之，`add_const_t` 應該是 `typename add_const<T>::type` 的別名，而非 `const T` 的別名。

## <a name="bug-fixes-and-behavior-changes-in-162"></a><a name="update_162"></a>16.2 中的 Bug 修正和行為變更

### <a name="const-comparators-for-associative-containers"></a>關聯容器的 Const 比較子

已合併[set](../standard-library/set-class.md)、 [map](../standard-library/map-class.md)、[多重集](../standard-library/multiset-class.md)和[multimap](../standard-library/multimap-class.md)中的搜尋和插入程式碼，以減少程式碼大小。 插入作業現在會 **`const`** 以與先前完成搜尋作業相同的方式，呼叫比較仿函數的小於比較。 下列程式碼會在 Visual Studio 2019 16.1 版和更早版本中進行編譯，但會在 Visual Studio 2019 版本16.2 中引發 C3848：

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

若要避免此錯誤，請進行比較運算子 **`const`** ：

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-version-167"></a><a name="updates_167"></a>Visual Studio 2019 16.7 版中的 Bug 修正和行為變更

### <a name="initialization-of-class-members-with-overloaded-names-is-correctly-sequenced"></a>已正確排序具有多載名稱之類別成員的初始化

當類型名稱也多載為資料成員的名稱時，我們發現類別資料成員內部標記法中的 bug。 此錯誤會導致匯總初始化和成員初始化順序不一致。 產生的初始化程式碼現在是正確的。 不過，這項變更可能會導致來源中不慎依賴錯誤排序成員的錯誤或警告，如下列範例所示：

```cpp
// Compiling with /w15038 now gives:
// warning C5038: data member 'Outer::Inner' will be initialized after data member 'Outer::v'
struct Outer {
    Outer(int i, int j) : Inner{ i }, v{ j } {}

    struct Inner { int x; };
    int v;
    Inner Inner; // 'Inner' is both a type name and data member name in the same scope
};
```

在舊版中，此函式會在資料成員之前，不正確地初始化資料成員 `Inner` `v` 。  (c + + 標準需要與成員) 的宣告順序相同的初始化順序。 現在，已產生的程式碼遵循標準，成員 init 清單則不會順序。 編譯器會產生此範例的警告。 若要修正此問題，請重新排列成員初始化運算式清單，以反映宣告順序。

### <a name="overload-resolution-involving-integral-overloads-and-long-arguments"></a>涉及整數多載和引數的多載解析 `long`

C + + 標準需要排名 a **`long`** 以 **`int`** 轉換成標準轉換。 先前的 MSVC 編譯器不正確地將其次序為整數提升，而將其順位為多載解析的高階。 當此次序應視為不明確時，可能會導致多載解析成功解析。

編譯器現在會在模式中正確地考慮次序 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 。 正確診斷不正確程式碼，如下列範例所示：

```cpp
void f(long long);
void f(int);

int main() {
    long x {};
    f(x); // error: 'f': ambiguous call to overloaded function
    f(static_cast<int>(x)); // OK
}
```

您可以透過數種方式來修正此問題：

- 在呼叫位置，將傳遞之引數的類型變更為 **`int`** 。 您可以變更變數類型，或將它轉換。

- 如果有許多呼叫網站，您可以加入另一個接受引數的多載 **`long`** 。 在此函式中，將引數轉型並轉送至多載 **`int`** 。

### <a name="use-of-undefined-variable-with-internal-linkage"></a>使用未定義的變數搭配內部連結

Visual Studio 2019 16.7 版之前的 MSVC 版本，可接受使用已宣告 **`extern`** 且未定義內部連結的變數。 這類變數無法在任何其他轉譯單位中定義，也不能形成有效的程式。 編譯器現在會在編譯時期診斷這種情況。 此錯誤與未定義的靜態函式的錯誤類似。

```cpp
namespace {
    extern int x; // Not a definition, but has internal linkage because of the anonymous namespace
}

int main()
{
    return x; // Use of 'x' that no other translation unit can possibly define.
}
```

此程式先前已不正確地進行編譯和連結，但現在會發出：

錯誤 C7631：`'anonymous-namespace'::x': variable with internal linkage declared but not defined`

這類變數必須在所用的相同轉譯單位中定義。 例如，您可以提供明確的初始化運算式或個別的定義。

### <a name="type-completeness-and-derived-to-base-pointer-conversions"></a>類型完整性和衍生到基底指標轉換

在 c + + 20 之前的 c + + 標準中，從衍生類別到基類的轉換不需要衍生的類別是完整的類別類型。 C + + 標準委員會已核准適用于所有 c + + 語言版本的追溯瑕疵報告變更。 這種變更會將轉換程式與類型特性（例如 `std::is_base_of` ）對齊，這需要衍生的類別是完整的類別類型。

以下為範例：

```cpp
template<typename A, typename B>
struct check_derived_from
{
    static A a;
    static constexpr B* p = &a;
};

struct W { };
struct X { };
struct Y { };

// With this change this code will fail as Z1 is not a complete class type
struct Z1 : X, check_derived_from<Z1, X>
{
};

// This code failed before and it will still fail after this change
struct Z2 : check_derived_from<Z2, Y>, Y
{
};

// With this change this code will fail as Z3 is not a complete class type
struct Z3 : W
{
    check_derived_from<Z3, W> cdf;
};
```

這項行為變更適用于 MSVC 的所有 c + + 語言模式，而不只是 **`/std:c++latest`** 。

### <a name="narrowing-conversions-are-more-consistently-diagnosed"></a>更一致地診斷縮小轉換

MSVC 會在括弧清單初始化運算式中發出縮小轉換的警告。 先前，編譯器不會從較大的基礎類型診斷縮小轉換 **`enum`** 成更窄的整數類資料類型。  (編譯器不正確地將其視為整數提升，而不是轉換) 。 如果是刻意進行的縮小轉換，您可以 **`static_cast`** 在初始化運算式引數上使用，以避免出現警告。 或者，選擇較大的目的地整數類資料類型。

以下是使用明確的 **`static_cast`** 來處理警告的範例：

```cpp
enum E : long long { e1 };
struct S { int i; };

void f(E e) {
    S s = { e }; // warning: conversion from 'E' to 'int' requires a narrowing conversion
    S s1 = { static_cast<int>(e) }; // Suppress warning with explicit conversion
}
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a>Visual Studio 2017 RTW (版本15.0 中的一致性改進) 

有了一般化 **`constexpr`** 和非靜態資料成員初始化的支援 (NSDMI) 進行匯總，現在 Visual Studio 2017 中的 Microsoft c + + 編譯器已針對 c + + 14 標準中新增的功能完成。 不過，編譯器仍缺乏一些來自 C++11 和 C++98 標準的功能。 如需顯示編譯器目前狀態的資料表，請參閱[Microsoft c + + 語言一致性表格](../visual-cpp-language-conformance.md)。

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C + + 11：更多程式庫中的 Expression SFINAE 支援

編譯器會繼續改善其對 expression SFINAE 的支援。 這是範本引數推算和替代的必要條件，其中 **`decltype`** 和 **`constexpr`** 運算式可能會顯示為範本參數。 如需詳細資訊，請參閱 [Expression SFINAE improvements in Visual Studio 2017 RC](https://devblogs.microsoft.com/cppblog/expression-sfinae-improvements-in-vs-2015-update-3/) (Visual Studio 2017 RC 中的運算式 SFINAE 增強功能)。

### <a name="c14-nsdmi-for-aggregates"></a>C + + 14：匯總的 NSDMI

匯總是陣列或類別，其具有：沒有使用者提供的函式、沒有私用或受保護的非靜態資料成員、沒有基類，且沒有虛擬函式。 從 c + + 14 開始，匯總可能會包含成員初始化運算式。 如需詳細資訊，請參閱 [Member initializers and aggregates](https://wg21.link/n3605) (成員初始設定式和彙總)。

### <a name="c14-extended-constexpr"></a>C + + 14： Extended`constexpr`

**`constexpr`** 宣告為的運算式現在允許包含特定類型的宣告、if 和 switch 語句、loop 語句，以及存留期開始于運算式評估內的物件變化 **`constexpr`** 。 您不再需要以隱含的方式來使用 **`constexpr`** 非靜態成員函式 **`const`** 。 如需詳細資訊，請參閱[ `constexpr` 函數的放寬條件約束](https://wg21.link/n3652)。

### <a name="c17-terse-static_assert"></a>C + + 17：簡易`static_assert`

的 message 參數 **`static_assert`** 是選擇性的。 如需詳細資訊，請參閱 [Extending static_assert, v2](https://wg21.link/n3928) (擴充 static_assert v2)。

### <a name="c17-fallthrough-attribute"></a>C++17：`[[fallthrough]]` 屬性

在 **`/std:c++17`** 模式中， `[[fallthrough]]` 可以在 switch 語句的內容中使用屬性，做為編譯器的提示，而這是預期的迴圈行為。 此屬性可避免編譯器發出警告。 如需詳細資訊，請參閱[ `[[fallthrough]]` 屬性的用語](https://wg21.link/p0188r0)。

### <a name="generalized-range-based-for-loops"></a>通用的範圍架構 for 迴圈

範圍式 for 迴圈不再需要 `begin()` 和 `end()` 傳回相同類型的物件。 此變更可讓 `end()` 傳回 [range-v3](https://github.com/ericniebler/range-v3) 中範圍所使用的 sentinel，以及已完成但尚未發行的「範圍技術規格」。 如需詳細資訊，請參閱[一般化以範圍為基礎的 `for` 迴圈](https://wg21.link/p0184r0)。

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a>15.3 中的一致性改善

### <a name="constexpr-lambdas"></a>`constexpr`lambda

Lambda 運算式現在可用於常數運算式。 如需詳細資訊，請參閱[ `constexpr` c + + 中的 lambda 運算式](../cpp/lambda-expressions-constexpr.md)。

### <a name="if-constexpr-in-function-templates"></a>函式範本中的 `if constexpr`

函式樣板可能會包含 **`if constexpr`** 語句，以啟用編譯時間分支。 如需詳細資訊，請參閱[ `if constexpr` 語句](../cpp/if-else-statement-cpp.md#if_constexpr)。

### <a name="selection-statements-with-initializers"></a>使用初始設定式的選取範圍陳述式

**`if`** 語句可能包含在語句本身的區塊範圍中引進變數的初始化運算式。 如需詳細資訊，請參閱[ `if` 具有初始化運算式的語句](../cpp/if-else-statement-cpp.md#if_with_init)。

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]` 與 `[[nodiscard]]` 屬性

當未使用實體時，新屬性 `[[maybe_unused]]` 會關閉警號。 如果捨棄函式呼叫的傳回值，`[[nodiscard]]` 屬性會建立警告。 如需詳細資訊，請參閱 [C++ 中的屬性](../cpp/attributes.md)。

### <a name="using-attribute-namespaces-without-repetition"></a>不重複使用屬性命名空間

新的語法讓您在屬性清單中可只用單一命名空間識別項。 如需詳細資訊，請參閱 [C++ 中的屬性](../cpp/attributes.md)。

### <a name="structured-bindings"></a>結構化繫結

現在可以在單一宣告中以值元件的個別名稱儲存值，前提是該值必須為陣列、`std::tuple` 或 `std::pair`，或具有公用非靜態資料成員。 如需詳細資訊，請參閱[結構化繫結](https://wg21.link/p0144r0)與[從函式傳回多重值](../cpp/functions-cpp.md#multi_val)。

### <a name="construction-rules-for-enum-class-values"></a>`enum class` 值的建構規則

現在有一個隱含轉換，適用于未縮小範圍的列舉。 它會從範圍列舉的基礎類型轉換成列舉本身。 當其定義未引進枚舉器，且來源使用清單初始化語法時，就可以使用轉換。 如需詳細資訊，請參閱[列舉類別值的建構規則](https://wg21.link/p0138r2)與 [Enumerations](../cpp/enumerations-cpp.md#no_enumerators)。

### <a name="capturing-this-by-value"></a>以值擷取 `*this`

**`*this`** Lambda 運算式中的物件現在可以藉由值來捕捉。 此變更可用在平行及非同步作業中叫用 Lambda 的案例，特別是在較新的電腦架構上。 如需詳細資訊，請參閱[ \* 以值做為 \[ = \* \] 的 Lambda 捕捉](https://wg21.link/p0018r3)。

### <a name="removing-operator-for-bool"></a>移除 `bool` 的 `operator++`

`operator++`類型已不再支援 **`bool`** 。 如需詳細資訊，請參閱[移除已取代的 operator++ (bool)](https://wg21.link/p0002r1) \(英文\)。

### <a name="removing-deprecated-register-keyword"></a>移除已淘汰的 `register` 關鍵字

先前已被 **`register`** 取代的關鍵字 (並已由編譯器) 忽略，現在已從語言中移除。 如需詳細資訊，請參閱移除已被[取代的 `register` 關鍵字使用](https://wg21.link/p0001r1)。

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a>15.5 中的一致性改善

標記為14的功能可以 \[ 無條件地在模式中使用 **`/std:c++14`** 。

### <a name="new-compiler-switch-for-extern-constexpr"></a>`extern constexpr` 的新編譯器參數

在舊版的 Visual Studio 中，編譯器一律會為 **`constexpr`** 變數提供內部連結，即使變數已標記也一樣 **`extern`** 。 在 Visual Studio 2017 15.5 版中，新的編譯器參數會 [`/Zc:externConstexpr`](../build/reference/zc-externconstexpr.md) 啟用正確且符合標準的行為。 如需詳細資訊，請參閱 [extern constexpr 連結](#extern_linkage)。

### <a name="removing-dynamic-exception-specifications"></a>移除動態例外狀況規格

[P0003R5](https://wg21.link/p0003r5) 動態例外狀況規格在 C++11 中已淘汰。 此功能已從 C++17 中移除，但已被取代的 `throw()` 規格仍會嚴格保留作為 `noexcept(true)` 的別名。 如需詳細資訊，請參閱[動態例外狀況規格移除和 noexcept](#noexcept_removal)。

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` 已取代 `not1` 和 `not2`。

### <a name="rewording-enable_shared_from_this"></a>重寫 `enable_shared_from_this`

[P0033R1](https://wg21.link/p0033r1) `enable_shared_from_this` 已新增於 C++11。 此 C++17 標準會更新規格，以更妥善處理某些極端的案例。 \[14

### <a name="splicing-maps-and-sets"></a>接合地圖與集合

[P0083R3](https://wg21.link/p0083r3)這項功能可讓您從關聯容器中提取節點 (也就是、 `map` `set` 、 `unordered_map`) ， `unordered_set` 然後可以修改並插回相同的容器，或使用相同節點類型的不同容器。 (常見的使用案例是從 `std::map` 擷取節點，再變更金鑰，然後重新插入。)

### <a name="deprecating-vestigial-library-parts"></a>淘汰不必要的程式庫組件

[P0174R2](https://wg21.link/p0174r2) C++ 標準程式庫有幾項功能多年來逐漸被較新的功能所取代，或是發現不實用或有問題。 這些功能在 C++17 中已正式被取代。

### <a name="removing-allocator-support-in-stdfunction"></a>移除 `std::function` 中的配置器支援

[P0302R1](https://wg21.link/p0302r1)在 c + + 17 之前，類別樣板 `std::function` 有數個接受配置器引數的函式。 不過，在此內容中使用配置器會有問題，而且語意不清。 已移除有問題的建構函式。

### <a name="fixes-for-not_fn"></a>`not_fn()` 的修正

[P0358R1](https://wg21.link/p0358r1)`std::not_fn` 的新寫法支援在用於包裝函式引動過程時傳播值類別。

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) 將程式庫基本概念中的 `shared_ptr` 變更合併到 C++17。 \[14

### <a name="fixing-shared_ptr-for-arrays"></a>修正陣列的 `shared_ptr`

[P0497R0](https://wg21.link/p0497r0) 修正陣列的 shared_ptr 支援。 \[14

### <a name="clarifying-insert_return_type"></a>釐清 `insert_return_type`

[P0508R0](https://wg21.link/p0508r0) 具有唯一金鑰的關聯容器和具有唯一金鑰的未排序容器包含傳回巢狀型別 `insert_return_type` 的成員函式 `insert`。 該傳回型別現在已定義為在容器的 Iterator 和 NodeType 上參數化的類型特製化。

### <a name="inline-variables-for-the-standard-library"></a>標準程式庫的內嵌變數

[P0607R0](https://wg21.link/p0607r0)

### <a name="annex-d-features-deprecated"></a>附錄 D 已淘汰的功能

C++ 標準的附錄 D 包含已淘汰的所有功能，包括 `shared_ptr::unique()`、`<codecvt>` 和 `namespace std::tr1`。 **`/std:c++17`** 設定編譯器參數時，附錄 D 中幾乎所有的標準程式庫功能都會標記為已被取代。 如需詳細資訊，請參閱[附錄 D 中的標準程式庫功能標記為已被取代](#annex_d)。

`std::tr2::sys`中的命名空間 `<experimental/filesystem>` 現在預設會在底下發出取代警告 **`/std:c++14`** ，而且預設會在底下移除 **`/std:c++17`** 。

藉由避免使用非標準的延伸模組 (類別內明確特製化) 來改善 `<iostream>` 中的一致性。

標準程式庫現在會於內部使用變數樣板。

標準程式庫已更新，以回應 c + + 17 編譯器變更。 更新包括 **`noexcept`** 在型別系統中新增，以及移除動態例外狀況規格。

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a>15.6 中的一致性改善

### <a name="c17-library-fundamentals-v1"></a>C++17 程式庫基本概念 V1

[P0220R1](https://wg21.link/p0220r1) 將 C++17 的程式庫基本技術規格合併至標準。 涵蓋 \<experimental/tuple> 、 \<experimental/optional> 、 \<experimental/functional> 、 \<experimental/any> 、、、 \<experimental/string_view> \<experimental/memory> \<experimental/memory_resource> 和 \<experimental/algorithm> 的更新。

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C + + 17：改善標準程式庫的類別樣板引數推斷

[P0739R0](https://wg21.link/p0739r0) 將 `adopt_lock_t` 移至參數清單前，使 `scoped_lock` 能夠一致使用 `scoped_lock`。 允許 `std::variant` 建構函式在更多案例中參與多載解析，以啟用複製指派。

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a>15.7 中的一致性改善

### <a name="c17-rewording-inheriting-constructors"></a>C + + 17：改寫繼承的函式

[P0136R1](https://wg21.link/p0136r1)指定名稱為「函式」的宣告 **`using`** 現在讓衍生類別的初始化能夠看到對應的基類，而不是宣告其他衍生類別的函式。 此重寫是來自 C++14 的變更。 在 Visual Studio 2017 15.7 版和更新版本中，在 **`/std:c++17`** 模式中，在 c + + 14 中有效的程式碼，並使用繼承的函數可能無效，或可能有不同的語義。

下列範例顯示 C++14 行為：

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

下列範例顯示 **`/std:c++17`** Visual Studio 15.7 中的行為：

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

如需詳細資訊，請參閱[建構函式](../cpp/constructors-cpp.md#inheriting_constructors)。

### <a name="c17-extended-aggregate-initialization"></a>C + + 17：擴充的匯總初始化

[P0017R1](https://wg21.link/p0017r1)

如果基類的函式為非公用，但衍生類別可存取，則在 **`/std:c++17`** Visual Studio 2017 15.7 版的模式下，您就無法再使用空的大括弧來初始化衍生型別的物件。
下列範例顯示 C++14 一致性行為：

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

在 C++17 中，`Derived` 已視作彙總類型。 因此，透過私用預設建構函式將 `Base` 初始化會直接包含在擴充彙總初始化規則的過程。 `Base` 私用建構函式在先前會透過 `Derived` 建構函式呼叫，而成功的因素是 friend 宣告所致。
下列範例顯示模式下 Visual Studio 版本15.7 中的 c + + 17 行為 **`/std:c++17`** ：

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};
struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C + + 17：使用 auto 宣告非類型範本參數

[P0127R2](https://wg21.link/p0127r2)

在 **`/std:c++17`** 模式中，編譯器現在可以推算以宣告的非類型樣板引數類型 **`auto`** ：

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

這項新功能的影響之一，包括有效的 C++14 程式碼可能失效或有不同的語意。 例如，部分先前無效的多載現在會變得有效。 下列範例顯示因為對 `example(p)` 的呼叫已繫結至 `example(void*);`，而編譯的 C++14 程式碼。 在 Visual Studio 2017 15.7 版的模式中，函式 **`/std:c++17`** `example` 範本是最符合的項。

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

下列範例會以模式顯示 Visual Studio 15.7 中的 c + + 17 程式碼 **`/std:c++17`** ：

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C + + 17： (部分) 的基底字元串轉換

[P0067R5](https://wg21.link/p0067r5) 介於整數與字串之間，以及浮點數與字串之間的低階、無關地區設定的函式轉換。

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C + + 20：避免不必要的衰減 (部分) 

[P0777R1](https://wg21.link/p0777r1) 為 "decay'' 的概念與單純移除常式或參考限定詞之間的差異新增區別。  新增類型特徵 `remove_reference_t` 來取代部分內容中的 `decay_t`。 Visual Studio 2019 中已實作 `remove_cvref_t` 的支援。

### <a name="c17-parallel-algorithms"></a>C + + 17：平行演算法

[P0024R2](https://wg21.link/p0024r2) 平行處理原則 TS 已併入標準，但有些微修改。

### <a name="c17-hypotx-y-z"></a>C++17：`hypot(x, y, z)`

[P0030R1](https://wg21.link/p0030r1)針對類型、和，將三個新的多載加入 `std::hypot` ， **`float`** **`double`** **`long double`** 其中每一個都有三個輸入參數。

### <a name="c17-filesystem"></a>C++17：\<filesystem>

[P0218R1](https://wg21.link/p0218r1) 為標準採用檔案系統 TS，其中包括些許用詞修改。

### <a name="c17-mathematical-special-functions"></a>C + + 17：數學特殊函數

[P0226R1](https://wg21.link/p0220r1)採用先前在標準標頭中數學特殊功能的技術規格 \<cmath> 。

### <a name="c17-deduction-guides-for-the-standard-library"></a>C + + 17：標準程式庫的推斷指南

[P0433R2](https://wg21.link/p0433r2) 更新 STL 以利用 C++17 對 [P0091R3](https://wg21.link/p0091r3) 的採用，這為類別範本引數推斷新增了支援。

### <a name="c17-repairing-elementary-string-conversions"></a>C + + 17：修復基底字元串轉換

[P0682R1](https://wg21.link/p0682r1)將新的基底字元串轉換函式從 P0067R5 移至新的標頭， \<charconv> 並進行其他改進，包括變更要使用的錯誤處理， `std::errc` 而不是 `std::error_code` 。

### <a name="c17-constexpr-for-char_traits-partial"></a>C++17：`char_traits` 的 `constexpr` (部分)

[P0426R1](https://wg21.link/p0426r1)對成員函式、和的變更， `std::traits_type` `length` `compare` `find` 使其可 `std::string_view` 在常數運算式中使用。 (在 Visual Studio 2017 15.6 版中，僅支援 Clang/LLVM。 在 15.7 版 Preview 2 中，也幾乎完全支援 CIXX。)

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a>15.9 中的一致性改善

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>運算子的從左到右評估順序 `->*`、`[]`、`>>` 與 `<<`

從 C++17 開始，運算子的運算元 `->*`、`[]`、`>>` 與 `<<` 必須以從左到右的順序評估。 編譯器在兩種案例下無法保證此順序：

- 當其中一個運算元運算式是由值傳遞的物件或包含由值傳遞的物件，或

- 當使用進行編譯時 **`/clr`** ，和其中一個運算元是物件或陣列元素的欄位。

編譯器在無法保證從左到右的評估時會發出警告 [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017)。 只有 **`/std:c++17`** 在指定或更新版本時，編譯器才會產生這個警告，因為這些運算子的由左至右順序需求是在 c + + 17 中引進。

若要解決這個警告，請先考慮是否需要對運算元進行由左至右評估。 例如，當評估運算元可能會產生與順序相關的副作用時，可能需要進行此動作。 在許多情況下，評估運算元的順序沒有可觀察的效果。 若評估順序必須是從左到右，請考慮您是否能改為依 const 參考傳遞運算元。 此變更會消除下列程式碼範例中的警告：

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

## <a name="bug-fixes-in-visual-studio-2017-rtw-version-150"></a><a name="update_150"></a> Visual Studio 2017 RTW (15.0 版) 中的 Bug 修正

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 正確地引發與使用初始化運算式清單建立物件相關的編譯器錯誤。 Visual Studio 2015 中未攔截到這些錯誤，可能會導致當機或未定義的執行時間行為。 根據 N4594 13.3.1.7 p1，在複製清單初始化中，編譯器必須針對多載解析考慮明確的函式。 不過，如果選擇特定的多載，它必須引發錯誤。

下列兩個範例是在 Visual Studio 2015 中編譯，但無法在 Visual Studio 2017 中編譯。

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

若要更正錯誤，請使用直接初始化︰

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

在 Visual Studio 2015 中，編譯器錯誤地處理複製清單初始化的方式與一般的複製初始化相同：它只會考慮轉換多載解析的函式。 在下列範例中，Visual Studio 2015 選擇 `MyInt(23)` 。 Visual Studio 2017 正確地引發錯誤。

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

這個範例與上一個範例類似，但會引發不同的錯誤。 它在 Visual Studio 2015 中成功，但在 Visual Studio 2017 中失敗，錯誤為 C2668。

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>被取代的 typedef

Visual Studio 2017 現在會針對類別或結構中已被取代的 typedef 發出正確的警告。 下列範例會在 Visual Studio 2015 中編譯而不發出警告。 它會在 Visual Studio 2017 中產生 C4996。

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### `constexpr`

在 constexpr 內容中條件式評估作業的左運算元無效時，Visual Studio 2017 會正確地引發錯誤。 下列程式碼會在 Visual Studio 2015 中進行編譯，但不在 Visual Studio 2017 中，其會引發 C3615 `constexpr function 'f' cannot result in a constant expression` ：

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}
```

若要更正錯誤，請將函式宣告 `array::size()` 為， **`constexpr`** 或 **`constexpr`** 從移除辨識符號 `f` 。

### <a name="class-types-passed-to-variadic-functions"></a>傳遞給 variadic 函式的類別類型

在 Visual Studio 2017 中，傳遞至 variadic 函數（例如）的類別或結構 `printf` 必須是完整可複製。 傳遞這類物件時，編譯器只會進行位元複製，而且不會呼叫建構函式或解構函式。

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

若要更正錯誤，您可以呼叫會傳回可完整複製類型的成員函式，

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

或者先使用靜態轉型來轉換物件，再傳遞它︰

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

對於使用建立和管理的字串 `CString` ，應該使用提供的，將 `operator LPCTSTR()` `CString` 物件轉換成格式字串所預期的 C 指標。

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>類別建構中的 CV 限定詞

在 Visual Studio 2015 中，透過建構函式呼叫來產生類別物件時，編譯器有時會錯誤地忽略 cv 限定詞。 此問題可能會導致當機或意外執行階段行為。 下列範例是在 Visual Studio 2015 中編譯，但在 Visual Studio 2017 中引發編譯器錯誤：

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

若要更正錯誤，請將宣告 `operator int()` 為 **`const`** 。

### <a name="access-checking-on-qualified-names-in-templates"></a>範本中限定名稱的存取檢查

舊版編譯器不會在某些範本內容中檢查限定名稱的存取權。 此問題可能會干擾預期的 SFINAE 行為，因為名稱的 inaccessibility，應該會導致替換失敗。 它可能會在執行時間造成當機或非預期的行為，因為編譯器錯誤地呼叫了運算子的錯誤多載。 在 Visual Studio 2017 中，會引發編譯器錯誤。 特定的錯誤可能會有所不同，但通常是 C2672 `no matching overloaded function found` 。 下列程式碼是在 Visual Studio 2015 中編譯，但在 Visual Studio 2017 中引發錯誤：

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>遺漏範本引數清單

在 Visual Studio 2015 和更早版本中，編譯器不會診斷所有遺漏的範本引數清單。 當遺漏的範本出現在樣板參數清單中時，並不會注意到：例如，缺少部分預設樣板引數或非類型範本參數時。 此問題可能會導致無法預期的行為，包括編譯器當機或意外執行階段行為。 下列程式碼在 Visual Studio 2015 中會編譯，但在 Visual Studio 2017 中會產生錯誤。

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Expression-SFINAE

為了支援運算式 SFINAE，編譯器現在 **`decltype`** 會在宣告範本而不是具現化時，剖析引數。 因此，如果在 decltype 引數中發現非相依特製化，不會延遲到具現化期間。 系統會立即處理，而且會在當下診斷出任何產生的錯誤。

下列範例顯示在宣告時引發的這類編譯器錯誤︰

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>宣告於匿名命名空間中的類別

根據 C++ 標準，宣告於匿名命名空間中的類別具有內部連結，這表示無法將它匯出。 在 Visual Studio 2015 和更早的版本中，並未強制執行此規則。 在 Visual Studio 2017 中，會部分強制執行此規則。 在 Visual Studio 2017 中，下列範例會引發錯誤 C2201：`const anonymous namespace::S1::vftable: must have external linkage in order to be exported/imported.`

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>實值類別成員的預設初始設定式 (C++/CLI)

在 Visual Studio 2015 和以前版本中，編譯器允許 (但忽略) 實值類別成員的預設成員初始設定式。 實值類別的預設初始化一律會以零初始化成員。 不允許預設建構函式。 在 Visual Studio 2017 中，預設成員初始設定式會引發編譯器錯誤，如這個範例中所示︰

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>預設索引子 (C++/CLI)

在 Visual Studio 2015 和以前版本中，在某些情況下，編譯器會將預設屬性錯誤地識別為預設索引子。 您可以使用識別碼來存取屬性，藉此解決此問題 **`default`** 。 因應措施本身在 **`default`** 以 c + + 11 的關鍵字引進之後變得有問題。 在 Visual Studio 2017 中，已修正需要解決的 bug。 編譯器現在 **`default`** 會在用來存取類別的預設屬性時引發錯誤。

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

在 Visual Studio 2017 中，您可以依名稱存取這兩個實值屬性︰

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="bug-fixes-in-153"></a><a name="update_153"></a>15.3 中的 Bug 修正

### <a name="calls-to-deleted-member-templates"></a>對已刪除之成員範本的呼叫

在舊版的 Visual Studio 中，在某些情況下，編譯器無法針對已刪除成員範本的格式不正確的呼叫發出錯誤。 這些呼叫可能會在執行時間造成當機。 下列程式碼現在會產生 C2280 `'int S<int>::f<int>(void)': attempting to reference a deleted function` ：

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}
```

若要修正錯誤，請將宣告 `i` 為 **`int`** 。

### <a name="pre-condition-checks-for-type-traits"></a>類型特性的先決條件檢查

Visual Studio 2017 15.3 版改進了類型特性的先決條件檢查，以更嚴格地遵守標準。 此類檢查是可供指派的。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生 C2139：

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>原生至 Managed 封送處理上的新編譯器警告和執行階段檢查

從受控函式對原生函式的呼叫需要封送處理。 CLR 會執行封送處理，但它並不了解 C++ 語意。 如果您根據傳遞原生物件，CLR 會呼叫物件的 copy-constructor，或使用 `BitBlt`，這可能在執行階段導致未定義的行為。

現在編譯器會在編譯時期發現此錯誤時發出警告：具有已刪除之複製 ctor 的原生物件會在原生和 managed 界限之間以傳值方式傳遞。 針對編譯器在編譯時期不知道的那些情況，其會插入執行階段檢查，以便程式會在發生語式錯誤的封送處理時，立即呼叫 `std::terminate`。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生警告 C4606`'A': passing argument by value across native and managed boundary requires valid copy constructor. Otherwise, the runtime behavior is undefined.`

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshaling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

若要修正錯誤，請移除 `#pragma managed` 指示詞，以將呼叫者標示為原生並避免封送處理。

### <a name="experimental-api-warning-for-winrt"></a>WinRT 的實驗性 API 警告

針對實驗和意見反應所發行的 WinRT API 會附有 `Windows.Foundation.Metadata.ExperimentalAttribute`。 在 Visual Studio 2017 15.3 版中，編譯器會產生這個屬性的警告 C4698。 舊版 Windows SDK 中的一些 API 已附有該屬性，而呼叫這些 API 現在會觸發此編譯器警告。 較新的 Windows Sdk 會將屬性從所有出貨的類型中移除。 如果您使用的是較舊的 SDK，您必須針對所有出貨類型的呼叫隱藏這些警告。

下列程式碼會產生警告 C4698： `'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' is for evaluation purposes only and is subject to change or removal in future updates` ：

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

若要停用該警告，請加入 #pragma：

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>範本成員函式的程式碼外部定義

Visual Studio 2017 15.3 版會針對未在類別中宣告之樣板成員函式的非正規定義產生錯誤。 下列程式碼現在會產生錯誤 C2039： `'f': is not a member of 'S'` ：

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

若要修正錯誤，請將宣告加入類別：

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>嘗試取得 `this` 指標的位址

在 c + + 中， **`this`** 是 X 類型指標的 x prvalue。您無法使用的位址， **`this`** 或將它系結至左值參考。 在舊版的 Visual Studio 中，編譯器可讓您使用轉換以避開此限制。 在 Visual Studio 2017 15.3 版中，編譯器會產生錯誤 C2664。

### <a name="conversion-to-an-inaccessible-base-class"></a>轉換成無法存取的基底類別

當您嘗試將類型轉換為無法存取的基底類別時，Visual Studio 2017 15.3 版會產生錯誤。 編譯器現在會引發錯誤 C2243： `'type cast': conversion from 'D *' to 'B *' exists, but is inaccessible` 。 下列程式碼是語式錯誤的，且可能在執行階段造成當機。 編譯器現在會在看到類似下面的程式碼時產生 C2243：

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>成員函式的程式碼外部定義不允許預設引數

範本類別中成員函式的程式碼外部定義不允許預設引數。 編譯器會在下發出警告 **`/permissive`** ，並在底下發生硬錯誤 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 。

在舊版的 Visual Studio 中，下列語式錯誤的程式碼可能會導致執行階段當機。 Visual Studio 2017 15.3 版會產生警告 C5034： `'A\<T>::f': an out-of-line definition of a member of a class template cannot have default arguments` ：

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

若要修正錯誤，請移除 `= false` 預設引數。

### <a name="use-of-offsetof-with-compound-member-designator"></a>使用 `offsetof` 搭配複合成員指示項

在 Visual Studio 2017 15.3 版中，使用 `offsetof(T, m)` （其中*m*是「複合成員指示項」）會在您使用選項編譯時產生警告 **`/Wall`** 。 下列程式碼的語式錯誤，且可能在執行階段造成當機。 Visual Studio 2017 15.3 版會產生警告 C4841： `non-standard extension used: compound member designator in offsetof` ：

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

若要修正程式碼，您可以使用 pragma 停用警告，或將程式碼變更為不使用 `offsetof`：

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>使用 `offsetof` 搭配靜態資料成員或成員函式

在 Visual Studio 2017 15.3 版中，使用 `offsetof(T, m)` (其中 *m* 代表靜態資料成員或成員函式) 會導致錯誤。 下列程式碼會產生錯誤 C4597： `undefined behavior: offsetof applied to member function 'example'` 和錯誤 C4597： `undefined behavior: offsetof applied to static data member 'sample'` ：

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

此程式碼的語式錯誤，且可能在執行階段造成當機。 若要修正錯誤，請變更程式碼以不再叫用未定義的行為。 它是不可移植且 C++ 標準不允許的程式碼。

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a> 針對 `__declspec` 屬性的新警告

在 Visual Studio 2017 15.3 版中，如果 `__declspec(...)` 套用於 `extern "C"` 連結規格前，編譯器就不再略過該屬性。 編輯器之前會忽略該屬性，這可能隱含執行階段。 當 **`/Wall`** 設定和 **`/WX`** 選項時，下列程式碼會產生警告 C4768： `__declspec attributes before linkage specification are ignored` ：

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

若要修正此警告，請先加入`extern "C"`：

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

在15.3 中，此警告預設為關閉，但在15.5 中預設為開啟，而且只會影響以編譯的程式碼 **`/Wall`** **`/WX`** 。

### <a name="decltype-and-calls-to-deleted-destructors"></a>`decltype` 和對已刪除之解構函式的呼叫

在舊版的 Visual Studio 中，編譯器不會在與相關聯之運算式的內容中發生已刪除的函式的呼叫時偵測到 **`decltype`** 。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生錯誤 C2280： `'A<T>::~A(void)': attempting to reference a deleted function` ：

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}
```

### <a name="uninitialized-const-variables"></a>未初始化的 const 變數

Visual Studio 2017 RTW 版本有回歸： c + + 編譯器不會針對未初始化的變數發出診斷 **`const`** 。 Visual Studio 2017 15.3 版已修正此迴歸。 下列程式碼現在會產生警告 C4132： `'Value': const object should be initialized` ：

```cpp
const int Value; //C4132
```

若要修正錯誤，請將值指派給 `Value`。

### <a name="empty-declarations"></a>空白宣告

Visual Studio 2017 15.3 版現在會針對所有類型的空白宣告發出警告，而不是只針對內建類型。 下列程式碼現在針對四種宣告，都會產生層級 2 C4091 警告：

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

若要移除警告，請將空白宣告註解化或移除。 在未命名物件可能具有副作用 (例如 RAII) 的情況下，應該提供名稱給它。

警告會排除在底下 **`/Wv:18`** ，而且預設會在警告層級 W2 下開啟。

### <a name="stdis_convertible-for-array-types"></a>陣列型別的 `std::is_convertible`

舊版編譯器對陣列類型的 [std::is_convertible](../standard-library/is-convertible-class.md) 會給出不正確的結果。 這要求程式庫作者在使用 `std::is_convertible<...>` 類型特性時，以特殊案例處理 Microsoft C++ 編譯器。 下例中，靜態判斷提示能夠通過舊版 Visual Studio，但在 Visual Studio 2017 15.3 版中失敗：

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` 的計算是查看 imaginary 函式的定義是否正確：

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>私用解構函式和 `std::is_constructible`

舊版編譯器在決定 [std::is_constructible](../standard-library/is-constructible-class.md) 的結果時，會忽略解構函式是否是私人的。 現在會考慮。 下例中，靜態判斷提示能夠通過舊版 Visual Studio，但在 Visual Studio 2017 15.3 版中失敗：

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

私人解構函式會讓類型成為不可建構的。 `std::is_constructible<T, Args...>` 的計算如下列宣告所示：

```cpp
   T obj(std::declval<Args>()...)
```

這個呼叫暗示解構函式呼叫。

### <a name="c2668-ambiguous-overload-resolution"></a>C2668：語意模糊的多載解析

舊版編譯器在同時透過使用宣告和引數相依查閱找到多個候選項目時，有時偵測不到語意模糊。 此失敗會導致選擇錯誤的多載和未預期的執行階段行為。 在下列範例中，Visual Studio 2017 15.3 版會正確地引發 C2668 `'f': ambiguous call to overloaded function` ：

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f;

   S s1, s2;
   f(s1, s2); // C2668
}
```

若要修正程式碼，如果您想要呼叫 `::f()`，請移除使用 `N::f` 陳述式。

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660：區域函式宣告和引數相依查閱

區域函式宣告會將函式宣告隱藏在封閉範圍中，停用引數相依查閱。 不過，在此情況下，舊版編譯器一律會執行引數相依的查閱。 這可能會導致選擇錯誤的多載，以及非預期的執行時間行為。 錯誤通常是因為區域函式宣告的簽章不正確而發生。 在下列範例中，Visual Studio 2017 15.3 版會正確地引發 C2660 `'f': function does not take two arguments` ：

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

若要修正此問題，請變更或移除 `f(S)` 簽章。

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038：初始設定式清單中的初始化順序

類別成員會依其宣告的順序進行初始化，而不是它們出現在初始化運算式清單中的順序。 當初始設定式清單的順序和宣告順序不一致時，舊版編譯器未發出警告。 如果某個成員的初始化相依于清單中另一個已初始化的成員，此問題可能會導致未定義的執行時間行為。 在下列範例中，Visual Studio 2017 15.3 版 (with **`/Wall`**) 會引發 Warning C5038： `data member 'A::y' will be initialized after data member 'A::x'` ：

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

若要修正此問題，請將初始設定式清單排列成和宣告一樣的順序。 當一或兩個初始設定式參考基底類別成員時，就會引發類似的警告。

此警告預設為關閉，且只會影響以編譯的程式碼 **`/Wall`** 。

## <a name="bug-fixes-and-other-behavior-changes-in-155"></a><a name="update_155"></a>15.5 中的錯誤修正和其他行為變更

### <a name="partial-ordering-change"></a>部分排序變更

編譯器現在會正確地拒絕下列程式碼，並提供正確的錯誤訊息：

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

上述範例的問題在於類型中有兩個差異 (const 與非 const 以及 pack 與非 pack)。 若要排除編譯器錯誤，請移除其中一個差異。 然後，編譯器可以明確地排序函式。

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>例外狀況處理常式

陣列或函式類型參考的處理常式從未可以比對所有例外狀況物件。 編譯器現在會正確地接受這項規則，並引發層級 4 警告。 當使用時，它也不會再將或的處理常式與 `char*` `wchar_t*` 字串常值進行比對 **`/Zc:strictStrings`** 。

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

下列程式碼可避免這個錯誤：

```cpp
catch (int (*)[1]) {}
```

### <a name="stdtr1-namespace-is-deprecated"></a><a name="tr1"></a> `std::tr1` 命名空間已淘汰

非標準 `std::tr1` 命名空間在 C++14 和 C++17 模式中現在皆標記為已淘汰。 在 Visual Studio 2017 15.5 版中，下列程式碼會引發 C4996：

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

若要修正此錯誤，請移除 `tr1` 命名空間的參考：

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a>附錄 D 中的標準程式庫功能標記為已被取代

當 **`/std:c++17`** 設定模式編譯器參數時，附錄 D 中幾乎所有的標準程式庫功能都會標示為已被取代。

在 Visual Studio 2017 15.5 版中，下列程式碼會引發 C4996：

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

若要修正錯誤，請遵循警告文字中的指示，如下列程式碼所示：

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>未參考的區域變數

在 Visual Studio 15.5 中，有更多情況會發出警告 C4189，如下列程式碼所示：

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

若要修正錯誤，請移除未使用的變數。

### <a name="single-line-comments"></a>單行註解

在 Visual Studio 2017 15.5 版中，C 編譯器不再發出警告 C4001 和 C4179。 之前，它們只會在 **`/Za`** 編譯器參數下發出。  由於自 C99 起，單行註解已成為 C 標準的一部分，因此不再需要這些警告。

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

當程式碼不需要回溯相容時，您可以藉由移除 C4001/C4179 隱藏專案來避免出現警告。 如果程式碼確實需要與舊版相容，則只隱藏 C4619。

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>包含 `extern "C"` 連結的 `__declspec` 屬性

在舊版的 Visual Studio 中，若在 `extern "C"` 連結規格之前套用 `__declspec(...)` 屬性，編譯器會忽略 `__declspec(...)`。 此行為會產生使用者不想要且可能隱含執行階段的程式碼。 在 Visual Studio 15.3 版中已新增警告，但預設為關閉。 在 Visual Studio 2017 15.5 版中，預設會啟用該警告。

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

若要修正錯誤，請在 __declspec 前面加上連結規格：

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Visual Studio 2017 15.3 或舊版隨附的一些 Windows SDK 標頭 (例如：10.0.15063.0 版，也稱為 RS2 SDK) 會提供這項新警告 C4768。 不過，較新版的 Windows SDK 標頭 (特別是 ShlObj.h 和 ShlObj_core.h) 已經過修正，因此不會產生這個警告。 當您看到 Windows SDK 標頭中出現這個警告時，您可以採取下列動作：

1. 切換至 Visual Studio 2017 15.5 版隨附的最新 Windows SDK。

1. 關閉 Windows SDK 標頭陳述式之 #include 前後的警告：

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a>`extern constexpr`連結

在舊版的 Visual Studio 中，編譯器一律會提供 **`constexpr`** 變數內部連結，即使變數已標記也一樣 **`extern`** 。 在 Visual Studio 2017 15.5 版中，新的編譯器參數 (**`/Zc:externConstexpr`**) 啟用正確且符合標準的行為。 此行為最後終究會成為預設值。

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

如果標頭檔包含宣告的變數 **`extern constexpr`** ，則需要將它標示 `__declspec(selectany)` 為正確結合其重複宣告：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>`typeid` 不可用於不完整的類別類型

在舊版的 Visual Studio 中，編譯器不正確地允許下列程式碼，因此導致可能不正確的類型資訊。 在 Visual Studio 2017 15.5 版中，編譯器會正確地引發錯誤：

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>`std::is_convertible` 目標類型

`std::is_convertible` 要求目標類型必須是有效的傳回型別。 在舊版的 Visual Studio 中，編譯器不正確地允許抽象類型，因此可能導致不正確的多載解析和非預期的執行階段行為。  下列程式碼現在會正確地引發 C2338：

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

若要避免錯誤，當使用 `is_convertible` 時，您應該比較指標類型，因為如果某個類型為抽象，非指標類型比較可能會失敗：

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a> 動態例外狀況規格移除和 `noexcept`

在 c + + 17 中， `throw()` 是的別名 **`noexcept`** ， `throw(<type list>)` 而且會 `throw(...)` 移除，而某些類型可能包含 **`noexcept`** 。 此變更會導致符合 C++14 或更早版本之程式碼的來源相容性。 在 **`/Zc:noexceptTypes-`** **`noexcept`** 一般情況下使用 c + + 17 模式時，可以使用參數來還原為 c + + 14 版的。 它可讓您更新原始程式碼以符合 C++17，而不需要同時重寫所有 `throw()` 程式碼。

編譯器現在也會在 c + + 17 模式中，或使用 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 新的警告 C5043，診斷更不相符的例外狀況規格。

下列程式碼會在套用參數時，于 Visual Studio 2017 15.5 版中產生 C5043 和 C5040 **`/std:c++17`** ：

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```

若要在仍使用時移除錯誤 **`/std:c++17`** ，請將 **`/Zc:noexceptTypes-`** 參數新增至命令列，或更新您的程式碼以使用 **`noexcept`** ，如下列範例所示：

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>內嵌變數

靜態 **`constexpr`** 資料成員現在是隱含的 **`inline`** ，這表示其在類別內的宣告現在是其定義。 針對資料成員使用非正規定義 **`static constexpr`** 是多餘的，現在已被取代。 在 Visual Studio 2017 15.5 版中，當 **`/std:c++17`** 套用參數時，下列程式碼現在會產生警告 C5041 `'size': out-of-line definition for constexpr static data member is not needed and is deprecated in C++17` ：

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)` 警告 C4768 現在預設會開啟

在 Visual Studio 2017 15.3 版中已新增警告，但預設為關閉。 在 Visual Studio 2017 15.5 版中，預設會啟用該警告。 如需詳細資訊，請參閱[ \_ \_ Declspec 屬性的新警告](#declspec)。

### <a name="defaulted-functions-and-__declspecnothrow"></a>預設函式和 `__declspec(nothrow)`

當對應的基底/成員函式允許例外狀況時，編譯器之前允許使用 `__declspec(nothrow)` 宣告預設函式。 此行為違反 C++ 標準，而且可能在執行階段導致未定義的行為。 如果不符合例外狀況規格，此標準會要求將這類函式定義為已刪除。  在底下 **`/std:c++17`** ，下列程式碼會引發 C2280`attempting to reference a deleted function. Function was implicitly deleted because the explicit exception specification is incompatible with that of the implicit declaration.`

```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

若要修正此程式碼，請從預設函式中移除 __declspec(nothrow) 或移除 `= default`，然後提供該函式的定義，以及任何必要的例外狀況處理：

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```

### <a name="noexcept-and-partial-specializations"></a>`noexcept` 和部分特製化

**`noexcept`** 在類型系統中，符合特定「可呼叫」類型的部分特製化可能無法編譯，或無法選擇主要範本，因為 noexcept 函式的部分特製化遺漏。

在這種情況下，您可能需要新增額外的部分特製化，以處理函式 **`noexcept`** 指標和成員函式的 **`noexcept`** 指標。 這些多載只在模式中是合法的 **`/std:c++17`** 。 如果必須維持與 C++14 舊版相容，而且您正撰寫的程式碼有其他人使用，則您應該使用 `#ifdef` 指示詞括住這些新的多載。 如果您使用的是獨立的模組，則 `#ifdef` 可以使用參數編譯，而不是使用「防護」 **`/Zc:noexceptTypes-`** 。

下列程式碼會在下編譯 **`/std:c++14`** ，但在底下會失敗 **`/std:c++17`** `error C2027: use of undefined type 'A<T>'` ：

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

下列程式碼會在下成功， **`/std:c++17`** 因為編譯器會選擇新的部分特製化 `A<void (*)() noexcept>` ：

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="bug-fixes-and-other-behavior-changes-in-157"></a><a name="update_157"></a>15.7 中的錯誤修正和其他行為變更

### <a name="c17-default-argument-in-the-primary-class-template"></a>C + + 17：主要類別範本中的預設引數

此行為變更是[類別範本的範本引述推算 - P0091R3](https://wg21.link/p0091r3) \(英文\) 的先決條件。

在此之前，編譯器會忽略主要類別範本中的預設引數：

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

在 **`/std:c++17`** Visual Studio 2017 15.7 版的模式中，不會忽略預設引數：

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>相依名稱解析

此行為變更是[類別範本的範本引述推算 - P0091R3](https://wg21.link/p0091r3) \(英文\) 的先決條件。

在下列範例中，Visual Studio 15.6 及舊版中的編譯器，在主要類別範本中會將 `D::type` 解析為 `B<T>::type`。

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Visual Studio 2017 15.7 版（在 **`/std:c++17`** 模式中）需要 **`typename`** D 中語句的關鍵字 **`using`** 。若沒有 **`typename`** ，編譯器會引發警告 C4346： `'B<T*>::type': dependent name is not a type` 和錯誤 C2061： `syntax error: identifier 'type'` ：

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17：`[[nodiscard]]` 屬性 - 警告等級增加

在 Visual Studio 2017 15.7 版的 **`/std:c++17`** 模式中，C4834 的警告層級 `discarding return value of function with 'nodiscard' attribute` 會從 W3 增加到 W1。 您可以停用轉換成的警告 **`void`** ，或傳遞 **`/wd:4834`** 給編譯器

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Variadic 範本建構函式基底類別初始化清單

在先前的 Visual Studio 版本中，有一個缺少範本引數的 variadic 範本建構函式基底類別初始化清單錯誤地被允許而未產生錯誤。 在 Visual Studio 2017 15.7 版中，會引發編譯器錯誤。

下列 Visual Studio 2017 15.7 版中的程式碼範例會引發錯誤 C2614： `D<int>: illegal member initialization: 'B' is not a base or member` 。

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;
```

若要修正錯誤，請將 B ( # A1 運算式變更為 B \<T> ( # A3。

### <a name="constexpr-aggregate-initialization"></a>`constexpr` 彙總初始化

舊版 c + + 編譯器不正確地處理 **`constexpr`** 匯總初始化。 編譯器接受不正確程式碼，其中匯總-init 清單具有太多元素，並為其產生不正確的 codegen。 以下程式碼為此類程式碼的範例：

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

在 Visual Studio 2017 版本 15.7 update 3 和更新版本中，先前的範例現在會引發 C2078 `too many initializers` 。 以下範例顯示如何修正該程式碼。 當使用巢狀大括弧初始化清單將 `std::array` 初始化時，讓內部陣列使用自己的大括弧清單：

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="bug-fixes-and-behavior-changes-in-158"></a><a name="update_158"></a>15.8 中的 Bug 修正和行為變更

Visual Studio 2017 15.8 版中的編譯器變更包括 bug 修正和行為變更。 如下所列：

### <a name="typename-on-unqualified-identifiers"></a>非限定識別碼上的 `typename`

在 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 模式中， **`typename`** 編譯器不再接受別名範本定義中未限定識別碼的偽關鍵字。 下列程式碼現在會產生 C7511 `'T': 'typename' keyword must be followed by a qualified name` ：

```cpp
template <typename T>
using  X = typename T;
```

若要修正此錯誤，請將第二行變更為 `using  X = T;`。

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>別名範本定義右側的 `__declspec()`

不再允許 [__declspec](../cpp/declspec.md) 位於別名範本定義的右側。 先前，編譯器已接受但忽略此程式碼。 使用別名時，絕對不會產生取代警告。

您可以改為使用已[ \[ \[ 淘汰 \] \] ](../cpp/attributes.md)的 standard c + + 屬性，並遵守 Visual Studio 2017 15.6 版。 下列程式碼現在會產生 C2760 `syntax error: unexpected token '__declspec', expected 'type specifier'` ：

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

若要修正此錯誤，請變更為下列程式碼 (使用位於別名定義 '=' 之前的屬性)：

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>兩階段名稱查閱診斷

兩階段名稱查閱需要讓範本能夠在定義時看到範本主體中使用的非相依名稱。 之前，Microsoft C++ 編譯器會在具現化時期之前將找不到的名稱保持未查閱。 現在，它需要在範本主體中繫結非相依名稱。

表示這種情況的其中一個方法是使用相依基底類別的查詢。 先前，編譯器允許使用在相依基類中定義的名稱。 這是因為它們會在具現化期間進行查閱，而所有類型都已解析。 現在，該程式碼會被視為錯誤。 在這些情況下，您可以強制在具現化時期查閱變數，方法是使用基底類別類型進行限定，或以其他方式使其相依，例如新增 `this->` 指標。

在 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 模式中，下列程式碼現在會引發 C3861： `'base_value': identifier not found` ：

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

若要修正錯誤，請將 **`return`** 語句變更為 `return this->base_value;` 。

**注意：** 在提升 python 程式庫中，已針對[unwind_type. 措施](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp)中的範本向前宣告提供了 MSVC 特有的因應措施。 [`/permissive-`](../build/reference/permissive-standards-conformance.md)從 Visual Studio 2017 15.8 版 (\_ services.msc \_ VER = 1915) 開始的模式下，MSVC 編譯器會正確地執行引數相依名稱查閱 (ADL) 。 它現在與其他編譯器一致，因此不需要這種因應措施的防護。 若要避免錯誤 C3861： `'unwind_type': identifier not found` ，請參閱提升存放庫中的[PR 229](https://github.com/boostorg/python/pull/229) ，以更新標頭檔。 我們已修補 [vcpkg](../build/vcpkg.md) Boost 套件，因此若您是從 vcpkg 取得或升級 Boost 來源，則不需要個別套用補充程式。

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>命名空間 `std` 中的向前宣告和定義

C++ 標準不允許使用者將向前宣告或定義新增到命名空間 `std` 中。 將宣告或定義新增至命名空間 `std` 或新增至命名空間 `std` 內的命名空間，現在會導致發生未定義的行為。

在未來的某個時間，Microsoft 將會移動一些標準程式庫類型定義所在的位置。 此變更會中斷將向前宣告新增至命名空間 `std` 的現有程式碼。 新警告 C4643 有助於識別這類來源問題。 警告是在模式中啟用 **`/default`** ，且預設為關閉。 它會影響以或編譯的程式 **`/Wall`** **`/WX`** 。

下列程式碼現在會引發 C4643： `Forward declaring 'vector' in namespace std is not permitted by the C++ Standard` 。

```cpp
namespace std {
    template<typename T> class vector;
}
```

若要修正此錯誤，請使用 **include** 指示詞，而不是向前宣告：

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>委派給其本身的建構函式

C++ 標準建議編譯器應該在建構函式委派給其本身時發出診斷。 和模式中的 Microsoft c + + 編譯器 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 現在會引發 C7535： `'X::X': delegating constructor calls itself` 。

若未出現此錯誤，下列程式會進行編譯，但將產生無限迴圈：

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

若要避免無限迴圈，請委派給不同的建構函式：

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>包含常數運算式的 `offsetof`

[offsetof](../c-runtime-library/reference/offsetof-macro.md) 傳統上使用需要 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) 的巨集來實作。 此用法在需要常數運算式的內容中並不合法，但 Microsoft C++ 編譯器傳統上會允許此做法。 隨附為標準程式庫一部分的 `offsetof` 巨集會正確使用編譯器內建函式 (**__builtin_offsetof**)，但有許多人已使用巨集技巧來定義自己的 `offsetof`。

在 Visual Studio 2017 15.8 版中，編譯器會限制這些 **`reinterpret_cast`** 運算子可以在預設模式中顯示的區域，以協助程式碼符合標準 c + + 行為。 在之下 [`/permissive-`](../build/reference/permissive-standards-conformance.md) ，條件約束甚至會更嚴格。 使用 `offsetof` 需要常數運算式之位置中的結果，可能會導致發出警告 C4644 `usage of the macro-based offsetof pattern in constant expressions is non-standard; use offsetof defined in the C++ standard library instead` 或 C2975 的程式碼 `invalid template argument, expected compile-time constant expression` 。

下列程式碼會在和模式中引發 C4644 **`/default`** **`/std:c++17`** ，並在模式中產生 C2975 [`/permissive-`](../build/reference/permissive-standards-conformance.md) ：

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

若要修正此錯誤，請使用透過 `offsetof` 下列方式定義的 \<cstddef> ：

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>基底類別的 CV 限定詞受限於套件展開

如果基底類別也受限於套件展開，舊版的 Microsoft C++ 編譯器不會偵測到基底類別具有 CV 限定詞。

在 Visual Studio 2017 15.8 版 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 的模式中，下列程式碼會引發 C3770 `'const S': is not a valid base class` ：

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>`template` 關鍵字和巢狀名稱規範

在 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 模式中，編譯器現在會要求 **`template`** 關鍵字出現在相依的嵌套名稱規範後面的範本名稱前面。

在模式中的下列程式碼 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 現在會引發 C7510： `'example': use of dependent template name must be prefixed with 'template'. note: see reference to class template instantiation 'X<T>' being compiled`

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>();
    }
};
```

若要修正錯誤，請將 **`template`** 關鍵字新增至 `Base<T>::example<int>();` 語句，如下列範例所示：

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="bug-fixes-and-behavior-changes-in-159"></a><a name="update_159"></a>15.9 中的 Bug 修正和行為變更

### <a name="identifiers-in-member-alias-templates"></a>成員別名範本中的識別碼

用於成員別名範本定義的識別碼必須先宣告才能使用。

舊版編譯器允許下列程式碼：

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

在 Visual Studio 2017 15.9 版 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 的模式中，編譯器會引發 C3861： `'from_template': identifier not found` 。

若要修正此錯誤，請在 `from_template_t` 之前宣告 `from_template`。

### <a name="modules-changes"></a>模組變更

在 Visual Studio 2017 15.9 版中，每當模組的命令列選項在模組建立端與模組取用端之間不一致時，編譯器都會引發 C5050。 下列範例中有兩個問題：

- 在 (主要 .cpp) 的耗用量端， **`/EHsc`** 未指定選項。

- C + + 版本位於 **`/std:c++17`** 建立端，而 **`/std:c++14`** 在取用端。

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

編譯器會針對這兩種情況引發 C5050： `warning C5050: Possible incompatible environment while importing module 'm': mismatched C++ versions.  Current "201402" module version "201703"` 。

每當 .ifc 檔案遭竄改時，編譯器都會引發 C7536。 模組介面的標頭下方會包含內容的 SHA2 雜湊。 匯入時，ifc 檔案會經過雜湊處理，然後針對標頭中提供的雜湊進行檢查。 如果兩者不相符，則會引發錯誤則 c7536： `ifc failed integrity checks.  Expected SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'` 。

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>涉及別名及非推算內容的部分排序

涉及非推算內容中別名的部分排序規則裡發生實作發散。 在下列範例中，GCC 和 Microsoft c + + 編譯器 ([`/permissive-`](../build/reference/permissive-standards-conformance.md) 模式) 會在 Clang 接受程式碼時引發錯誤。

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

上述範例會引發 C2668：

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

實作散發的原因是 C++ 標準寫法中的迴歸。 核心問題 2235 的解決辦法移除了某些會允許排序這些多載的文字。 目前的 C++ 標準並不提供將這些函式部分排序的機制，因此會將他們視為不明確。

建議的因應措施是，不依賴部分排序來解決此問題。 反之，請使用 SFINAE 來移除特定多載。 在下列範例中，我們使用協助程式類別 `IsA`，在 `Alloc` 為 `A` 的專屬表示時移除第一個多載：

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>樣板化函式定義中不合法的運算式和非常值類型

現在，系統可正確診斷已明確特殊化之樣板化函式定義中不合法的運算式和非常值類型。 先前，系統並不會針對函式定義發出這類錯誤。 不過，如果不合法的運算式或非常值類型是評估為常數運算式的一部分，仍可能被診斷出來。

在舊版的 Visual Studio 中，系統會編譯下列程式碼而不發出警告：

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};

template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

在 Visual Studio 2017 15.9 版中，該程式碼會引發此錯誤：

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

若要避免此錯誤，請 **`constexpr`** 從函式的明確具現化移除限定詞 `f()` 。

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Visual Studio 2015 中的 C++ 一致性改善

我們有完整的一致性改進清單，其中包含了 Visual Studio 2015 Update 3。 如需詳細資訊，請參閱[Visual C++ What's New 2003 through 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015) (Visual C++ 2003 至 2015 的新功能)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[Microsoft c + + 語言一致性資料表](visual-cpp-language-conformance.md)
