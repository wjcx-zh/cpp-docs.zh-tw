---
title: C++ 一致性改善
ms.date: 12/04/2019
description: Visual Studio 的 Microsoft C++ 正在向完全符合 C++20 語言標準邁進。
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: de31c2e61f0a10c785d610d3227a659c59b56d38
ms.sourcegitcommit: 00f50ff242031d6069aa63c81bc013e432cae0cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546428"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Visual Studio 中的 C++ 一致性改善

Microsoft C++ 在每個版本中都進行一致性改善和 Bug 修正。 本文依主要版次和版本的順序列出列出改善。 它也依版本列出重大 Bug 修正。 若要直接跳到特定版本的變更，請使用 [本文內容] 清單。

::: moniker range="vs-2019"

## <a name="improvements_160"></a>Visual Studio 2019 RTW 中的一致性改進（版本16.0）

Visual Studio 2019 RTW 包含下列的一致性改進、bug 修正，以及 Microsoft C++編譯器（MSVC）中的行為變更

**注意：** C + + 20 功能將會在 `/std:c++latest` 模式中提供，直到編譯器和 IntelliSense 的 c + + 20 執行完成為止。 屆時，即會推出 `/std:c++20` 編譯器模式。

### <a name="improved-modules-support-for-templates-and-error-detection"></a>改善的範本和錯誤偵測模組支援

模組現已正式使用 C++20 標準。 Visual Studio 2017 15.9 版已新增改善的支援。 如需詳細資訊，請參閱 [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/) (C++ 模組與 MSVC 2017 15.9 版的更佳範本支援和錯誤偵測)。

### <a name="modified-specification-of-aggregate-type"></a>已修改彙總類型的規格

C++20 已變更彙總類型的規格 (請參閱 [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1) (禁止使用使用者宣告的建構函式彙總))。 在 Visual Studio 2019 的 `/std:c++latest` 下，任何具有使用者宣告建構函式的類別 (例如，包括建構函式宣告的 `= default` 或 `= delete`) 都不是彙總。 過去，只有使用者所提供建構函式才可取消讓類別成為彙總的資格。 這項變更會對如何初始化這類類型的方式加諸額外限制。

在 Visual Studio 2017 中，下列程式碼在編譯時不會引發錯誤，但在 Visual Studio 2019 的 `/std:c++latest` 下會引發 C2280 和 C2440 錯誤：

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

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf) C++20 引入 `<=>` 三向比較運算子，也稱為「太空船運算子」。 `/std:c++latest` 模式中的 Visual Studio 2019 透過引發目前不允許的語法錯誤，引入運算子部分支援。 例如，在 Visual Studio 2017 中，下列程式碼在編譯時不會引發錯誤，但在 Visual Studio 2019 的 `/std:c++latest` 下會引發多個錯誤：

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

在過去，MSVC 允許直接從最高層級底下具有不相符 CV 限定詞的類型繫結參考。 此繫節可能允許修改參考應參考的 const 資料。 編譯器現在會如標準所要求建立暫存。 在 Visual Studio 2017 中，下列程式碼在編譯時不會發出警告。 在 Visual Studio 2019 中，編譯器會引發「警告 C4172：\<func:#1 "?PData@X@@QBEABQBXXZ">，傳回區域變數或暫存的位址」。

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

`reinterpret_cast` 的引數不是允許多載函式位址的內容之一。 在 Visual Studio 2017 中，下列程式碼在編譯時不會引發錯誤，但在 Visual Studio 2019 中會引發「C2440：無法從「多載函式」轉換為 'fp'」：

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

在 C++14 中，Lambda 終止類型不是常值。 此規則的主要結果是 lambda 可能不會指派給**constexpr**變數。 在 Visual Studio 2017 中，下列程式碼在編譯時不會引發錯誤，但在 Visual Studio 2019 中會引發「C2127: 'l': 以非常數運算式初始化 'constexpr' 實體不合法」：

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

若要避免此錯誤，請移除**constexpr**辨識符號，否則請將一致性模式變更為 `/std:c++17`。

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory` 失敗碼

已從 C++20 無條件實作 [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf)。 這會變更 `std::create_directory`，檢查目標在發生故障時是否即為目錄。 以前，所有 ERROR_ALREADY_EXISTS 類型錯誤都會轉換成成功但未建立目錄的程式碼。

### `operator<<(std::ostream, nullptr_t)`

依 [LWG 2221](https://cplusplus.github.io/LWG/issue2221)，已新增 `operator<<(std::ostream, nullptr_t)` 將 nullptrs 寫入資料流。

### <a name="additional-parallel-algorithms"></a>其他的平行演算法

新的平行版 `is_sorted`、`is_sorted_until`、`is_partitioned`、`set_difference`、`set_intersection`、`is_heap` 和 `is_heap_until`。

### <a name="atomic-initialization"></a>不可部分完成的初始化

[P0883 "Fixing atomic initialization"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) (P0883「修正不可部分完成的初始化」) 將 `std::atomic` 變更為初始化包含 T 的值，而不是將它初始化的預設值。 使用 Clang/LLVM 與 Microsoft 標準程式庫時即啟用此修正。 Microsoft C++編譯器目前已停用此功能，作為**constexpr**處理中 bug 的因應措施。

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` 和 `remove_cvref_t`

已從 [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) 實作 `remove_cvref` 和 `remove_cvref_t` 類型特性。 它們會移除類型中的參考性質和 CV 限定性，但不衰減指標的函式和陣列 (不同於 `std::decay` 和 `std::decay_t`)。

### <a name="feature-test-macros"></a>功能測試巨集

[P0941R2 - 功能測試巨集](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html)已完成，並支援 `__has_cpp_attribute`。 所有標準模式都支援功能測試巨集。

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>禁止使用使用者宣告的建構函式彙總

[C++20 P1008R1 - 禁止使用使用者宣告的建構函式彙總](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf)已完成。

## <a name="improvements_161"></a>16.1 中的一致性改善

### <a name="char8_t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html)。 C++20 新增用來表示 UTF-8 字碼單位的新字元類型。 C++20 的 `u8` 字串常值具有類型 `const char8_t[N]` 而非 `const char[N]`，這是舊例。 [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm) \(英文\) 已針對 C 標準建議類似的變更。 [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html) 提供 `char8_t` \(英文\) 回溯相容性的補救建議。 在 Visual Studio 2019 16.1 版中，當您指定 **/Zc:char8_t** 編譯器選項時，Microsoft C++ 編譯器會新增 `char8_t` 支援。 未來還會支援 [/std:c++latest](../build/reference/std-specify-language-standard-version.md)，其可透過 **/Zc:char8_t-** 還原成 C++17 行為。 驅動 IntelliSense 的 EDG 編譯器尚不支援它，所以您會看到假性的僅限 IntelliSense 錯誤，不會影響實際的編譯。

#### <a name="example"></a>範例

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>std::type_identity metafunction 和 std::identity 函式物件

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). 已移除淘汰的 `std::identity` 類別範本副檔名，並已經以 C++20 `std::type_identity` metafunction 和 `std::identity` 函式物件取代。 兩者都僅能在 [/std:c++latest](../build/reference/std-specify-language-standard-version.md) 下使用。

下列範例會在 Visual Studio 2017 中產生 `std::identity` 的淘汰警告 C4996 (定義於 \<type_traits>)：

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

下列範例示範如何使用新的 `std::identity` (定義於\<functional>) 以及新的 `std::type_identity`：

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>泛型 Lambda 的語法檢查

新的 Lambda 處理器可在泛型 Lambda 中啟用一些一致性模式語法檢查，在 [/std:c++latest](../build/reference/std-specify-language-standard-version.md) 下或使用 **/experimental:newLambdaProcessor** 的任何其他語言模式下。

在 Visual Studio 2017 中，此程式碼在編譯時不會發出警告，但在 Visual Studio 2019 中會產生錯誤「C2760 語法錯誤：未預期的權杖 '\<id-expr>'，必須是 'id-expression'」：

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

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (C++20) 為具有明確範本引數的函式呼叫運算式，增強透過依引數相關查閱來尋找函式範本的功能。 需要 **/std:c++latest**。

### <a name="designated-initialization"></a>指定的初始化

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (C++20) 指定的初始化使用 `Type t { .member = expr }` 語法，在彙總初始化中選取特定成員。 需要 **/std:c++latest**。

### <a name="new-and-updated-standard-library-functions-c20"></a>更新的新標準程式庫函式 (C++20)

- 用於 `basic_string` 和 `basic_string_view` 的 `starts_with()` 和 `ends_with()`。
- 關聯容器的 `contains()`。
- `list` 和 `forward_list` 的 `remove()`、`remove_if()` 與 `unique()` 現在會傳回 `size_type`。
- `shift_left()` 和 `shift_right()` 已新增至 \<演算法>。


## <a name="improvements_162"></a>16.2 中的一致性改善

### <a name="noexcept-constexpr-functions"></a>noexcept constexpr 函式

