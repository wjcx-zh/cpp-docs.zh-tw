---
title: C++ 一致性改善
ms.date: 05/16/2019
description: Visual Studio 2019 的 Microsoft C++ 正在向完全符合 C++20 語言標準邁進。
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 02b778f10ad94342c922a4e79a856cc2a7d53076
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451213"
---
# <a name="c-conformance-improvements-in-visual-studio-2019-rtw-and-version-161improvements161"></a>Visual Studio 2019 RTW 和 [16.1](#improvements_161) 版的 C++ 一致性改善

## <a name="improvements-in-visual-studio-2019-rtw"></a>Visual Studio 2019 RTW 的改善

Visual Studio 2019 RTW 包含下列一致性改善、Bug 修正和 Microsoft C++ 編譯器 (MSVC) 的行為變更。

**注意：** 在編譯器和 IntelliSense 的 C++20 實作完成前，C++20 的功能都可以在 `/std:c++latest` 模式中取得。 屆時，即會推出 `/std:c++20` 編譯器模式。

### <a name="improved-modules-support-for-templates-and-error-detection"></a>改善的範本和錯誤偵測模組支援

模組現已正式使用 C++20 標準。 Visual Studio 2017 15.9 版已新增改善的支援。 如需詳細資訊，請參閱 [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/) (C++ 模組與 MSVC 2017 15.9 版的更佳範本支援和錯誤偵測)。

### <a name="modified-specification-of-aggregate-type"></a>已修改彙總類型的規格

C++20 已變更彙總類型的規格 (請參閱 [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1) (禁止使用使用者宣告的建構函式彙總))。 在 Visual Studio 2019 的 `/std:c++latest` 下，任何具有使用者宣告建構函式的類別 (例如包括建構函式宣告的 `= default` 或 `= delete`) 都不是彙總。 過去，只有使用者所提供建構函式才可取消讓類別成為彙總的資格。 這項變更會對如何初始化這類類型的方式加諸額外限制。

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

### <a name="partial-support-for-operator-"></a>部分支援運算子 <=>

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

為避免發生錯誤，請在有問題程式行的最後一個括弧前插入空格：`U<&S::operator<= > u;`。

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>參考具有不相符 cv 限定詞的類型

MSVC 過去允許直接從最高層級底下具有不相符 cv 限定詞的類型繫結參考。 這可能會允許修改參考本應參考的 const 資料，而編譯器現在會建立標準所需的暫存。 在 Visual Studio 2017 中，下列程式碼在編譯時不會發出警告。 在 Visual Studio 2019 中，編譯器會引發「警告 C4172：\<func:#1 "?PData@X@@QBEABQBXXZ">，傳回區域變數或暫存的位址」  。

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
### <a name="reinterpretcast-from-an-overloaded-function"></a>來自多載函式的 `reinterpret_cast`

`reinterpret_cast` 的引數不是允許多載函式位址的內容之一。 在 Visual Studio 2017 中，下列程式碼在編譯時不會引發錯誤，但在 Visual Studio 2019 中會引發「C2440：無法從「多載函式」轉換為 'fp'」  ：

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

在 C++14 中，Lambda 終止類型不是常值。 此規則的主要的結果是 Lambda 可能不會指派給 `constexpr` 變數。 在 Visual Studio 2017 中，下列程式碼在編譯時不會引發錯誤，但在 Visual Studio 2019 中會引發「C2127：'l'：以非常數運算式不合法初始化 'constexpr' 實體」  ：

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

為避免此錯誤，請移除 `constexpr` 限定詞，或變更 `/std:c++17` 的一致性模式。

### <a name="stdcreatedirectory-failure-codes"></a>std::create_directory 失敗碼

已從 C++20 無條件實作 [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf)。 這會變更 `std::create_directory`，檢查目標在發生故障時是否即為目錄。 以前，所有 ERROR_ALREADY_EXISTS 類型錯誤都會轉換成成功但未建立目錄的程式碼。

### <a name="operatorstdostream-nullptrt"></a>operator<<(std::ostream, nullptr_t)