在常數運算式中使用 Constexpr 函數時，預設不再將其視為**noexcept** 。 這項行為變更來自[CWG 1351](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#1351)的解決方式，並已在[/permissive-](../build/reference/permissive-standards-conformance.md)中啟用。 下列範例會在 Visual Studio 2019 16.1 版和更早版本中進行編譯，但會在 Visual Studio 2019 版本16.2 中產生 C2338：

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

若要修正錯誤，請將**noexcept**運算式新增至函式宣告：

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>具有不同列舉類型的二進位運算式

在其中一個是列舉型別，另一個是不同的列舉型別或浮點類型的運算元上套用一般算術轉換的功能，在 c + + 20 （[P1120R0](https://wg21.link/p1120r0)）中已被取代。 在 Visual Studio 2019 16.2 版和更新版本中，當啟用[/std： c + + 最新](../build/reference/std-specify-language-standard-version.md)編譯器選項時，下列程式碼會產生層級4警告：

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

### <a name="binary-expressions-with-enumeration-and-floating-point-types"></a>具有列舉和浮點類型的二進位運算式

在其中一個是列舉型別，另一個是不同的列舉型別或浮點類型的運算元上套用一般算術轉換的功能，在 c + + 20 （[P1120R0](https://wg21.link/p1120r0)）中已被取代。 換句話說，在[/std： c + + 最新](../build/reference/std-specify-language-standard-version.md)編譯器選項啟用時，在列舉和浮點類型之間使用二元運算現在是一個警告：

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

在 c + + 20 （[P1120R0](https://wg21.link/p1120r0)）中，陣列類型的兩個運算元之間的相等和關聯式比較已被取代。 換句話說，兩個數組之間的比較作業（不論次序和範圍相似之處）現在都是警告。 從 Visual Studio 2019 16.2 版開始，下列程式碼會產生*C5056： operator ' = = '：* 當[/std： c + + 最新](../build/reference/std-specify-language-standard-version.md)編譯器選項啟用時，陣列類型已被取代：

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

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>定義太空船運算子的效果 = = 和！ =

除非太空船運算子標記為 `= default` （[P1185R2](https://wg21.link/p1185r2)），否則太空船運算子（ **<=>** ）的定義不會再重寫牽涉 **==** 或 **！ =** 的運算式。 下列範例會在 Visual Studio 2019 RTW 和16.1 版中進行編譯，但會在 Visual Studio 2019 版本16.2 中產生 C2678：

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

- 以固定/科學精確度 \<charconv > `to_chars()`。 （目前已針對16.4 規劃一般精確度）。
- [P0020R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)：不可部分完成的\<float >、不可部分完成\<雙重 >、不可部分完成\<long double >
- [P0463R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)： endian
- [P0482R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html)： char8_t 的程式庫支援
- [P0600R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)： [\[nodiscard]] （適用于 STL，第1部分）
- [P0653R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)： to_address （）
- [P0754R2](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0754r2.pdf)： \<版本 >
- [P0771R1](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0771r1.pdf)： std：： function 的 move 函數的 noexcept

## <a name="improvements_163"></a>Visual Studio 2019 16.3 版中的一致性改善

### <a name="stream-extraction-operators-for-char-removed"></a>已移除 char * 的資料流程提取運算子

連結至字元的資料流程提取運算子已移除，並由一系列字元的抽取運算子取代（每個[P0487R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0487r1.html)）。 WG21 會將已移除的多載視為不安全。 在[/std： c + + 最新](../build/reference/std-specify-language-standard-version.md)模式中，下列範例現在*會產生 C2679：二元 ' > > '：找不到接受 ' char\*' 類型之右運算元的運算子（或是沒有可接受的轉換）* ：

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

### <a name="new-keywords-requires-and-concept"></a>新關鍵字**需要**和**概念**

新的關鍵字**需要**和**概念**已新增至 Microsoft C++編譯器。 如果您嘗試在[/std： c + + 最新](../build/reference/std-specify-language-standard-version.md)模式中使用其中一種作為識別碼，編譯器會引發*C2059：語法錯誤*。

### <a name="constructors-as-type-names-disallowed"></a>不允許型別名稱的函式

當函式名稱在類別樣板特製化的別名後面出現于限定名稱時，不會再將其視為已插入的類別名稱。 這之前允許使用「函式」做為型別名稱來宣告其他實體。 下列範例現在會產生*C3646： ' TotalDuration '：未知的覆寫規範*：

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

若要避免此錯誤，請宣告 `TotalDuration`，如下所示：

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>嚴格檢查 extern "C" 函式

如果在不同的命名空間中宣告**extern "C"** 函式，舊版 Microsoft C++編譯器不會檢查宣告是否相容。 在 Visual Studio 2019 16.3 版中，編譯器會執行這類檢查。 在[/permissive-](../build/reference/permissive-standards-conformance.md)模式中，下列程式碼會產生*C2371：重複定義; 不同的基本類型*和*C2733 您無法使用 C 連結來*多載函式：

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

若要避免上述範例中的錯誤，請在兩個 `f`宣告中一致使用**bool**而非**bool** 。

### <a name="standard-library-improvements"></a>標準程式庫改良功能

已移除 \<stdexcpt 的非標準標頭 > 和 \<typeinfo. h >。 包含它們的程式碼應改為分別包含標準標頭 \<exception > 和 \<typeinfo >。

## <a name="improvements_164"></a>Visual Studio 2019 16.4 版中的一致性改善

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>針對/permissive-中的合格識別碼，更有效地強制執行兩階段名稱查閱

兩階段名稱查閱需要讓範本能夠在定義時看到範本主體中使用的非相依名稱。 先前在範本具現化時，可能會發現這類名稱。 這項變更可讓您更輕鬆地在[/permissive-](../build/reference/permissive-standards-conformance.md)旗標底下的 MSVC 中撰寫可攜、一致的程式碼。

在 Visual Studio 2019 16.4 版中，已設定 **/permissive-** 旗標，下列範例會產生錯誤，因為當定義 `f<T>` 範本時，`N::f` 不會顯示：

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

一般來說，您可以藉由包含遺漏的標頭或向前宣告函式或變數來修正此問題，如下列範例所示：

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

MSVC 編譯器現在會在一致性模式（/permissive-）中實行[CWG 問題 903](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#903) 。 此規則不允許將整數常數運算式隱含轉換（整數常值 ' 0 ' 除外）為 null 指標常數。 下列範例會在一致性模式下產生 C2440：

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

若要修正錯誤，請使用**nullptr** ，而不是**false**。 請注意，仍然允許使用常值0：

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>整數常數值型別的標準規則

在一致性模式（由[/permissive-](../build/reference/permissive-standards-conformance.md)啟用）中，MSVC 會使用整數常數值型別的標準規則。 先前的十進位常值太大，無法納入帶正負號的 ' int '，因為其類型為 ' 無符號 int '。 現在，這類常值會指定下一個最大的帶正負號整數類型「長長」。 此外，具有 ' 尾碼 ' 的常值會被指定為類型「不帶正負號的長長時間」。

這可能會產生不同的警告診斷，以及在常值上執行之算數運算的行為差異。

下列範例顯示 Visual Studio 2019 16.4 版中的新行為。 `i` 變數屬於不**帶正負**號的 int 類型，因此會引發警告。 `j` 變數的高序位位會設定為0。

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

下列範例示範如何保留舊的行為，進而避免警告和執行時間的行為變更：

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

在符合標準的*rqmts*子句時，MSVC 編譯器現在會在遇到 `std` 命名空間中指定的其中一個 type_traits 範本的使用者定義特製化時，引發錯誤。 除非另有指定，否則這類特製化會導致未定義的行為。 下列範例有未定義的行為，因為它違反規則，而 `static_assert` 失敗，併發生錯誤**C2338**。

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

若要避免此錯誤，請定義繼承自所需 type_trait 的結構，並將其特殊化：

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

當啟用[/std： c + + 最新](../build/reference/std-specify-language-standard-version.md)的選項時，MSVC 編譯器現在會針對每個[P1630R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1630r1.html)的比較運算子執行下列變更：

如果運算式牽涉到不是**布林**值的傳回型別，則編譯器不會再以 `operator==` 重寫運算式。 下列程式碼現在會產生*錯誤 C2088： '！ = '：結構不合法*：

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

如果編譯器是類似聯集類別的成員，則不會再定義預設的比較運算子。 下列範例現在會產生*C2120： ' void ' 不合法的所有類型*：

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

如果類別包含參考成員，則編譯器不會再定義預設的比較運算子。 下列程式碼現在會產生*錯誤 C2120： ' void ' 不合法的所有類型*：

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

## <a name="update_160"></a>Visual Studio 2019 中的 Bug 修正和行為變更

### <a name="reinterpret_cast-in-a-constexpr-function"></a>Constexpr 函式中的 Reinterpret_cast

**Reinterpret_cast**在**constexpr**函式中是不合法的。 Microsoft C++編譯器先前只有在**constexpr**內容中使用時，才會拒絕**reinterpret_cast** 。 在 Visual Studio 2019 中，在所有語言標準模式中，編譯器會正確地診斷**constexpr**函式定義中的**reinterpret_cast** 。 下列程式碼現在會產生*C3615： constexpr 函數 ' f ' 無法產生常數運算式*。

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

若要避免此錯誤，請從函式宣告中移除**constexpr**修飾詞。

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>basic_string 範圍建構函式的正確診斷

在 Visual Studio 2019 中，`basic_string` 範圍建構函式不再使用 `static_cast` 隱藏編譯器診斷。 下列程式碼會在 Visual Studio 2017 中編譯而不發出警告，但在初始化 `out`時，從 `wchar_t` 到**char**的資料可能會遺失：

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 會正確引發「C4244：'argument'：從 'wchar_t' 轉換成 'const _Elem'，可能會遺失資料」。 為避免此警告，您可以初始化 std::string，如此範例所示：

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>現可正確偵測 /clr 或 /ZW 下的不正確呼叫 += 和 -=

Visual Studio 2017 中引入的 Bug 導致編譯器以無訊息方式忽略錯誤，且不會為 `/clr` 或 `/ZW` 下的 += 和 -= 無效呼叫產生程式碼。 下列程式碼會在 Visual Studio 2017 中編譯而不會發生錯誤，但在 Visual Studio 2019 中，它會正確引發*錯誤 C2845： ' System：： String ^ '：不允許在此類型上使用指標算術*：

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

為避免此範例中的錯誤，請使用運算子搭配 ToString() 方法：`s += E::e.ToString();`。

### <a name="initializers-for-inline-static-data-members"></a>內嵌靜態資料成員的初始設定式

現在已正確偵測到**內嵌**和**靜態 constexpr**初始化運算式中的成員存取無效。 在 Visual Studio 2017 中，下列範例在編譯時不會引發錯誤，但在 Visual Studio 2019 的 `/std:c++17` 模式下，會引發「錯誤 C2248：無法存取在類別 'X' 中宣告的私用成員」。

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

MSVC 用來提供有關隱含轉換為**bool**的效能警告 C4800。 它太頻繁地發出且無法隱藏，所以在 Visual Studio 2017 我們將它移除。 不過，Visual Studio 2017 在生命週期中獲得許多有助於解決案例問題的意見反應。 我們在 Visual Studio 2019 中重新加入，仔細設計的 C4800，以及說明性的 C4165。 透過明確轉換或適當類型的與 0 比較，這兩個警告都很容易隱藏。 C4800 為預設關閉的層級 4 警告，C4165 是預設關閉的層級 3 警告。 兩者都可使用 `/Wall` 編譯器選項探索。

下列範例在 `/Wall` 下會引發 C4800 和 C4165：

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

在 Visual Studio 2017 中， *C4822：區域類別成員*函式不會只有在明確設定編譯器選項 `/w14822` 時才會引發主體;它不會顯示 `/Wall`。 在 Visual Studio 2019 中，C4822 為預設關閉的警告，因此不必明確設定 `/w14822`，即可在 `/Wall` 下探查到它。

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>如果陳述式

樣板函式主體，其中包含**if constexpr**語句是否已啟用一些[/permissive-](../build/reference/permissive-standards-conformance.md)剖析相關的檢查。 例如，在 Visual Studio 2017 中，下列程式碼會產生*C7510： ' Type '：* 只有在未設定 **/permissive-** 選項時，才使用相依型別名稱的前置詞必須加上 ' typename '。 在 Visual Studio 2019 中，即使已設定 **/permissive-** 選項，相同的程式碼也會引發錯誤：

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

若要避免此錯誤，請將**typename**關鍵字新增至 `a`： `typename T::Type a;`的宣告。

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Lambda 運算式不支援內嵌組譯碼

Microsoft C++小組最近發現在 lambda 中使用內嵌組譯工具的安全性問題，可能會在執行時間導致 `ebp` （傳回位址暫存器）損毀。 惡意攻擊者可能利用這種情況。 鑒於問題的本質，即只有 x86 支援內嵌組譯工具，以及內嵌組譯工具與編譯器的其餘部分互動不佳的事實，這個問題最安全的解決方法是 Lambda 運算式內不允許有內嵌組譯工具。

我們所見唯一會在 Lambda 運算式內使用內嵌組譯工具的實際情況，是擷取傳回位址。 在此案例中，您可以擷取所有平台的寄件地址，只要使用編譯器內建 `_ReturnAddress()` 即可。

下列程式碼會在 Visual Studio 2017 15.9 和 Visual Studio 2019 中產生「C7552：Lambda 中不支援內嵌組譯工具」：

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

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>修正 \<xkeycheck.h> 關鍵字強制執行

已修正標準程式庫的巨集取代關鍵字強制執行 \<xkeycheck.h>，會發出偵測到的實際問題關鍵字，而不是一般訊息。 它也支援 C++20 的關鍵字，可避免誘騙 IntelliSense 說出隨機的巨集關鍵字。

### <a name="allocator-types-no-longer-deprecated"></a>配置器類型不再予以淘汰

`std::allocator<void>`、`std::allocator::size_type` 和 `std::allocator::difference_type` 不再予以淘汰。

### <a name="correct-warning-for-narrowing-string-conversions"></a>更正縮小字串轉換的警告

已從 `std::string` 移除未經標準呼叫之假性 `static_cast` 意外隱藏的 C4244 縮小警告。 嘗試呼叫 `std::string::string(const wchar_t*, const wchar_t*)` 現會正確發出「C4244：將 wchar_t 縮小為一個字元。」

### <a name="various-filesystem-correctness-fixes"></a>各種 \<檔案系統> 正確性修正

- 嘗試變更目錄的上次寫入時間時，修正 `std::filesystem::last_write_time` 失敗。
- 提供不存在的目標路徑時，`std::filesystem::directory_entry` 建構函式現在會儲存失敗的結果，而不是擲回例外狀況。
- `std::filesystem::create_directory` 的 2 個參數版本已變更為呼叫 1 個參數版本，因為當 `existing_p` 為符號連結時，基礎 `CreateDirectoryExW` 函式會使用 `copy_symlink`。
- 當發現符號連結中斷時，`std::filesystem::directory_iterator` 不會再失敗。
- `std::filesystem::space` 現在接受相對路徑。
- `std::filesystem::path::lexically_relative` 不再為句尾斜線困惑，回報為 [LWG 3096](https://cplusplus.github.io/LWG/issue3096)。
- 因應措施為 `CreateSymbolicLinkW` 拒絕在 `std::filesystem::create_symlink` 中有正斜線的路徑。
- 因應措施為 Windows 10 LTSB 1609 有 POSIX 刪除模式 `delete` 函式，實際上並不能刪除檔案。
- `std::boyer_moore_searcher` 和 `std::boyer_moore_horspool_searcher` 的複製建構函式和複製指派運算子現都可實際複製項目。

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Windows 8 和更新版本中的平行演算法

平行演算法程式庫現可正確使用 Windows 8 和更新版本的真實 `WaitOnAddress` 系列，而不是一律使用 Windows 7 和舊版的假版本。

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()` 空白字元

`std::system_category::message()` 現在會修剪傳回訊息的尾端空格。

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine` 除以零

已修正會導致 `std::linear_congruential_engine` 觸發除以 0 的一些情況。

### <a name="fixes-for-iterator-unwrapping"></a>修正迭代器解除包裝

在 Visual Studio 2017 15.8 中，針對程式設計師和使用者整合初次公開的迭代器解除包裝機制，如 C++ 小組部落格文章 [VS 2017 15.8 中的 STL 功能和修正](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/) \(英文\) 中所述，不會再解除包裝衍生自標準程式庫迭代器的迭代器。 例如，衍生自 `std::vector<int>::iterator` 的使用者和嘗試自訂行為的使用者，現在都可在呼叫標準程式庫演算法時試取得其自訂的行為，而不是指標的行為。

未排序的容器 `reserve` 函式現在實際上都會保留以供 N 個元素使用，如 [LWG 2156](https://cplusplus.github.io/LWG/issue2156) \(英文\) 中所述。

### <a name="time-handling"></a>時間處理

- 過去，某些已傳遞給並行程式庫的時間值會溢位，例如 `condition_variable::wait_for(seconds::max())`。 現已修正，溢位過去似乎會以隨機的 29 日循環變更行為 (當基礎 Win32 API 接受的 uint32_t 毫秒溢位時)。

- \<的 ctime > 標頭現在會在命名空間 `std` 中正確宣告 `timespec` 和 `timespec_get`，除了在全域命名空間中宣告這些專案之外。

### <a name="various-fixes-for-containers"></a>容器的各種修正

- 許多標準程式庫的內部容器函式都已成為私用，以改善 IntelliSense 體驗。 MSVC 的較新版本預計會提供可將成員標記為私用的其他修正。

- 已修正 `list`、`map` 和 `unordered_map` 等節點型容器可能損毀的例外狀況安全正確性問題。 在 `propagate_on_container_copy_assignment` 或 `propagate_on_container_move_assignment` 重新指派作業期間，我們會利用舊配置器來釋放容器的 sentinel 節點、對舊的配置器執行 POCCA/POCMA 指派，然後重試取得新配置器的 sentinel 節點。 如果這項配置失敗，則容器會損毀且甚至無法終結，因為擁有 sentinel 節點是不可變的永久性資料結構。 已藉由從來源容器的配置器配置新 sentinel 節點，再終結現有的 sentinel 節點來修正此程式碼。

- 容器已修正為根據 `propagate_on_container_copy_assignment`、`propagate_on_container_move_assignment` 和 `propagate_on_container_swap`，甚至針對配置器宣告的 `is_always_equal` 來一律複製/移動/分頁配置器。

- 已新增容器合併的多載，並依 [P0083 "Splicing Maps And Sets"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) (P0083：接合對應和集合) 擷取接受右值容器的成員函式

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>\\r\\n => \\n 的 `std::basic_istream::read` 處理

`std::basic_istream::read` 已修正為不寫入部分所提供緩衝區轉存作為 \\r\\n => \\n 處理的一部分。 此變更放棄 Visual Studio 2017 15.8 中大小大於 4K 之讀取的效能優勢。 不過，避免每個字元三次虛擬呼叫的效率改善仍存在。

### <a name="stdbitset-constructor"></a>`std::bitset` 建構函式

`std::bitset` 建構函式不會再反向讀取大型位元集的一和零。

### <a name="stdpairoperator-regression"></a>`std::pair::operator=` 迴歸

已修正實作 [LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729) 時，`std::pair` 指派運算子導入的迴歸。 它現在可以再次正確接受可轉換為 `std::pair` 的類型。

### <a name="non-deduced-contexts-for-add_const_t"></a>`add_const_t` 的非推算內容

已修正 `add_const_t` 和相關函式本該是非推算內容的次要類型特性 Bug。 換言之，`add_const_t` 應該是 `typename add_const<T>::type` 的別名，而非 `const T` 的別名。

## <a name="update_162"></a>16.2 中的 Bug 修正和行為變更

### <a name="const-comparators-for-associative-containers"></a>關聯容器的 Const 比較子

已合併[set](../standard-library/set-class.md)、 [map](../standard-library/map-class.md)、[多重集](../standard-library/multiset-class.md)和[multimap](../standard-library/multimap-class.md)中的搜尋和插入程式碼，以減少程式碼大小。 插入作業現在會呼叫**const**比較仿函數的小於比較，與先前搜尋作業的方式相同。 下列程式碼會在 Visual Studio 2019 16.1 版和更早版本中進行編譯，但會在 Visual Studio 2019 版本16.2 中引發 C3848：

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

若要避免此錯誤，請將比較運算子設為**const**：

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="improvements_150"></a>Visual Studio 2017 RTW 中的一致性改進（版本15.0）

針對匯總的一般化**constexpr**和非靜態資料成員初始化（NSDMI）支援，現在已針對 c C++ + + 14 標準中新增的功能完成了 Visual Studio 2017 中的 Microsoft 編譯器。 不過，編譯器仍缺乏一些來自 C++11 和 C++98 標準的功能。 如需顯示編譯器目前狀態的資料表，請參閱[Microsoft C++語言一致性表格](../visual-cpp-language-conformance.md)。

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C + + 11：更多程式庫中的 Expression SFINAE 支援

編譯器會繼續改善其對 expression SFINAE 的支援，這是樣板引數推算和替代的必要條件，其中**decltype**和**constexpr**運算式可能會顯示為範本參數。 如需詳細資訊，請參閱 [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3) (Visual Studio 2017 RC 中的運算式 SFINAE 增強功能)。

### <a name="c14-nsdmi-for-aggregates"></a>C + + 14：匯總的 NSDMI

彙總是陣列或類別，但沒有使用者提供的建構函式、私人或受保護的非靜態資料成員、基底類別和虛擬函式。 從 C++14 開始，彙總可能會包含成員初始設定式。 如需詳細資訊，請參閱 [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html) (成員初始設定式和彙總)。

### <a name="c14-extended-constexpr"></a>C + + 14：延伸的**constexpr**

宣告為**constexpr**的運算式現在允許包含特定種類的宣告、if 和 switch 語句、loop 語句，以及存留期開始于 constexpr 運算式評估內的物件變化。 此外，已不再需要**constexpr**非靜態成員函式必須隱含**const**。 如需詳細資訊，請參閱 [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html) (放寬 constexpr 函式的條件約束)。

### <a name="c17-terse-static_assert"></a>C + + 17：簡易 `static_assert`

`static_assert` 的訊息參數是選擇性的。 如需詳細資訊，請參閱 [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf) (擴充 static_assert v2)。

### <a name="c17-fallthrough-attribute"></a>C++17：`[[fallthrough]]` 屬性

在 **/std:c++17** 模式中，`[[fallthrough]]` 屬性可以用於 switch 陳述式的內容，作為對意圖發生失敗行為之編譯器的提示。 此屬性可避免編譯器發出警告。 如需詳細資訊，請參閱 [\[\[fallthrough\]\] 屬性的用語](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf) \(英文\)。

### <a name="generalized-range-based-for-loops"></a>通用的範圍架構 for 迴圈

範圍式 for 迴圈不再需要 `begin()` 和 `end()` 傳回相同類型的物件。 此變更可讓 `end()` 傳回 [range-v3](https://github.com/ericniebler/range-v3) 中範圍所使用的 sentinel，以及已完成但尚未發行的「範圍技術規格」。 如需詳細資訊，請參閱 [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) (一般化範圍架構的 For 迴圈)。

## <a name="improvements_153"></a>15.3 中的一致性改善

### <a name="constexpr-lambdas"></a>constexpr lambdas

Lambda 運算式現在可用於常數運算式。 如需詳細資訊，請參閱 [C++ 中的 constexpr Lambda 運算式](../cpp/lambda-expressions-constexpr.md)。

### <a name="if-constexpr-in-function-templates"></a>**如果**函式樣板中的 constexpr

函數樣板可以包含**if constexpr**語句，以啟用編譯時間分支。 如需詳細資訊，請參閱 [if constexpr 陳述式](../cpp/if-else-statement-cpp.md#if_constexpr)。

### <a name="selection-statements-with-initializers"></a>使用初始設定式的選取範圍陳述式

**If**語句可能包含在語句本身的區塊範圍中引進變數的初始化運算式。 如需詳細資訊，請參閱[搭配初始設定式的 if 陳述式](../cpp/if-else-statement-cpp.md#if_with_init)。

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]` 與 `[[nodiscard]]` 屬性

當未使用實體時，新屬性 `[[maybe_unused]]` 會關閉警號。 如果捨棄函式呼叫的傳回值，`[[nodiscard]]` 屬性會建立警告。 如需詳細資訊，請參閱 [C++ 中的屬性](../cpp/attributes.md)。

### <a name="using-attribute-namespaces-without-repetition"></a>不重複使用屬性命名空間

新的語法讓您在屬性清單中可只用單一命名空間識別項。 如需詳細資訊，請參閱 [C++ 中的屬性](../cpp/attributes.md)。

### <a name="structured-bindings"></a>結構化繫結

現在可以在單一宣告中以值元件的個別名稱儲存值，前提是該值必須為陣列、`std::tuple` 或 `std::pair`，或具有公用非靜態資料成員。 如需詳細資訊，請參閱[結構化繫結](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf)與[從函式傳回多重值](../cpp/functions-cpp.md#multi_val)。

### <a name="construction-rules-for-enum-class-values"></a>**列舉類別**值的結構規則

當列舉的定義未導入列舉程式，且來源使用 list-initialization 語法時，從範圍列舉的基礎類型到列舉本身之間現在已有隱含/非縮小的轉換。 如需詳細資訊，請參閱[列舉類別值的建構規則](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)與 [Enumerations](../cpp/enumerations-cpp.md#no_enumerators)。

### <a name="capturing-this-by-value"></a>以值擷取 `*this`

Lambda 運算式中的 `*this` 物件現已可以值擷取。 此變更可用在平行及非同步作業中叫用 Lambda 的案例，特別是在較新的電腦架構上。 如需詳細資訊，請參閱 [Lambda 透過值將 \*this 擷取為 \[=,\*this\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html) \(英文\)。

### <a name="removing-operator-for-bool"></a>移除**bool**的 `operator++`

已不再支援**bool**類型的 `operator++`。 如需詳細資訊，請參閱[移除已取代的 operator++ (bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html) \(英文\)。

### <a name="removing-deprecated-register-keyword"></a>移除已淘汰的**register**關鍵字

先前已淘汰（並由編譯器忽略）的**register**關鍵字，現在已從語言中移除。 如需詳細資訊，請參閱[移除 register 關鍵字的已取代用途](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html) \(英文\)。

## <a name="improvements_155"></a>15.5 中的一致性改善

以 \[14] 標記的功能可無條件地使用，即使在 **/std:c++14** 模式中也一樣。

### <a name="new-compiler-switch-for-extern-constexpr"></a>**Extern constexpr**的新編譯器參數

在舊版的 Visual Studio 中，編譯器一律會提供**constexpr**變數內部連結，即使變數已標記為**extern**也一樣。 在 Visual Studio 2017 15.5 版中，新編譯器參數 [/Zc:externConstexpr](../build/reference/zc-externconstexpr.md) 啟用正確且符合標準的行為。 如需詳細資訊，請參閱 [extern constexpr 連結](#extern_linkage)。

### <a name="removing-dynamic-exception-specifications"></a>移除動態例外狀況規格

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) 動態例外狀況規格在 C++11 中已淘汰。 此功能已從 C++17 中移除，但已被取代的 `throw()` 規格仍會嚴格保留作為 `noexcept(true)` 的別名。 如需詳細資訊，請參閱[動態例外狀況規格移除和 noexcept](#noexcept_removal)。

### `not_fn()`

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` 取代 `not1` 和 `not2`。

### <a name="rewording-enable_shared_from_this"></a>重寫 `enable_shared_from_this`

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` 已在 c + + 11 中新增。 此 C++17 標準會更新規格，以更妥善處理某些極端的案例。 [14]

### <a name="splicing-maps-and-sets"></a>接合地圖與集合

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) 此功能讓您可從關聯容器 (即 `map`、`set`、`unordered_map`、`unordered_set`) 擷取節點，然後進行修改，再插回相同容器或使用相同節點類型的不同容器中。 (常見的使用案例是從 `std::map` 擷取節點，再變更金鑰，然後重新插入。)

### <a name="deprecating-vestigial-library-parts"></a>淘汰不必要的程式庫組件

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) C++ 標準程式庫有幾項功能多年來逐漸被較新的功能所取代，或是發現不實用或有問題。 這些功能在 C++17 中已正式被取代。

### <a name="removing-allocator-support-in-stdfunction"></a>移除 `std::function` 中的配置器支援

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) 在 C++17 之前，類別範本 `std::function` 具有數個使用配置器引數的建構函式。 不過，在此內容中使用配置器會有問題，而且語意不清。 已移除有問題的建構函式。

### <a name="fixes-for-not_fn"></a>`not_fn()` 的修正

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)`std::not_fn` 的新寫法支援在用於包裝函式引動過程時傳播值類別。

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`、 `shared_ptr<T[N]>`

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) 將程式庫基本概念中的 `shared_ptr` 變更合併到 C++17。 [14]

### <a name="fixing-shared_ptr-for-arrays"></a>修正陣列的 `shared_ptr`

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) 修正陣列的 shared_ptr 支援。 [14]

### <a name="clarifying-insert_return_type"></a>釐清 `insert_return_type`

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) 具有唯一金鑰的關聯容器和具有唯一金鑰的未排序容器包含傳回巢狀型別 `insert_return_type` 的成員函式 `insert`。 該傳回型別現在已定義為在容器的 Iterator 和 NodeType 上參數化的類型特製化。

### <a name="inline-variables-for-the-standard-library"></a>標準程式庫的內嵌變數

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>附錄 D 已淘汰的功能

C++ 標準的附錄 D 包含已淘汰的所有功能，包括 `shared_ptr::unique()`、`<codecvt>` 和 `namespace std::tr1`。 當 **/std:c++17** 編譯器參數已設定時，附錄 D 中幾乎所有標準程式庫功能都會標記為已淘汰。 如需詳細資訊，請參閱[附錄 D 中的標準程式庫功能標記為已被取代](#annex_d)。

`<experimental/filesystem>` 中的 `std::tr2::sys` 命名空間現在於 **/std:c++14** 下預設會發出取代警告，且在 **/std:c++17** 下預設已移除。

藉由避免使用非標準的延伸模組 (類別內明確特製化) 來改善 `<iostream>` 中的一致性。

標準程式庫現在會於內部使用變數樣板。

標準程式庫已更新，以回應 c + + 17 編譯器變更，包括在類型系統中新增**noexcept** ，以及移除動態例外狀況規格。

## <a name="improvements_156"></a>15.6 中的一致性改善

### <a name="c17-library-fundamentals-v1"></a>C++17 程式庫基本概念 V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) 將 C++17 的程式庫基本技術規格合併至標準。 涵蓋對 \<experimental/tuple>、\<experimental/optional>、\<experimental/functional>、\<experimental/any>、\<experimental/string_view>、\<experimental/memory>、\<experimental/memory_resource> 及 \<experimental/algorithm> 的更新。

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C + + 17：改善標準程式庫的類別樣板引數推斷

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) 將 `adopt_lock_t` 移至參數清單前，使 `scoped_lock` 能夠一致使用 `scoped_lock`。 允許 `std::variant` 建構函式在更多案例中參與多載解析，以啟用複製指派。

## <a name="improvements_157"></a>15.7 中的一致性改善

### <a name="c17-rewording-inheriting-constructors"></a>C + + 17：改寫繼承的函式

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) \(英文\) 指定了為建構函式命名的 **using** 宣告，現在會對衍生的類別顯示相應的基底類別建構函式，而不宣告額外的衍生類別建構函式。 此重寫是來自 C++14 的變更。 在 Visual Studio 2017 15.7 版及更新版本中，於 **/std:c++17** 模式中，在 C++14 有效以及使用繼承建構函式的程式碼，可能會失效或有不同的語意。

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

下列範例顯示 Visual Studio 15.7 中的 **/std:c++17** 行為：

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

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

如果基類的函式不是公用的，但衍生類別可存取，則在 Visual Studio 2017 版本15.7 中的 **/std： c + + 17**模式下，您就無法再使用空的大括弧來初始化衍生類型的物件。
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
下列範例顯示 **/std:c++17** 模式中，Visual Studio 15.7 內的 C++17 行為：

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

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

在 **/std:c + + 17** 模式中，編譯器現在可以推斷以 **auto** 宣告之非類型樣本引數的類型：

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

這項新功能的影響之一，包括有效的 C++14 程式碼可能失效或有不同的語意。 例如，部分先前無效的多載現在會變得有效。 下列範例顯示因為對 `example(p)` 的呼叫已繫結至 `example(void*);`，而編譯的 C++14 程式碼。 在 Visual Studio 2017 15.7 版中，在 **/std:c++17** 模式內的 `example` 函式範本是最佳符合項。

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

下列範例顯示 **/std:c++17** 模式中的 Visual Studio 15.7 C++17 程式碼：

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C + + 17：基底字元串轉換（部分）

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) 介於整數與字串之間，以及浮點數與字串之間的低階、無關地區設定的函式轉換。

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C + + 20：避免不必要的衰減（部分）

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) 為 "decay'' 的概念與單純移除常式或參考限定詞之間的差異新增區別。  新增類型特徵 `remove_reference_t` 來取代部分內容中的 `decay_t`。 Visual Studio 2019 中已實作 `remove_cvref_t` 的支援。

### <a name="c17-parallel-algorithms"></a>C + + 17：平行演算法

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) 平行處理原則 TS 已併入標準，但有些微修改。

### <a name="c17-hypotx-y-z"></a>C++17：`hypot(x, y, z)`

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) 新增三個新多載到 `std::hypot`，針對 **float**、**double** 及 **long double** 類型，每個都有三種輸入參數。

### <a name="c17-filesystem"></a>C++17：\<filesystem>

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) 為標準採用檔案系統 TS，其中包括些許用詞修改。

### <a name="c17-mathematical-special-functions"></a>C + + 17：數學特殊函數

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) 為 \<cmath> 標頭將先前技術規格的數學特殊函式納入標準。

### <a name="c17-deduction-guides-for-the-standard-library"></a>C + + 17：標準程式庫的推斷指南

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) 更新 STL 以利用 C++17 對 [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) 的採用，這為類別範本引數推斷新增了支援。

### <a name="c17-repairing-elementary-string-conversions"></a>C + + 17：修復基底字元串轉換

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) 將新的基礎字串轉換函式從 P0067R5 移至新標頭 \<charconv>，並進行了其他改善，包括將錯誤處理函式改為使用 `std::errc` 而非 `std::error_code`。

### <a name="c17-constexpr-for-char_traits-partial"></a>C + + 17： `char_traits` 的**constexpr** （部分）

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) \(英文\) 對 `std::traits_type` 成員函式 `length`、`compare` 及 `find` 進行變更，讓常數運算式中可使用 `std::string_view`。 (在 Visual Studio 2017 15.6 版中，僅支援 Clang/LLVM。 在 15.7 版 Preview 2 中，也幾乎完全支援 CIXX。)

## <a name="improvements_159"></a>15.9 中的一致性改善

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>運算子的從左到右評估順序 `->*`、`[]`、`>>` 與 `<<`

從 C++17 開始，運算子的運算元 `->*`、`[]`、`>>` 與 `<<` 必須以從左到右的順序評估。 編譯器在兩種案例下無法保證此順序：