依 [LWG 2221](https://cplusplus.github.io/LWG/issue2221)，已新增 `operator<<(std::ostream, nullptr_t)` 將 nullptrs 寫入資料流。 

### <a name="additional-parallel-algorithms"></a>其他的平行演算法

新的平行版 `is_sorted`、`is_sorted_until`、`is_partitioned`、`set_difference`、`set_intersection`、`is_heap` 和 `is_heap_until`。

### <a name="atomic-initialization"></a>不可部分完成的初始化

[P0883 "Fixing atomic initialization"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) (P0883「修正不可部分完成的初始化」) 將 `std::atomic` 變更為初始化包含 T 的值，而不是將它初始化的預設值。 使用 Clang/LLVM 與 Microsoft 標準程式庫時即啟用此修正。 目前因使用 Microsoft C++ 編譯器作為 constexpr 處理的錯誤 (bug) 因應措施而停用。

### <a name="removecvref-and-removecvreft"></a>remove_cvref and remove_cvref_t

已從 [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) 實作 `remove_cvref` 和 `remove_cvref_t` 類型特性。 它們會移除類型中的參考性質和 CV 限定性，但不衰減指標的函式和陣列 (不同於 `std::decay` 和 `std::decay_t`)。

### <a name="feature-test-macros"></a>功能測試巨集

[P0941R2 - 功能測試巨集](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html)已完成，並支援 `__has_cpp_attribute`。 所有的標準模式都支援功能測試巨集。

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>禁止使用使用者宣告的建構函式彙總

[C++20 P1008R1 - 禁止使用使用者宣告的建構函式彙總](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf)已完成。

## <a name="improvements_161"></a> Visual Studio 2019 16.1 版的改善

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html)。 C++20 新增用來表示 UTF-8 字碼單位的新字元類型。 C++20 的 u8 字串常值具有類型 `const char8_t[N]` 而非 `const char[N]`，這是舊例。 [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm) 已針對 C 標準建議類似的變更。 [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html) 提供 Char8_t 回溯相容性的補救建議。 在 Visual Studio 2019 16.1 版中，當您指定 **/Zc:char8_t** 編譯器選項時，Microsoft C++ 編譯器會新增 char8_t 支援。 未來還會支援 [/std:c++latest](../../build/reference/std-specify-language-standard-version.md)，其可透過 **/Zc:char8_t-** 還原成 C++17 行為。 驅動 IntelliSense 的 EDG 編譯器尚不支援它，所以您會看到假性的僅限 IntelliSense 錯誤，不會影響實際的編譯。

#### <a name="example"></a>範例

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>std::type_identity metafunction 和 std::identity 函式物件

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). 已移除淘汰的 `std::identity` 類別範本副檔名，並已經以 C++20 `std::type_identity` metafunction 和 `std::identity` 函式物件取代。 兩者都僅能在 [/std:c++latest](../../build/reference/std-specify-language-standard-version.md) 下使用。 

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

新的 Lambda 處理器可在泛型 Lambda 中啟用一些一致性模式語法檢查，在 [/std:c++latest](../../build/reference/std-specify-language-standard-version.md) 下或使用 **/experimental:newLambdaProcessor** 的任何其他語言模式下。 

在 Visual Studio 2017 中，此程式碼在編譯時不會發出警告，但在 Visual Studio 2019 中會產生錯誤「C2760 語法錯誤：未預期的權杖 '\<id-expr>'，必須是 'id-expression'」  ：

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
- ` list` 和 `forward_list` 的 `remove()`、`remove_if()` 和 `unique()` 現在會傳回 `size_type`。
- `shift_left()` 和 `shift_right()` 已新增至 \<演算法>。

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-rtw"></a>Visual Studio 2019 RTW 中的 Bug 修正及行為變更

### <a name="correct-diagnostics-for-basicstring-range-constructor"></a>basic_string 範圍建構函式的正確診斷

在 Visual Studio 2019 中，`basic_string` 範圍建構函式不再使用 `static_cast` 隱藏編譯器診斷。 在 Visual Studio 2017 中，下列程式碼在編譯時不會發出警告，但在初始化 `out` 時，從 `wchar_t` 到 `char` 可能會遺失資料：

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 會正確引發「C4244：'argument'：從 'wchar_t' 轉換成 'const _Elem'，可能會遺失資料」  。 為避免此警告，您可以初始化 std::string，如此範例所示：

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>現可正確偵測 /clr 或 /ZW 下的不正確呼叫 += 和 -=

Visual Studio 2017 中引入的 Bug 導致編譯器以無訊息方式忽略錯誤，且不會為 `/clr` 或 `/ZW` 下的 += 和 -= 無效呼叫產生程式碼。 在 Visual Studio 2017 中，下列程式碼在編譯時不會引發錯誤，但在 Visual Studio 2019 中會正確引發「錯誤 C2845： *'System::String ^'：這種類型不允許指標算術*：

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

為避免此範例中的錯誤，請使用運算子搭配 ToString() 方法：`s += E::e.ToString();`。

### <a name="initializers-for-inline-static-data-members"></a>內嵌靜態資料成員的初始設定式

現可正確偵測到 `inline` 和 `static constexpr` 初始設定式內的無效成員存取。 在 Visual Studio 2017 中，下列範例在編譯時不會引發錯誤，但在 Visual Studio 2019 的 `/std:c++17` 模式下，會引發「錯誤 C2248：無法存取在類別 'X' 中宣告的私用成員」  。

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