- 當其中一個運算元運算式是由值傳遞的物件或包含由值傳遞的物件，或

- 當使用 **/clr** 編譯且其中一個運算元事物件或陣列元素的欄位時。

編譯器在無法保證從左到右的評估時會發出警告 [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017)。 只有指定 **/std:c++17** 或更新版本時，編譯器才會產生此警告，因為這些運算元的從左到右順序需求是在 C++17 中引進的。

若要解決此警告，請先考慮運算元的從左到右評估是否必要，例如當評估運算元可能會產生與順序有關的副作用時。 在許多案例中，運算元評估順序沒有顯著的作用。 若評估順序必須是從左到右，請考慮您是否能改為依 const 參考傳遞運算元。 此變更會消除下列程式碼範例中的警告：

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

## <a name="update_150"></a> Visual Studio 2017 RTW (15.0 版) 中的 Bug 修正

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 會針對使用初始設定式清單建立物件的相關錯誤，正確地引發編譯器錯誤，Visual Studio 2015 中攔截不到這些錯誤，它們可能導致當機或未定義執行階段行為。 根據 N4594 13.3.1.7p1，在 copy-list-initialization 中，編譯器需要考慮使用明確建構函式來進行多載解析，但必須在選擇該多載時引發錯誤。

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

在 Visual Studio 2015 中，編譯器會使用與一般 copy-initialization 相同的方式錯誤地處理 copy-list-initialization；它只會考慮轉換建構函式來進行多載解析。 在下列範例中，Visual Studio 2015 會選擇 MyInt(23)，但 Visual Studio 2017 會正確地引發錯誤。

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

Visual Studio 2017 現在會發出類別或結構中所宣告之被取代 typedef 的正確警告。 下列範例是在 Visual Studio 2015 中編譯，而不會發出警告，但在 Visual Studio 2017 中產生 C4996。

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

### <a name="constexpr"></a>**constexpr**

在 constexpr 內容中條件式評估作業的左運算元無效時，Visual Studio 2017 會正確地引發錯誤。 下列程式碼可使用 Visual Studio 2015 編譯，但不能用 Visual Studio 2017 編譯 (C3615 constexpr 函式 'f' 無法產生常數運算式)：

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

若要更正錯誤，請將 `array::size()` 函式宣告為**constexpr** ，或從 `f`移除**constexpr**辨識符號。

### <a name="class-types-passed-to-variadic-functions"></a>傳遞給 variadic 函式的類別類型

在 Visual Studio 2017 中，傳遞給 variadic 函式的類別或結構 (例如 printf) 必須可完整複製。 傳遞這類物件時，編譯器只會進行位元複製，而且不會呼叫建構函式或解構函式。

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

針對使用 CString 所建置和管理的字串，應該使用提供的 `operator LPCTSTR()` 將 CString 物件轉換為格式字串所預期的 C 指標。

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

若要更正錯誤，請將 `operator int()` 宣告為**const**。