MSVC 過去會提出隱含轉換為 bool 的效能警告 C4800，因為太吵雜又不可隱藏，所以 Visual Studio 2017 移除此警告。 不過，Visual Studio 2017 在生命週期中獲得許多有助於解決案例問題的意見反應。 我們在 Visual Studio 2019 重新引入仔細裁剪的 C4800 及相伴的 C4165，這兩者都可以使用明確轉型或設為 0 的適當類型比較來輕鬆隱藏。 C4800 為預設關閉的層級 4 警告，C4165 是預設關閉的層級 3 警告。 兩者都可使用 `/Wall` 編譯器選項探索。

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

在 Visual Studio 2017 中，「更新*C4822：* 區域類別成員函式沒有主體」只會在明確設定編譯器選項 `/w14822` 時引發，不會和 `/Wall` 一起出現。 在 Visual Studio 2019 中，C4822 為預設關閉的警告，因此不必明確設定 `/w14822`，即可在 `/Wall` 下探查到它。

```cpp
void foo()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>如果陳述式

範本函式主體包含的 `if constexpr` 陳述式已啟用一些 `/permissive-` 剖析相關檢查，則函式範本主體會包含 constexpr。 例如，在 Visual Studio 2017 中，下列程式碼會產生 C*7510：* 'Type'：只有未設定 `/permissive-` 選項時，使用相依類型名稱才必須加上 'typename' 前置詞。 在 Visual Studio 2019 中，無論是否設定 `/permissive-` 選項，相同的程式碼都會引發錯誤：

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

為避免此錯誤，請將 `typename` 關鍵字新增至 `a` 宣告：`typename T::Type a;`。

### <a name="inline-assembly-code-is-not-supported-in-a-lambda-expression"></a>Lambda 運算式不支援內嵌組譯碼

Visual C++ 小組最近發現一個安全性問題，即在 Lambda 內使用內嵌組譯碼可能會導致執行階段的 'ebp' (寄件地址註冊) 損毀。 惡意攻擊者有可能利用這種情況。 鑒於問題的本質，即只有 x86 支援內嵌組譯工具，且內嵌組譯工具與編譯器的其餘部分互動不佳的事實，這個問題的解決方法是 Lambda 運算式內不允許有內嵌組譯工具。

注意：唯一會在 Lambda 運算式內使用內嵌組譯工具的不尋常情況，是以擷取寄件位址為目的的用途。 在此案例中，您可以擷取所有平台的寄件地址，只要使用編譯器內建 `_ReturnAddress()` 即可。

下列程式碼會在 Visual Studio 2017 15.9 和 Visual Studio 2019 中產生「C7552：Lambda 中不支援內嵌組譯工具」  ：

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

### <a name="iterator-debugging-and-stdmoveiterator"></a>迭代器偵錯和 std::move_iterator

已教授迭代器偵錯功能正確解除包裝 `std::move_iterator`。 例如，`std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` 現可投入 `memcpy` 快速路徑。

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>修正 \<xkeycheck.h> 關鍵字強制執行

已修正標準程式庫的巨集化關鍵字強制執行 \<xkeycheck.h>，會發出偵測到的實際問題關鍵字，而不是一般訊息。 它也支援 C++20 的關鍵字，可避免誘騙 IntelliSense 說出隨機的巨集關鍵字。

### <a name="allocator-types-un-deprecated"></a>未淘汰的配置器類型

`std::allocator<void>`、`std::allocator::size_type` 和 `std::allocator::difference_type` 未被淘汰。

### <a name="correct-warning-for-narrowing-string-conversions"></a>更正縮小字串轉換的警告

已從 std::string 移除未經標準呼叫之假性 `static_cast` 意外隱藏的 C4244 縮小警告。 嘗試呼叫 `std::string::string(const wchar_t*, const wchar_t*)` 現會正確發出「C4244：將 wchar_t 縮小為一個字元。」 

### <a name="various-filesystem-correctness-fixes"></a>各種 \<檔案系統> 正確性修正

- 嘗試變更目錄的上次寫入時間時，修正 `std::filesystem::last_write_time` 失敗。
- 提供不存在的目標路徑時，`std::filesystem::directory_entry` 建構函式現在會儲存失敗的結果，而不是擲回例外狀況。
- `std::filesystem::create_directory` 的 2 個參數版本已變更為呼叫 1 個參數版本，因為當 existing_p 為符號連結時，基礎 `CreateDirectoryExW` 函式會執行 `copy_symlink`。
- 當發生符號連結中斷時，`std::filesystem::directory_iterator` 不會再失敗。
- `std::filesystem::space` 現在接受相對路徑。
- `std::filesystem::path::lexically_relative` 不再為句尾斜線困惑，回報為 [LWG 3096](https://cplusplus.github.io/LWG/issue3096)。
- 因應措施為 `CreateSymbolicLinkW` 拒絕在 `std::filesystem::create_symlink` 中有正斜線的路徑。
- 因應措施為 Windows 10 LTSB 1609 有 POSIX 刪除模式 `delete` 函式，實際上並不能刪除檔案。
- `std::boyer_moore_searcher` 和 `std::boyer_moore_horspool_searcher` 的複製建構函式和複製指派運算子現都可實際複製項目。

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Windows 8 和更新版本中的平行演算法

平行演算法程式庫現可正確使用 Windows 8 和更新版本的真實 `WaitOnAddress` 系列，而不是一律使用 Windows 7 和舊版的假版本。

### <a name="stdsystemcategorymessage-whitespace"></a>std::system_category::message() 空格

`std::system_category::message()` 現在會修剪傳回訊息的尾端空格。

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>std::linear_congruential_engine 除以零

已修正會導致 `std::linear_congruential_engine` 觸發除以 0 的一些情況。

### <a name="fixes-for-iterator-unwrapping"></a>修正迭代器解除包裝

在 Visual Studio 2017 15.8 中，針對程式設計師和使用者整合初次公開的迭代器解除包裝機制 (如 https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/ 中所述)，不會再解除包裝衍生自標準程式庫迭代器的迭代器。 例如，衍生自 `std::vector<int>::iterator` 的使用者和嘗試自訂行為的使用者，現在都可在呼叫標準程式庫演算法時試取得其自訂的行為，而不是指標的行為。
未排序的容器保留函式現在實際上都會保留以供 N 個項目使用，如 [LWG 2156](https://cplusplus.github.io/LWG/issue2156) 中所述。

### <a name="time-handling"></a>時間處理

- 過去，某些已傳遞給並行程式庫的時間值會溢位，例如 `condition_variable::wait_for(seconds::max())`。 現已修正的這些溢位，過去似乎會以隨機的 29 日循環變更行為 (當基礎 Win32 API 接受的 uint32_t 毫秒溢位時)。

- <ctime> 標頭現在除了全域命名空間外，還可使用命名空間標準正確宣告 timespec 與 timespec_get。

### <a name="various-fixes-for-containers"></a>容器的各種修正

- 許多標準程式庫的內部容器函式都已成為私用，以改善 IntelliSense 體驗。 MSVC 後續版本預計會提供可將成員標記為私用的其他修正。

- 已修正 `list`、`map` 和 `unordered_map` 等節點型容器可能損毀的例外狀況安全正確性問題。 在 `propagate_on_container_copy_assignment` 或 `propagate_on_container_move_assignment` 重新指派作業期間，我們會利用舊配置器來釋放容器的 sentinel 節點、對舊的配置器執行 POCCA/POCMA 指派，然後重試取得新配置器的 sentinel 節點。 如果這項配置失敗，則容器會損毀且甚至無法終結，因為擁有 sentinel 節點是不可變的永久性資料結構。 已藉由從來源容器的配置器配置新 sentinel 節點，再終結現有的 sentinel 節點來修正此問題。

- 容器已修正為根據 `propagate_on_container_copy_assignment`、`propagate_on_container_move_assignment` 和 `propagate_on_container_swap`，甚至針對配置器宣告的 `is_always_equal` 來一律複製/移動/分頁配置器。

- 已新增容器合併的多載，並依 [P0083 "Splicing Maps And Sets"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) (P0083：接合對應和集合) 擷取接受右值容器的成員函式

### <a name="stdbasicistreamread-processing-of-rn--n"></a>\r\n => \n 的 std::basic_istream::read 處理

`std::basic_istream::read` 已修正為不寫入部分所提供緩衝區轉存作為 \r\n => \n 處理的一部分。 這會放棄 Visual Studio 2017 15.8 在讀取大於 4K 大小的某些效能優勢，但仍保留避免每字元 3 次虛擬呼叫的效率改善。

### <a name="stdbitset-constructor"></a>std::bitset 建構函式

`std::bitset` 的建構函式不會再反向讀取大型位元集的一和零。

### <a name="stdpairoperator-regression"></a>std::pair::operator= 迴歸

已修正實作 [LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729) 時，`std::pair` 指派運算子導入的迴歸。 它現在可以再次正確接受可轉換為 `std::pair` 的類型。

### <a name="non-deduced-contexts-for-addconstt"></a>add_const_t 的非推算內容

已修正 `add_const_t` 和相關函式本該是非推算內容的次要類型特性 Bug。 換言之，`add_const_t` 應該是 `typename add_const<T>::type` 的別名，而非 `const T` 的別名。

## <a name="see-also"></a>另請參閱

[Visual Studio 2019 的新功能](../what-s-new-for-visual-cpp-in-visual-studio.md)