### <a name="access-checking-on-qualified-names-in-templates"></a>範本中限定名稱的存取檢查

舊版編譯器未對部分範本內容中限定名稱檢查存取。 此問題可能會干擾預期 SFINAE 行為，其中，替代預期會因無法存取名稱而失敗。 它可能會在執行階段因編譯器錯誤地呼叫運算子的錯誤多載而導致當機或意外行為。 在 Visual Studio 2017 中，會引發編譯器錯誤。 特定錯誤可能會不同，但通常為「C2672 找不到相符的多載函式」。 下列程式碼是在 Visual Studio 2015 中編譯，但在 Visual Studio 2017 中引發錯誤：

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

在 Visual Studio 2015 和以前版本中，範本出現在範本參數清單時 (例如，作為預設範本引數或非類型範本參數的一部分)，編譯器無法診斷出遺漏範本引數清單。 此問題可能會導致無法預期的行為，包括編譯器當機或意外執行階段行為。 下列程式碼在 Visual Studio 2015 中會編譯，但在 Visual Studio 2017 中會產生錯誤。

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Expression-SFINAE

為了支援運算式 SFINAE，編譯器現在會在宣告範本而不是具現化時，剖析**decltype**引數。 因此，如果在 decltype 引數中發現非相依特製化，不會延遲到具現化期間。 系統會立即處理，而且會在當下診斷出任何產生的錯誤。

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

根據 C++ 標準，宣告於匿名命名空間中的類別具有內部連結，這表示無法將它匯出。 在 Visual Studio 2015 和更早的版本中，並未強制執行此規則。 在 Visual Studio 2017 中，會部分強制執行此規則。 下列範例會在 Visual Studio 2017 中引發這個錯誤：「錯誤 C2201: const anonymous namespace::S1::vftable: 必須具有外部連結以便匯出/匯入。」

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

在 Visual Studio 2015 和以前版本中，在某些情況下，編譯器會將預設屬性錯誤地識別為預設索引子。 您可以使用識別碼**預設值**來存取屬性，藉此解決此問題。 因應措施本身會在**預設**為 c + + 11 中的關鍵字引進之後變得有問題。 在 Visual Studio 2017 中，已修正需要因應措施的 bug，而且編譯器現在會在使用**預設**值來存取類別的預設屬性時引發錯誤。

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

## <a name="update_153"></a>15.3 中的 Bug 修正

### <a name="calls-to-deleted-member-templates"></a>對已刪除之成員範本的呼叫

在舊版的 Visual Studio 中，編譯器在某些情況下針對呼叫已刪除之成員範本的語式錯誤會無法發出錯誤。而可能造成在執行階段當機。 下列程式碼現在會產生 C2280「'int S\<int>::f\<int>(void)': 嘗試參考刪除的函式」：

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

若要修正錯誤，請將 `i` 宣告為**int**。

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

編譯器如果可以在編譯時期時，知道含有已刪除 copy ctor 的原生物件會在原生和 Managed 界限之間以值傳遞，就會發出警告。 針對編譯器在編譯時期不知道的那些情況，其會插入執行階段檢查，以便程式會在發生語式錯誤的封送處理時，立即呼叫 `std::terminate`。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生警告 C4606「'A': 跨越原生與 Managed 界限以值傳遞引數必須使用有效的複製建構函式。 否則不會定義執行階段行為。

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

針對實驗和意見反應所發行的 WinRT API 會附有 `Windows.Foundation.Metadata.ExperimentalAttribute`。 在 Visual Studio 2017 15.3 版中，編譯器在遇到該屬性時，會產生警告 C4698。 舊版 Windows SDK 中的一些 API 已附有該屬性，而呼叫這些 API 現在會觸發此編譯器警告。 新版 Windows SDK 已將所有隨附的類型移除該屬性，但如果您目前使用舊版 SDK，將需隱藏這些警告，才能呼叫隨附的類型。

下列程式碼會產生警告 C4698：「'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' 僅供評估之用。後續版本可能會變更或移除此功能」：

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

Visual Studio 2017 15.3 版在遇到未在類別中宣告之樣板成員函式的非正規定義時會產生錯誤。 下列程式碼現在會產生錯誤 C2039：'f': 不是 'S' 的成員：

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

### <a name="attempting-to-take-the-address-of-this-pointer"></a>嘗試採用**這個**指標的位址

在C++中，**這**是 X 類型指標的 x prvalue。您無法接受**這個**位址，或將它系結至左值參考。 在舊版的 Visual Studio 中，編譯器可讓您使用轉換以避開此限制。 在 Visual Studio 2017 15.3 版中，編譯器會產生錯誤 C2664。

### <a name="conversion-to-an-inaccessible-base-class"></a>轉換成無法存取的基底類別

當您嘗試將類型轉換為無法存取的基底類別時，Visual Studio 2017 15.3 版會產生錯誤。 編譯器現在會引發「錯誤 C2243: 'type cast': 從 'D *' 至 'B *' 的轉換已存在，但無法存取」。 下列程式碼是語式錯誤的，且可能在執行階段造成當機。 現在編譯器遇到如下程式碼時會產生 C2243：

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

範本類別中成員函式的程式碼外部定義不允許預設引數。 編譯器會在 **/permissive** 下發出警告，且在 [/permissive-](../build/reference/permissive-standards-conformance.md) 下發出硬體錯誤警告。

在舊版的 Visual Studio 中，下列語式錯誤的程式碼可能會導致執行階段當機。 Visual Studio 2017 15.3 版會產生警告 C5034：'A\<T>::f': 類別範本成員的非正規定義不可使用預設引數：

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

在 Visual Studio 2017 15.3 版中，使用 `offsetof(T, m)` (其中 *m* 是「複合成員指示項」) 會在您使用 **/Wall** 選項編譯時產生警告。 下列程式碼的語式錯誤，且可能在執行階段造成當機。 Visual Studio 2017 15.3 版會產生「警告 C4841: 使用了非標準擴充：offsetof 中有複合成員指示項」：

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

在 Visual Studio 2017 15.3 版中，使用 `offsetof(T, m)` (其中 *m* 代表靜態資料成員或成員函式) 會導致錯誤。 下列程式碼會產生「錯誤 C4597: 未定義的行為: offsetof 套用至成員函式 'example'」和「錯誤 C4597: 未定義的行為: offsetof 套用至靜態資料成員 'sample'」：

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

### <a name="declspec"></a> 針對 `__declspec` 屬性的新警告

在 Visual Studio 2017 15.3 版中，如果 `__declspec(...)` 套用於 `extern "C"` 連結規格前，編譯器就不再略過該屬性。 編輯器之前會忽略該屬性，這可能隱含執行階段。 當 **/Wall** 和 **/WX** 選項設定時，下列程式碼會產生「警告 C4768: 連結規格前的 __declspec 屬性已略過」：

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

若要修正此警告，請先加入`extern "C"`：

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

在15.3 中，此警告預設為關閉，但在15.5 中預設為開啟，而且只會影響使用 **/Wall** **/wx**編譯的程式碼。

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype**和呼叫已刪除的析構函數

在舊版的 Visual Studio 中，編譯器未偵測到與**decltype**相關聯之運算式的內容中發生已刪除的析構函式的呼叫。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生「錯誤 C2280: 'A\<T>::~A(void)'：嘗試參考已刪除的函式」：

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

Visual Studio 2017 RTW 版本有一個回歸，如果C++ **常數**變數未初始化，編譯器不會發出診斷。 Visual Studio 2017 15.3 版已修正此迴歸。 下列程式碼現在會產生「警告 C4132: 'Value': 應初始化常數物件」：

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

該警告在 **/Wv:18** 下會排除，且在警告層級 W2 下預設為開啟。

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

舊版編譯器在同時透過使用宣告和引數相依查閱找到多個候選項目時，有時偵測不到語意模糊。 此失敗會導致選擇錯誤的多載和未預期的執行階段行為。 在下列範例中，Visual Studio 2017 15.3 版會正確引發「C2668 'f': 多載函式的語意模糊呼叫」：

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

區域函式宣告會將函式宣告隱藏在封閉範圍中，停用引數相依查閱。 不過，舊版編譯器在這種情況下會執行引數相依查閱，有可能導致選擇錯誤的多載和未預期的執行階段行為。 錯誤通常是因為區域函式宣告的簽章不正確而發生。 在下列範例中，Visual Studio 2017 15.3 版會正確引發「C2660 'f': 函式不接受兩個引數」：

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

類別成員會依其宣告的順序初始化，而不是依它們在初始設定式清單中出現的順序。 當初始設定式清單的順序和宣告順序不一致時，舊版編譯器未發出警告。 如果某個成員的初始化依存於清單中另一個已初始化的成員，此問題可能導致未定義的執行階段行為。 在下列範例中，Visual Studio 2017 15.3 版 (使用 **/Wall**) 會引發「警告 C5038: 資料成員 'A::y' 會在資料成員 'A::x' 之後初始化」：

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

若要修正此問題，請將初始設定式清單排列成和宣告一樣的順序。 當一或兩個初始設定式參考基底類別成員時，就會引發類似的警告。

此警告預設為關閉，且只影響以 **/Wall** 編譯的程式碼。

## <a name="update_155"></a>15.5 中的錯誤修正和其他行為變更

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

上述範例的問題在於類型中有兩個差異 (const 與非 const 以及 pack 與非 pack)。 若要排除編譯器錯誤，請移除其中一個差異。 如此即可讓編譯器明確地排序函式。

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

陣列或函式類型參考的處理常式從未可以比對所有例外狀況物件。 編譯器現在會正確地接受這項規則，並引發層級 4 警告。 此外，使用 **/Zc:strictStrings** 時，不會再將 `char*` 或 `wchar_t*` 的處理常式與字串常值進行比對。

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

### <a name="tr1"></a>`std::tr1` 命名空間已被取代

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

### <a name="annex_d"></a> 附錄 D 中的標準程式庫功能標記為已淘汰

當 **/std:c++17** 模式編譯器參數設定時，附錄 D 中幾乎所有標準程式庫功能都會標記為已淘汰。

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

在 Visual Studio 2017 15.5 版中，C 編譯器不再發出警告 C4001 和 C4179。 先前，只會在 **/Za** 編譯器參數下發出這些警告。  由於自 C99 起，單行註解已成為 C 標準的一部分，因此不再需要這些警告。

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

如果程式碼不需要與舊版相容，您可以藉由移除 C4001/C4179 隱藏項目來避免出現警告。 如果程式碼確實需要與舊版相容，則只隱藏 C4619。

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

### <a name="extern_linkage"></a>Extern constexpr 連結

在舊版的 Visual Studio 中，編譯器一律會提供**constexpr**變數內部連結，即使變數已標記為**extern**也一樣。 在 Visual Studio 2017 15.5 版中，新的編譯器參數 ( **/Zc:externConstexpr**) 讓行為可正確且符合標準。 此行為最後終究會成為預設值。

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

如果標頭檔包含宣告為**extern constexpr**的變數，則必須將它標記為 `__declspec(selectany)`，才能正確結合其重複宣告：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>**typeid**不能用於不完整的類別類型

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

### <a name="noexcept_removal"></a>動態例外狀況規格移除和**noexcept**

在 c + + 17 中，`throw()` 是**noexcept**的別名，`throw(<type list>)` 和 `throw(...)` 會移除，而某些類型可能包含**noexcept**。 此變更會導致符合 C++14 或更早版本之程式碼的來源相容性。 在一般情況下，您可以使用 **/zc： noexceptTypes-** switch 來還原為 c + + 14 版的**noexcept** 。 它可讓您更新原始程式碼以符合 C++17，而不需要同時重寫所有 `throw()` 程式碼。

編譯器現在也會診斷 C++17 模式宣告中或使用 [/permissive-](../build/reference/permissive-standards-conformance.md) 的更多不相符例外狀況規格，並發出新的警告 C5043。

在 Visual Studio 2017 15.5 版中，當套用 **/std:c++17** 參數時，下列程式碼會產生 C5043 和 C5040：

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

若要在仍然使用/std 時移除錯誤 **： c + + 17**，請將 **/zc： noexceptTypes-** 參數新增至命令列，或更新您的程式碼以使用**noexcept**，如下列範例所示：

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

靜態 constexpr 資料成員現在隱含內嵌，這表示其在類別內的宣告現在會是其定義。 對靜態 constexpr 資料成員使用程式碼外部定義是多餘的，現在已被取代。 在 Visual Studio 2017 15.5 版中，當套用 **/std:c++17** 參數時，下列程式碼現在會產生警告 C5041「'size': 不需要 constexpr 靜態資料成員的非正規定義，且在 C++17 中已淘汰」：

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)` 警告 C4768 現在預設會開啟

在 Visual Studio 2017 15.3 版中已新增警告，但預設為關閉。 在 Visual Studio 2017 15.5 版中，預設會啟用該警告。 如需詳細資訊，請參閱[針對 \_\_declspec 屬性的新警告](#declspec)。

### <a name="defaulted-functions-and-__declspecnothrow"></a>預設函式和 `__declspec(nothrow)`

當對應的基底/成員函式允許例外狀況時，編譯器之前允許使用 `__declspec(nothrow)` 宣告預設函式。 此行為違反 C++ 標準，而且可能在執行階段導致未定義的行為。 如果不符合例外狀況規格，此標準會要求將這類函式定義為已刪除。  在 **/std： c + + 17**底下，下列程式碼會引發 C2280*嘗試參考已刪除的函式。因為明確的例外狀況規格與隱含宣告不相容，所以已隱含刪除函式。*

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

### <a name="noexcept-and-partial-specializations"></a>**noexcept**和部分特製化

使用類型系統中的**noexcept**時，比對特定「可呼叫」類型的部分特製化可能無法編譯或選擇主要範本，因為指標對 noexcept 函式缺少部分特製化。

在這種情況下，您可能需要新增額外的部分特製化，以處理**noexcept**函式指標和成員函式的**noexcept**指標。 這些多載只在 **/std:c++17** 模式中才合法。 如果必須維持與 C++14 舊版相容，而且您正撰寫的程式碼有其他人使用，則您應該使用 `#ifdef` 指示詞括住這些新的多載。 如果您想在獨立模組中工作，則可以直接使用 **/Zc:noexceptTypes-** 參數進行編譯，而不需要使用 `#ifdef` 成立條件。

下列程式碼在 **/std:c++14** 下會編譯，但在 **/std:c++17** 下會失敗，並發生「錯誤 C2027: 使用未定義的類型 'A\<T>'」：

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

下列程式碼在 **/std:c++17** 下會成功，原因是編譯器會選擇新的部份特製化 `A<void (*)() noexcept>`：

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

## <a name="update_157"></a>15.7 中的錯誤修正和其他行為變更

### <a name="c17-default-argument-in-the-primary-class-template"></a>C + + 17：主要類別範本中的預設引數

此行為變更是[類別範本的範本引述推算 - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) \(英文\) 的先決條件。

在此之前，編譯器會忽略主要類別範本中的預設引數：

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

在 Visual Studio 2017 15.7 版的 **/std:c++17** 模式中，將不再忽略預設引數：

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>相依名稱解析

此行為變更是[類別範本的範本引述推算 - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) \(英文\) 的先決條件。

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

Visual Studio 2017 15.7 版（在 **/std： c + + 17**模式中）需要在 D 的 using 語句中**使用** **typename**關鍵字。若沒有**typename**，編譯器會引發警告 C4346： *' B < T\*>：： type '：相依名稱不是類型*，錯誤 C2061：*語法錯誤：識別碼 ' type '* ：

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

在 Visual Studio 2017 15.7 版的 **/std:c++17** 模式中，警告等級 C4834 (「捨棄屬性為 'nodiscard' 之函式的傳回值」) 已從 W3 增加至 W1。 您可以停用轉換為**void**的警告，或將 **/wd： 4834**傳遞給編譯器

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Variadic 範本建構函式基底類別初始化清單

在先前的 Visual Studio 版本中，有一個缺少範本引數的 variadic 範本建構函式基底類別初始化清單錯誤地被允許而未產生錯誤。 在 Visual Studio 2017 15.7 版中，會引發編譯器錯誤。

Visual Studio 2017 15.7 版中的下列程式碼範例會引發*錯誤 C2614: D\<int>: 成員初始化不合法: 'B' 不是基底或成員類別*

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

若要修正錯誤，請將 B() 運算式變更為 B\<T>()。

### <a name="constexpr-aggregate-initialization"></a>**constexpr**匯總初始化

舊版C++編譯器不正確地處理了**constexpr**匯總初始化;它接受不正確程式碼，其中匯總-init 清單具有太多元素，並為其產生不正確的 codegen。 以下程式碼為此類程式碼的範例：

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

在 Visual Studio 2017 15.7 版 Update 3 和更新版本中，上述的範例將會引發「C2078 太多初始設定式」。 以下範例顯示如何修正該程式碼。 當使用巢狀大括弧初始化清單將 `std::array` 初始化時，讓內部陣列使用自己的大括弧清單：

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

## <a name="update_158"></a>15.8 中的 Bug 修正和行為變更

Visual Studio 2017 版本 15.8 中的編譯器變更，全都落在修正 Bug 與行為變更的這一類別中，如下所示：

###<a name="typename-on-unqualified-identifiers"></a>非限定識別碼上的**typename**

在[/permissive-](../build/reference/permissive-standards-conformance.md)模式中，編譯器不再接受別名範本定義中不合格識別碼的偽**typename**關鍵字。 下列程式碼現在會產生 C7511「T': 'typename' 關鍵字後面必須接著限定名稱」：

```cpp
template <typename T>
using  X = typename T;
```

若要修正此錯誤，請將第二行變更為 `using  X = T;`。

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>別名範本定義右側的 `__declspec()`

不再允許 [__declspec](../cpp/declspec.md) 位於別名範本定義的右側。 系統先前接受此程式碼，但編譯器會忽略它，且永遠不會在使用別名時產生淘汰警告。

可以改為使用標準 C++ 屬性 [\[\[deprecated\]\]](../cpp/attributes.md)，並將從 Visual Studio 2017 15.6 版開始採用此屬性。 下列程式碼現在會產生 C2760「語法錯誤：非預期的語彙基元 '__declspec'，必須是類型規範」：

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

表示這種情況的其中一個方法是使用相依基底類別的查詢。 之前，編譯器允許使用相依基底類別中定義的名稱，因為在解析所有類型時，會在具現化期間查閱這些名稱。 現在，該程式碼會被視為錯誤。 在這些情況下，您可以強制在具現化時期查閱變數，方法是使用基底類別類型進行限定，或以其他方式使其相依，例如新增 `this->` 指標。

在 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式中，下列程式碼現在會引發 C3861：「'base_value': 找不到識別碼」：

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

若要修正此錯誤，請將 `return` 陳述式變更為 `return this->base_value;`。

**注意：** 在 Boost Python 程式庫中，長久以來 [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp) 中就有向前範本宣告的 MSVC 特定因應措施。 從 Visual Studio 2017 15.8 版 (_MSC_VER=1915) 開始，在 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式下，MSVC 編譯器就會正確地執行引數相依名稱查閱 (ADL) 且行為與其他編譯器一致，讓此因應措施逐漸變得沒必要。 若要避免錯誤「C3861: 'unwind_type': 找不到識別項」，請參閱 Boost 存放庫中的 [PR 229](https://github.com/boostorg/python/pull/229) \(英文\) 以更新標頭檔。 我們已修補 [vcpkg](../build/vcpkg.md) Boost 套件，因此若您是從 vcpkg 取得或升級 Boost 來源，則不需要個別套用補充程式。

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>命名空間 `std` 中的向前宣告和定義

C++ 標準不允許使用者將向前宣告或定義新增到命名空間 `std` 中。 將宣告或定義新增至命名空間 `std` 或新增至命名空間 `std` 內的命名空間，現在會導致發生未定義的行為。

在未來的某個時間，Microsoft 將會移動一些標準程式庫類型定義所在的位置。 此變更會中斷將向前宣告新增至命名空間 `std` 的現有程式碼。 新警告 C4643 有助於識別這類來源問題。 警告在 **/default** 模式中已啟用且預設為關閉。 它會影響使用 **/Wall** 或 **/WX** 編譯的程式。

下列程式碼現在引發 C4643：「C++ 標準不允許在命名空間 std 中向前宣告 'vector'」。

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

C++ 標準建議編譯器應該在建構函式委派給其本身時發出診斷。 Microsoft C++ 編譯器在 [/std:c++17](../build/reference/std-specify-language-standard-version.md) 和 [/std:c++latest](../build/reference/std-specify-language-standard-version.md) 模式中現在會引發 C7535：「'X::X': 委派建構函式呼叫其本身」。

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

[offsetof](../c-runtime-library/reference/offsetof-macro.md) 傳統上使用需要 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) 的巨集來實作。 此用法在需要常數運算式的內容中並不合法，但 Microsoft C++ 編譯器傳統上會允許此做法。 隨附為標準程式庫一部分的 `offsetof` 巨集會正確使用編譯器內建函式 ( **__builtin_offsetof**)，但有許多人已使用巨集技巧來定義自己的 `offsetof`。

在 Visual Studio 2017 15.8 版中，編譯器會限制預設模式中可以顯示這些 `reinterpret_cast` 運算子的區域，以協助程式碼符合標準的 C++ 行為。 在 [/permissive-](../build/reference/permissive-standards-conformance.md) 下，條件約束更為嚴格。 在需要常數運算式的地方使用 `offsetof` 的結果，可能會導致程式碼發出警告 C4644「在常數運算式中使用以巨集為基礎的 offsetof 模式是非標準用法；請改為使用 C++ 標準程式庫中定義的 offsetof」或 C2975「範本引數無效，必須是編譯時期常數運算式」。

下列程式碼會在 **/default** 和 **/std:c++17** 模式中引發 C4644，並在 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式中引發 C2975：

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

若要修正此錯誤，請使用透過 \<cstddef> 定義的 `offsetof`：

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

在 Visual Studio 2017 15.8 版的 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式中，下列程式碼會引發 C3770「'const S': 不是有效的基底類別」：

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>樣板**關鍵字和**嵌套名稱規範

在[/permissive-](../build/reference/permissive-standards-conformance.md)模式中，編譯器現在會要求**樣板關鍵字出現**在相依的嵌套名稱規範後面的範本名稱前面。

下列程式碼在 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式中現在會引發 C7510：「'example': 使用相依範本名稱時，前面必須加上 'template'。注意：請查看所編譯之類別範本具現化 'X<T>' 的參考」：

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

若要修正錯誤，請將**template**關鍵字新增至 `Base<T>::example<int>();` 語句，如下列範例所示：

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

## <a name="update_159"></a>15.9 中的 Bug 修正和行為變更

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

在 Visual Studio 2017 15.9 版的 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式中，編譯器會引發 C3861：「'from_template': 找不到識別碼」.

若要修正此錯誤，請在 `from_template_t` 之前宣告 `from_template`。

### <a name="modules-changes"></a>模組變更

在 Visual Studio 2017 15.9 版中，每當模組的命令列選項在模組建立端與模組取用端之間不一致時，編譯器都會引發 C5050。 下列範例中有兩個問題：

- 取用端 (main.cpp) 上未指定 **/EHsc** 選項。

- 建立端上的 C++ 版本是 **/std:c++17**，而在取用端上則是 **/std:c++14**。

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

編譯器會針對這兩種情況引發 C5050：*警告 C5050：匯入模組 ' ' 時可能不相容的C++環境：不相符的版本。 目前的 "201402" 模組版本 "201703"* 。

每當 .ifc 檔案遭竄改時，編譯器都會引發 C7536。 模組介面的標頭下方會包含內容的 SHA2 雜湊。 匯入時，.ifc 檔案會以相同方式雜湊，然後與標頭中提供的雜湊對照。 如果兩者不相符，則會引發錯誤則 c7536： *ifc 失敗的完整性檢查。 預期的 SHA2： ' 66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6 '* 。

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>涉及別名及非推算內容的部分排序

涉及非推算內容中別名的部分排序規則裡發生實作發散。 在下列範例中，GCC 及 Microsoft C++ 編譯器 (在 [/permissive-](../build/reference/permissive-standards-conformance.md) 模式中) 於 Clang 接受程式碼時會引發錯誤。

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

若要避免此錯誤，請從函式 `f()`的明確具現化移除**constexpr**辨識符號。

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Visual Studio 2015 中的 C++ 一致性改善

如需到 Visual Studio 2015 Update 3 為止的所有完整一致性改善清單，請參閱 [Visual C++ 2003 至 2015 的新功能](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)。

::: moniker-end

## <a name="see-also"></a>請參閱

[Microsoft C++語言一致性資料表](../visual-cpp-language-conformance.md)
