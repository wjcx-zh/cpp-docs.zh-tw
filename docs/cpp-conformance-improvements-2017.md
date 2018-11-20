---
title: C++ 一致性改善
ms.date: 10/31/2018
ms.technology:
- cpp-language
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: ad34e2721723e113417b45cf7c1da0da4575837f
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694396"
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-155improvements155-156improvements156-157improvements157-158update158-159update159"></a>Visual Studio 2017 15.0、[15.3](#improvements_153)、[15.5](#improvements_155)、[15.6](#improvements_156)、[15.7](#improvements_157)、[15.8](#update_158)、[15.9](#update_159) 版中的 C++ 一致性改善

Microsoft Visual C++ 編譯器支援一般化的 constexpr 和 NSDMI 彙總，現在完整呈現 C++14 標準中新增的功能。 請注意，編譯器仍缺乏一些來自 C++11 和 C++98 標準的功能。 請參閱 [Visual C++ 語言一致性](visual-cpp-language-conformance.md)，以取得顯示編譯器目前狀態的表格。

## <a name="c11"></a>C++11

### <a name="expression-sfinae-support-in-more-libraries"></a>更多程式庫支援運算式 SFINAE

編譯器會持續改善其對運算式 SFINAE 的支援，這是進行範本引數推算和替代的必要項目，而 decltype 和 constexpr 運算式可能會用作範本參數。 如需詳細資訊，請參閱 [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3) (Visual Studio 2017 RC 中的運算式 SFINAE 增強功能)。

## <a name="c-14"></a>C++ 14

### <a name="nsdmi-for-aggregates"></a>彙總的 NSDMI

彙總是陣列或類別，但沒有使用者提供的建構函式、私人或受保護的非靜態資料成員、基底類別和虛擬函式。 從 C++14 開始，彙總可能會包含成員初始設定式。 如需詳細資訊，請參閱 [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html) (成員初始設定式和彙總)。

### <a name="extended-constexpr"></a>擴充的 constexpr

宣告為 constexpr 的運算式現在允許包含特定種類的宣告、if 和 switch 陳述式、loop 陳述式，以及存留期開始於 constexpr 運算式評估以內的物件變動。 此外，constexpr 非靜態成員函式不再需要是隱含 const。 如需詳細資訊，請參閱 [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html) (放寬 constexpr 函式的條件約束)。

## <a name="c17"></a>C++17

### <a name="terse-staticassert"></a>Terse static_assert

static_assert 的訊息參數是選擇性的。 如需詳細資訊，請參閱 [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf) (擴充 static_assert v2)。

### <a name="fallthrough-attribute"></a>[[fallthrough]] 屬性

在 **/std:c++17** 模式中，[[fallthrough]] 屬性可以用於 switch 陳述式的內容，作為對意圖發生失敗行為之編譯器的提示。 在這類情況下，如此可避免編譯器發出警告。 如需詳細資訊，請參閱 [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf) ([[fallthrough]] 屬性的用語)。

### <a name="generalized-range-based-for-loops"></a>通用的範圍架構 for 迴圈

範圍式 for 迴圈不再需要 begin() 和 end() 傳回相同類型的物件。 這可讓 end() 傳回 [range-v3](https://github.com/ericniebler/range-v3) 中範圍所使用的 sentinel，以及已完成但尚未發行的「範圍技術規格」。 如需詳細資訊，請參閱 [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) (一般化範圍架構的 For 迴圈)。

## <a name="improvements_153"></a> Visual Studio 2017 15.3 版中的改善

### <a name="constexpr-lambdas"></a>constexpr lambdas

Lambda 運算式現在可用於常數運算式。 如需詳細資訊，請參閱 [C++ 中的 constexpr Lambda 運算式](cpp/lambda-expressions-constexpr.md)。

### <a name="if-constexpr-in-function-templates"></a>if constexpr 函式範本

函式範本可包含 `if constexpr` 陳述式，以進行編譯時間分支。 如需詳細資訊，請參閱 [if constexpr 陳述式](cpp/if-else-statement-cpp.md#if_constexpr)。

### <a name="selection-statements-with-initializers"></a>使用初始設定式的選取範圍陳述式

`if` 陳述式可包含會在陳述式之內於區塊範圍導入變數的初始設定式。 如需詳細資訊，請參閱[搭配初始設定式的 if 陳述式](cpp/if-else-statement-cpp.md#if_with_init)。

### <a name="maybeunused-and-nodiscard-attributes"></a>[[maybe_unused]] 與 [[nodiscard]] 屬性

這兩種新屬性可分別用來在實體未使用時，將警告設為無聲，以及在函式呼叫的傳回值遭捨棄時建立警告。 如需詳細資訊，請參閱 [C++ 中的屬性](cpp/attributes.md)。

### <a name="using-attribute-namespaces-without-repetition"></a>不重複使用屬性命名空間

新的語法讓您在屬性清單中可只用單一命名空間識別項。 如需詳細資訊，請參閱 [C++ 中的屬性](cpp/attributes.md)。

### <a name="structured-bindings"></a>結構化繫結

現在可以在單一宣告中以值元件的個別名稱儲存值，前提是該值必須為陣列、std::tuple 或 std::pair，或具有公用非靜態資料成員。 如需詳細資訊，請參閱[結構化繫結](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf)與[從函式傳回多重值](cpp/functions-cpp.md#multi_val)。

### <a name="construction-rules-for-enum-class-values"></a>enum class 值的建構規則

當列舉的定義未導入列舉程式，且來源使用 list-initialization 語法時，從範圍列舉的基礎類型到列舉本身之間現在已有隱含/非縮小的轉換。 如需詳細資訊，請參閱[列舉類別值的建構規則](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)與 [Enumerations](cpp/enumerations-cpp.md#no_enumerators)。

### <a name="capturing-this-by-value"></a>以值擷取 \*this

Lambda 運算式中的 `*this` 物件現已可以值擷取。 這可用在平行及非同步作業中叫用 Lambda 的案例，特別是在較新的電腦架構上。 如需詳細資訊，請參閱[Lambda 透過值將 \*this 擷取為 [=,\*this]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html) \(英文\)。

### <a name="removing-operator-for-bool"></a>移除 bool 的 operator++

`bool` 類型已不再支援 `operator++`。 如需詳細資訊，請參閱[移除已取代的 operator++ (bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html) \(英文\)。

### <a name="removing-deprecated-register-keyword"></a>移除已淘汰的 "register" 關鍵字

`register` 關鍵字先前已淘汰 (且編譯器已略過)，且現已從語言移除。 如需詳細資訊，請參閱[移除 register 關鍵字的已取代用途](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html) \(英文\)。

如需到 Visual Studio 2015 Update 3 為止的所有完整一致性改善清單，請參閱 [Visual C++ 2003 至 2015 的新功能](https://msdn.microsoft.com/library/mt723604.aspx)。

## <a name="improvements_155"></a>  Visual Studio 2017 15.5 版中的改善

以 [14] 標記的功能可無條件地使用，即使在 **/std:c++14** 模式中也一樣。

### <a name="new-compiler-switch-for-extern-constexpr"></a>extern constexpr 的新編譯器參數

在舊版的 Visual Studio 中，編譯器一律會為 `constexpr` 變數提供內部連結，即使變數以 `extern` 標記也一樣。 在 Visual Studio 2017 15.5 版中，新編譯器參數 [/Zc:externConstexpr](build/reference/zc-externconstexpr.md) 啟用正確且符合標準的行為。 如需詳細資訊，請參閱 [extern constexpr 連結](#extern_linkage)。

### <a name="removing-dynamic-exception-specifications"></a>移除動態例外狀況規格

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) 動態例外狀況規格在 C++11 中已淘汰。 此功能已從 C++17 中移除，但已被取代的 `throw()` 規格仍會嚴格保留作為 `noexcept(true)` 的別名。 如需詳細資訊，請參閱[動態例外狀況規格移除和 noexcept](#noexcept_removal)。

### <a name="notfn"></a>not_fn()

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` 已取代 `not1` 和 `not2`。

### <a name="rewording-enablesharedfromthis"></a>改寫 enable_shared_from_this

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` 已新增於 C++11。 此 C++17 標準會更新規格，以更妥善處理某些極端的案例。 [14]

### <a name="splicing-maps-and-sets"></a>接合 Map 與 Set

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) 此功能讓您可從關聯容器 (例如 map、set、unordered\_map、unordered\_set) 擷取節點，然後進行修改，再插回相同容器或使用相同節點類型的不同容器中。 (常見的使用案例是從 `std::map` 擷取節點，再變更金鑰，然後重新插入。)

### <a name="deprecating-vestigial-library-parts"></a>取代不必要的程式庫組件

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) C++ 標準程式庫有幾項功能多年來逐漸被較新的功能所取代，或是發現不實用或有問題。 這些功能在 C++17 中已正式被取代。

### <a name="removing-allocator-support-in-stdfunction"></a>移除 std::function 中的配置器支援

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) 在 C++17 之前，類別範本 `std::function` 具有數個使用配置器引數的建構函式。 不過，在此內容中使用配置器會有問題，而且語意不清。 因此已移除這些建構函式。

### <a name="fixes-for-notfn"></a>not_fn() 的修正

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) `std::not_fn` 的新寫法支援在包裝函式引動過程中傳播值類別。

### <a name="sharedptrt-sharedptrtn"></a>shared_ptr\<T[]>，shared_ptr\<T[N]>

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) 將程式庫基本概念中的 `shared_ptr` 變更合併到 C++17。 [14]

### <a name="fixing-sharedptr-for-arrays"></a>修正陣列的 shared_ptr

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) 修正陣列的 shared_ptr 支援。 [14]

### <a name="clarifying-insertreturntype"></a>讓 insert_return_type 更清楚

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) 具有唯一金鑰的關聯容器和具有唯一金鑰的未排序容器包含傳回巢狀型別 `insert_return_type` 的成員函式 `insert`。 該傳回型別現在已定義為在容器的 Iterator 和 NodeType 上參數化的類型特製化。

### <a name="inline-variables-for-the-stl"></a>STL 的 Inline 變數

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>附錄 D 已淘汰的功能

C++ 標準的附錄 D 包含已淘汰的所有功能，包括 `shared_ptr::unique()`、`<codecvt>` 和 `namespace std::tr1`。 當 **/std:c++17** 編譯器參數已設定時，附錄 D 中幾乎所有標準程式庫功能都會標記為已淘汰。 如需詳細資訊，請參閱[附錄 D 中的標準程式庫功能標記為已被取代](#annex_d)。

`<experimental/filesystem>` 中的 `std::tr2::sys` 命名空間現在於 **/std:c++14** 下預設會發出取代警告，且在 **/std:c++17** 下預設已移除。

藉由避免使用非標準的延伸模組 (類別內明確特製化) 來改善 iostreams 中的一致性。

標準程式庫現在會於內部使用變數樣板。

為了回應 C++17 編譯器變更，標準程式庫已經過更新，包括在型別系統中新增 noexcept 及移除動態例外狀況規格。

## <a name="improvements_156"></a>  Visual Studio 2017 15.6 版中的改善

### <a name="c17-library-fundamentals-v1"></a>C++17 程式庫基本概念 V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) 將 C++17 的程式庫基本技術規格合併至標準。 涵蓋對 \<experimental/tuple>、\<experimental/optional>、\<experimental/functional>、\<experimental/any>, \<experimental/string_view> 、\<experimental/memory>、\<experimental/memory_resource> 及 \<experimental/algorithm> 的更新。

### <a name="c17-improving-class-template-argument-deduction-for-the-stl"></a>適用於 STL 的 C++17 改善型類別範本引數推斷

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) 將 `adopt_lock_t` 移至參數清單前，使 `scoped_lock` 能夠一致使用 `scoped_lock`。 允許 `std::variant` 建構函式在更多案例中參與多載解析，以啟用 copy assignment。

## <a name="improvements_157"></a> Visual Studio 2017 15.7 版中的改善

### <a name="c17-rewording-inheriting-constructors"></a>C++17 改寫繼承建構函式

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) 指定了為建構函式命名的 **using** 宣告，現在會對衍生的類別顯示相應的基底類別建構函式，而不宣告額外的衍生類別建構函式。 這是從 C++14 開始的變更。 在 Visual Studio 2017 15.7 版及更新版本中，於 **/std:c++17** 模式中，在 C++14 有效以及使用繼承建構函式的程式碼，可能會失效或有不同的語意。

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

如需詳細資訊，請參閱[建構函式](cpp/constructors-cpp.md#inheriting_constructors)。

### <a name="c17-extended-aggregate-initialization"></a>C++17 擴充的彙總初始化

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

若基底類別的建構函式為非公開，但可由衍生類別存取，則在 Visual Studio 15.7 版的 **/std:c++17** 模式下，您將不必使用空括號就能將衍生類型的物件初始化。

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

在 C++17 中，`Derived` 已視作彙總類型；因此，透過私用預設建構函式將 `Base` 初始化會直接包含在擴充彙總初始化規則的過程。 `Base` 私用建構函式在先前會透過 `Derived` 建構函式呼叫，而成功的因素是 friend 宣告所致。

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17 使用 auto 宣告非類型範本參數

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

在 **/std:c + + 17** 模式中，編譯器現在可以推斷以 **auto** 宣告之非類型樣本引數的類型：

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

這項新功能的影響之一，包括有效的 C++14 程式碼可能失效或有不同的語意。 例如，部分先前無效的多載現在會變得有效。 下列範例顯示因為對 `foo(p)` 的呼叫已繫結至 `foo(void*);`，而編譯的 C++14 程式碼。 在 Visual Studio 2017 15.7 版中，在 **/std:c++17** 模式內的 `foo` 函式範本是最佳符合項。

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*) = delete;

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // OK in C++14
}
```

下列範例顯示 **/std:c++17** 模式中的 Visual Studio 15.7 C++17 程式碼：

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*);

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // C2280: 'int foo<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17 基礎字串轉換 (部分)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) 介於整數與字串之間，以及浮點數與字串之間的低階、無關地區設定的函式轉換。 (若為 Visual Studio 15.7 Preview 2，則僅支援整數。)

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20 避免不必要的 decay (部分)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) 為 "decay'' 的概念與單純移除常式或參考限定詞之間的差異新增區別。  新增類型特徵 `remove_reference_t` 來取代部分內容中的 `decay_t`。 Visual Studio 2017 version 15.7 Preview 2 尚未實作 `remove_cvref_t` 的支援。

### <a name="c17-parallel-algorithms"></a>C++17 平行演算法

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) 平行處理原則 TS 已併入標準，但有些微修改。

### <a name="c17-hypotx-y-z"></a>C++17 hypot(x、y、z)

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) 新增三個新多載到 `std::hypot`，針對 **float**、**double** 及 **long double** 類型，每個都有三種輸入參數。

### <a name="c17-filesystem"></a>C++17 \<filesystem>

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) 為標準採用檔案系統 TS，其中包括些許用詞修改。

### <a name="c17-mathematical-special-functions"></a>C++17 數學特殊函式

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) 為 \<cmath> 標頭將先前技術規格的數學特殊函式納入標準。

### <a name="c17-deduction-guides-for-the-stl"></a>C++17 STL 推斷指引

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) 更新 STL 以利用 C++17 對 [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) 的採用，這為類別範本引數推斷新增了支援。

### <a name="c17-repairing-elementary-string-conversions"></a>C++17 修復基礎字串轉換

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) 將新的基礎字串轉換函式從 P0067R5 移至新標頭 \<charconv>，並進行了其他改善，包括將錯誤處理函式改為使用 `std::errc` 而非 `std::error_code`。

### <a name="c17-constexpr-for-chartraits-partial"></a>C++17 char_traits 的 constexpr (部分)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) 對 `std::traits_type` 成員函式 `length`、`compare` 及 `find` 進行變更，讓常數運算式中可使用 `std::string_view`。 (在 Visual Studio 2017 15.6 版中，僅支援 Clang/LLVM。 在 15.7 版 Preview 2 中，也幾乎完全支援 CIXX。)

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-155update155-157update157-158update158-and-159update159"></a>Visual Studio 15.0、[15.3](#update_153)、[15.5](#update_155)、[15.7](#update_157)、[15.8](#update_158) 及 [15.9](#update_159) 版中的 Bug 修正

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 使用 Visual Studio 2015 中攔截不到且可能導致當機或未定義執行階段行為的初始設定式清單，正確地引發與建立物件相關的編譯器錯誤。 根據 N4594 13.3.1.7p1，在 copy-list-initialization 中，編譯器需要考慮使用明確建構函式來進行多載解析，但必須在實際選擇該多載時引發錯誤。

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

### <a name="constexpr"></a>constexpr

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

若要更正錯誤，請將 `array::size()` 函式宣告為 `constexpr`，或從 `f` 中移除 `constexpr` 限定詞。

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

或者先執行靜態轉型來轉換物件，再傳遞它︰

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

### <a name="cv-qualifiers-in-class-construction"></a>類別建構中的 cv 限定詞

在 Visual Studio 2015 中，透過建構函式呼叫來產生類別物件時，編譯器有時會錯誤地忽略 cv 限定詞。 這可能會導致當機或意外執行階段行為。 下列範例是在 Visual Studio 2015 中編譯，但在 Visual Studio 2017 中引發編譯器錯誤：

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

若要更正錯誤，請將 `operator int()` 宣告為 `const`。

### <a name="access-checking-on-qualified-names-in-templates"></a>範本中限定名稱的存取檢查

舊版編譯器未對部分範本內容中限定名稱執行存取檢查。 這可能會干擾預期 SFINAE 行為，其中，替代預期會因無法存取名稱而失敗。 這可能會在執行階段因編譯器錯誤地呼叫運算子的錯誤多載而導致當機或意外行為。 在 Visual Studio 2017 中，會引發編譯器錯誤。 特定錯誤可能會不同，但通常為「C2672 找不到相符的多載函式」。 下列程式碼是在 Visual Studio 2015 中編譯，但在 Visual Studio 2017 中引發錯誤：

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

在 Visual Studio 2015 和以前版本中，範本出現在範本參數清單時 (例如，作為預設範本引數或非類型範本參數的一部分)，編譯器無法診斷出遺漏範本引數清單。 這可能會導致無法預期的行為，包括編譯器當機或意外執行階段行為。 下列程式碼是在 Visual Studio 2015 中編譯，但在 Visual Studio 2017 中產生錯誤。

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Expression-SFINAE

為了支援 expression-SFINAE，編譯器現在會在宣告範本而非具現化範本時剖析 decltype 引數。 因此，如果在 decltype 引數中發現非相依特製化，不會延遲到具現化期間，並會立即處理，而且會在當下診斷出任何產生的錯誤。

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

根據 C++ 標準，宣告於匿名命名空間中的類別具有內部連結，因此無法匯出。 在 Visual Studio 2015 和更早的版本中，並未強制執行此規則。 在 Visual Studio 2017 中，會部分強制執行此規則。 下列範例會在 Visual Studio 2017 中引發這個錯誤：「錯誤 C2201: const anonymous namespace::S1::vftable: 必須具有外部連結以便匯出/匯入。」

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>實值類別成員的預設初始設定式 (C++/CLI)

在 Visual Studio 2015 和以前版本中，編譯器允許 (但忽略) 實值類別成員的預設成員初始設定式。 實值類別的預設初始化一律會以零初始化成員；不允許預設建構函式。 在 Visual Studio 2017 中，預設成員初始設定式會引發編譯器錯誤，如這個範例中所示︰

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>預設索引子 (C++/CLI)

在 Visual Studio 2015 和以前版本中，在某些情況下，編譯器會將預設屬性錯誤地識別為預設索引子。 使用 `default` 識別項存取屬性，即可解決問題。 在 C++11 中將 `default` 用作 關鍵字後，該因應措施本身會成為問題。 因此，在 Visual Studio 2017 中，已修正需要該因應措施的 Bug，而且編譯器現在會在使用 `default` 存取類別的預設屬性時引發錯誤。

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

## <a name="update_153"></a> Visual Studio 2017 15.3 版中的錯誤修正

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

若要修正錯誤，請將 i 宣告為 `int`。

### <a name="pre-condition-checks-for-type-traits"></a>類型特性的先決條件檢查

Visual Studio 2017 15.3 版改進了類型特性的先決條件檢查，以更嚴格地遵守標準。 此類檢查是可供指派的。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生 C2139：

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>原生至 Managed 封送處理上的新編譯器警告和執行階段檢查

從 Managed 函式對原生函式的呼叫需要封送處理。 CLR 會執行封送處理，但它並不了解 C++ 語意。 如果您根據傳遞原生物件，CLR 會呼叫物件的 copy-constructor，或使用 BitBlt，這可能在執行階段導致未定義的行為。

編譯器如果可以在編譯時期時，知道含有已刪除 copy ctor 的原生物件會在原生和 Managed 界限之間以值傳遞，就會發出警告。 針對編譯器在編譯時期不知道的那些情況，其會插入執行階段檢查，以便程式會在發生語式錯誤的封送處理時，立即呼叫 `std::terminate`。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生警告 C4606「'A': 跨越原生與 Managed 界限以值傳遞引數必須使用有效的複製建構函式。 否則不會定義執行階段行為」。

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
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
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

Visual Studio 2017 15.3 版在遇到未在類別中宣告之樣板成員函式的程式碼外部定義時會產生錯誤。 下列程式碼現在會產生錯誤 C2039：'f': 不是 'S' 的成員：

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

### <a name="attempting-to-take-the-address-of-this-pointer"></a>嘗試取得 "this" 指標的位址

在 C++ 中，`this` 是 X 之類型指標的 prvalue。您無法取得 `this` 的位址，或將其繫結至 lvalue 參考。 在舊版的 Visual Studio 中，編譯器可讓您執行轉型以避開此限制。 在 Visual Studio 2017 15.3 版中，編譯器會產生錯誤 C2664。

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

### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>成員函式的程式碼外部定義不允許預設引數

在範本類別中成員函式的非正規定義上不可使用預設引數。編譯器會在 **/permissive** 下發出警告，並在 **/permissive-** 下發出硬碟錯誤。

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

### <a name="use-of-offsetof-with-compound-member-designator"></a>使用 offsetrof 搭配複合成員指示項

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

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>使用 offsetof 搭配靜態資料成員或成員函式

在 Visual Studio 2017 15.3 版中，使用 `offsetof(T, m)` (其中 *m* 代表靜態資料成員或成員函式) 會導致錯誤。 下列程式碼會產生「錯誤 C4597: 未定義的行為: offsetof 套用至成員函式 'foo'」和「錯誤 C4597: 未定義的行為: offsetof 套用至靜態資料成員 'bar'」：

```cpp
#include <cstddef>

struct A {
   int foo() { return 10; }
   static constexpr int bar = 0;
};

constexpr auto off = offsetof(A, foo);
constexpr auto off2 = offsetof(A, bar);
```

此程式碼的語式錯誤，且可能在執行階段造成當機。 若要修正錯誤，請變更程式碼以不再叫用未定義的行為。 這是不可移植且 C++ 標準不允許的程式碼。

### <a name="declspec"></a> 針對 declspec 屬性的新警告

在 Visual Studio 2017 15.3 版中，如果 `__declspec(...)` 套用於 `extern "C"` 連結規格前，編譯器就不再略過該屬性。 編輯器之前會忽略該屬性，這可能隱含執行階段。 當 **/Wall** 和 **/WX** 選項設定時，下列程式碼會產生「警告 C4768: 連結規格前的 __declspec 屬性已略過」：

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

若要修正此警告，請先加入 extern "C"：

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

此警告在 15.3 中預設為關閉 (但在 15.5 中預設為開啟)，且只影響以 **/Wall** **/WX** 編譯的程式碼。

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype 和對已刪除之解構函式的呼叫

在舊版的 Visual Studio 中，在與 'decltype' 相關聯的運算式內容中呼叫已刪除的解構函式時，編譯器並不會偵測到。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生「錯誤 C2280: 'A\<T>::~A(void)'：嘗試參考已刪除的函式」：

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

如果 'const' 變數未初始化，C++ 編譯器將不會發出診斷，而 Visual Studio 2017 RTW 版本會發生回歸。 Visual Studio 2017 15.3 版已修正此迴歸。 下列程式碼現在會產生「警告 C4132: 'Value': 應初始化常數物件」：

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

若要移除警告，只要將空白宣告註解化或移除即可。 在未命名物件可能具有副作用 (例如 RAII) 的情況下，應該提供名稱給它。

該警告在 **/Wv:18** 下會排除，且在警告層級 W2 下預設為開啟。

### <a name="stdisconvertible-for-array-types"></a>陣列類型的 std::is_convertible

舊版編譯器對陣列類型的 [std::is_convertible](standard-library/is-convertible-class.md) 會給出不正確的結果。 這要求程式庫作者在使用 `std::is_convertible<...>` 類型特性時，以特殊案例處理 Microsoft Visual C++ 編譯器。 下例中，靜態判斷提示能夠通過舊版 Visual Studio，但在 Visual Studio 2017 15.3 版中失敗：

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

### <a name="private-destructors-and-stdisconstructible"></a>私人解構函式和 std::is_constructible

舊版編譯器在決定 [std::is_constructible](standard-library/is-constructible-class.md) 的結果時，會忽略解構函式是否是私人的。 現在會考慮。 下例中，靜態判斷提示能夠通過舊版 Visual Studio，但在 Visual Studio 2017 15.3 版中失敗：

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

舊版編譯器在同時透過使用宣告和引數相依查閱找到多個候選項目時，有時偵測不到語意模糊。 這會導致選擇錯誤的多載和未預期的執行階段行為。 在下列範例中，Visual Studio 2017 15.3 版會正確引發「C2668 'f': 多載函式的語意模糊呼叫」：

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

區域函式宣告會將函式宣告隱藏在封閉範圍中，停用引數相依查閱。 不過，舊版編譯器在這種情況下會執行引數相依查閱，有可能導致選擇錯誤的多載和未預期的執行階段行為。 錯誤通常是因為區域函式宣告的簽章不正確而發生。 在下列範例中，Visual Studio 2017 15.3 版會正確引發「C2660 'f': 函式不接受 2 個引數」：

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

類別成員會依其宣告的順序初始化，而不是依它們在初始設定式清單中出現的順序。 當初始設定式清單的順序和宣告順序不一致時，舊版編譯器未發出警告。 如果某個成員的初始化依存於清單中另一個已初始化的成員，這可能導致未定義的執行階段行為。 在下列範例中，Visual Studio 2017 15.3 版 (使用 **/Wall**) 會引發「警告 C5038: 資料成員 'A::y' 會在資料成員 'A::x' 之後初始化」：

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

若要修正此問題，請將初始設定式清單排列成和宣告一樣的順序。 當一或兩個初始設定式參考基底類別成員時，就會引發類似的警告。

請注意，此警告預設為關閉，且只影響以 **/Wall** 編譯的程式碼。

## <a name="update_155"></a> Visual Studio 2017 15.5 版中的錯誤修正及其他行為變更

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

### <a name="tr1"></a>std::tr1 命名空間已被取代

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
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
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

### <a name="annex_d"></a>附錄 D 中的標準程式庫功能標記為已淘汰

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
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ Standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
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

### <a name="declspec-attributes-with-extern-c-linkage"></a>具有 extern "C" 連結的 __declspec 屬性

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

在舊版的 Visual Studio 中，編譯器一律會為 `constexpr` 變數提供內部連結，即使變數以 `extern` 標記也一樣。 在 Visual Studio 2017 15.5 版中，新的編譯器參數 (**/Zc:externConstexpr**) 讓行為可正確且符合標準。 這最後終究會成為預設值。

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

如果標頭檔包含宣告為 `extern constexpr` 的變數，就需要以 `__declspec(selectany)` 標記，才能正確地合併其重複宣告：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>typeid 不可用於不完整的類別類型

在舊版的 Visual Studio 中，編譯器不正確地允許下列程式碼，因此導致可能不正確的類型資訊。 在 Visual Studio 2017 15.5 版中，編譯器會正確地引發錯誤：

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>std::is_convertible 目標類型

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

### <a name="noexcept_removal"></a> 動態例外狀況規格移除和 noexcept

在 C++17 中，`throw()` 是 `noexcept` 的別名、`throw(<type list>)` 和 `throw(...)` 會遭到移除，而且某些類型可能包含 `noexcept`。 這會導致符合 C++14 或更早版本之程式碼的來源相容性。 在一般情況下使用 C++17 模式時，可使用 **/Zc:noexceptTypes-** 參數還原為 C++14 版的 `noexcept`。 這可讓您更新原始程式碼以符合 C++17，而不需要同時重寫所有 `throw()` 程式碼。

編譯器現在也會診斷 C++17 模式宣告中或使用 **/permissive-** 的更多不相符例外狀況規格，並發出新的警告 C5043。

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

若要移除錯誤但仍然使用 **/std:c++17**，請將 **/Zc:noexceptTypes-** 參數新增至命令列，或更新您的程式碼以使用 `noexcept`，如下列範例所示：

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

靜態 constexpr 資料成員現在隱含內嵌，這表示其在類別內的宣告現在會是其定義。 對靜態 constexpr 資料成員使用程式碼外部定義是多餘的，現在已被取代。 在 Visual Studio 2017 15.5 版中，當套用 **/std:c++17** 參數時，下列程式碼現在會產生警告 C5041 'size': 不需要 constexpr 靜態資料成員的非正規定義，且在 C++17 中已淘汰：

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>extern "C" __declspec(...) 警告 C4768 現在預設會開啟

在 Visual Studio 2017 15.3 版中已新增警告，但預設為關閉。 在 Visual Studio 2017 15.5 版中，預設為開啟。 如需詳細資訊，請參閱[針對 declspec 屬性的新警告](#declspec)。

### <a name="defaulted-functions-and-declspecnothrow"></a>預設函式和 __declspec(nothrow)

當對應的基底/成員函式允許例外狀況時，編譯器之前允許使用 `__declspec(nothrow)` 宣告預設函式。 此行為違反 C++ 標準，而且可能在執行階段導致未定義的行為。 如果不符合例外狀況規格，此標準會要求將這類函式定義為已刪除。  在 **/std:c++17** 下，下列程式碼會引發 C2280 嘗試參考已刪除的函式 *。* 已隱含刪除函式，因為明確例外狀況的規格與隱含宣告的規格不相容」：

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

### <a name="noexcept-and-partial-specializations"></a>noexcept 和部分特製化

當型別系統中有 noexcept 時，符合特定「可呼叫」類型的部分特製化可能會由於遺漏 noexcept 函式指標的部分特製化而無法編譯或選擇主要樣板。

在這種情況下，您可能需要新增額外的部分特製化，以處理 noexcept 函式指標及成員函式的 noexcept 指標。 這些多載只在 **/std:c++17** 模式中才合法。 如果必須維持與 C++14 舊版相容，而且您正撰寫的程式碼有其他人使用，則您應該使用 `#ifdef` 指示詞括住這些新的多載。 如果您想在獨立模組中工作，則可以直接使用 **/Zc:noexceptTypes-** 參數進行編譯，而不需要使用 `#ifdef` 成立條件。

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

## <a name="update_157"></a> Visual Studio 2017 15.7 版中的 Bug 修正及其他行為變更

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17 主要類別範本中的預設引數

此行為變更是[類別範本之範本引數推斷 - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) 的前置條件，計劃在之後的 Visual Studio 2017 15.7 預覽版中提供完整支援。

在此之前，編譯器會忽略主要類別範本中的預設引數。

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

此行為變更是[類別範本之範本引數推斷 - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) 的前置條件，計劃在之後的 Visual Studio 2017 15.7 預覽版中提供完整支援。

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

Visual Studio 2017 15.7 版在 **/std:c++17** 模式中，於 D 內的 `using` 陳述式需要 `typename` 索引鍵。若缺少 `typename`，則編譯器會引發警告 C4346: *'B<T>::type': 相依性名稱不是類型\**，以及錯誤 C2061: 語法錯誤: 識別碼 'type':

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17 [[nodiscard]] 屬性 - 警告等級增加

在 Visual Studio 2017 15.7 版的 **/std:c++17** 模式中，警告等級 C4834 (「捨棄屬性為 'nodiscard' 之函式的傳回值」) 已從 W3 增加至 W1。 您可對 `void` 進行轉換，或是傳遞 **/wd:4834** 給編譯器以停用警告

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

### <a name="constexpr-aggregate-initialization"></a>constexpr 彙總初始化

C++ 編譯器的先前版本未能正確地處理 constexpr 彙總初始化，它會接受無效的程式碼 (其中的彙總初始化清單包含了太多元素)，並產生不良的 Codegen。 以下程式碼為此類程式碼的範例：

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

## <a name="update_158"></a> Visual Studio 2017 15.8 版中的 Bug 修正及行為變更

Visual Studio 2017 版本 15.8 中的編譯器變更，全都落在修正 Bug 與行為變更的這一類別中，如下所示：

### <a name="typename-on-unqualified-identifiers"></a>非限定識別碼上的 typename

在 [/permissive-](build/reference/permissive-standards-conformance.md) 模式中，編譯器不再接受別名範本定義中非限定識別碼上的假性 `typename` 關鍵字。 下列程式碼現在會產生 C7511「T': 'typename' 關鍵字後面必須接著限定名稱」：

```cpp
template <typename T>
using  X = typename T;
```

若要修正此錯誤，只需要將第二行變更為 `using  X = T;` 即可。

### <a name="declspec-on-right-side-of-alias-template-definitions"></a>別名範本定義右側的 __declspec()

不再允許 [__declspec](cpp/declspec.md) 位於別名範本定義的右側。 編譯器先前接受此用法，但此用法完全被忽略，且永遠不會在使用別名時產生淘汰警告。

可以改為使用標準 C++ 屬性 [\[\[deprecated\]\]](cpp/attributes.md)，並將從 Visual Studio 2017 15.6 版開始採用此屬性。 下列程式碼現在會產生 C2760「語法錯誤：非預期的語彙基元 '__declspec'，必須是類型規範」：

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

表示這種情況的其中一個方法是使用相依基底類別的查詢。 之前，編譯器允許使用相依基底類別中定義的名稱，因為在解析所有類型時，會在具現化期間查閱這些名稱。 現在，該程式碼則會被視為錯誤。 在這些情況下，您可以強制在具現化時期查閱變數，方法是使用基底類別類型進行限定，或以其他方式使其相依，例如新增 `this->` 指標。

在 **/permissive-** 模式中，下列程式碼現在會引發 C3861：「'base_value': 找不到識別碼」：

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

**注意：** 在 Boost Python 程式庫中，長久以來 [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp) 中就有向前範本宣告的 MSVC 特定因應措施。 從 Visual Studio 2017 15.8 版 (_MSC_VER=1915) 開始，在 [/permissive-](build/reference/permissive-standards-conformance.md) 模式下，MSVC 編譯器就會正確地執行引數相依名稱查閱 (ADL) 且行為與其他編譯器一致，讓此因應措施逐漸變得沒必要。 若要避免此錯誤 *C3861: 'unwind_type': 找不到識別項*，請參閱 Boostorg 存放庫中的 [PR 229](https://github.com/boostorg/python/pull/229) 以更新標頭檔。 我們已修補 [vcpkg](vcpkg.md) Boost 套件，因此若您是從 vcpkg 取得或更新 Boost 來源，則不需要個別套用補充程式。

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>命名空間 std 中的向前宣告和定義

C++ 標準不允許使用者將向前宣告或定義新增到命名空間 `std` 中。 將宣告或定義新增至命名空間 `std` 或新增至命名空間 std 內的命名空間，現在會導致發生未定義的行為。

在未來的某個時間，Microsoft 將會移動一些 STL 類型定義所在的位置。 發生這種情況時，它會中斷將向前宣告新增至命名空間 `std` 的現有程式碼。 新警告 C4643 有助於識別這類來源問題。 警告在 **/default** 模式中已啟用且預設為關閉。 它會影響使用 **/Wall** 或 **/WX** 編譯的程式。

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

C++ 標準建議編譯器應該在建構函式委派給其本身時發出診斷。 Microsoft C++ 編譯器在 [/std:c++17](build/reference/std-specify-language-standard-version.md) 和 [/std:c++latest](build/reference/std-specify-language-standard-version.md) 模式中現在會引發 C7535：「'X::X': 委派建構函式呼叫其本身」。

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

### <a name="offsetof-with-constant-expressions"></a>使用常數運算式的 offsetof

[offsetof](c-runtime-library/reference/offsetof-macro.md) 傳統上使用需要 [reinterpret_cast](cpp/reinterpret-cast-operator.md) 的巨集來實作。 這在需要常數運算式的內容中並不合法，但 Microsoft C++ 編譯器傳統上會允許此做法。 隨附為 STL 一部分的 offsetof 巨集會正確使用編譯器內建函式 (**__builtin_offsetof**)，但有許多人已使用巨集技巧來定義自己的 **offsetof**。

在 Visual Studio 2017 15.8 版中，編譯器會限制預設模式中可以顯示這些 reinterpret_cast 的區域，以協助程式碼符合標準的 C++ 行為。 在 [/permissive-](build/reference/permissive-standards-conformance.md) 下，條件約束更為嚴格。 在需要常數運算式的地方使用 offsetof 的結果，可能會導致程式碼發出警告 C4644「在常數運算式中使用以巨集為基礎的 offsetof 模式是非標準用法；請改為使用 C++ 標準程式庫中定義的 offsetof」或 C2975「範本引數無效，必須是編譯時期常數運算式」。

下列程式碼會在 **/default** 和 **/std:c++17** 模式中引發 C4644，並在 **/permissive-** 模式中引發 C2975：

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

若要修正此錯誤，請使用透過 \<cstddef> 定義的 **offsetof**：

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

在 Visual Studio 2017 15.8 版的 **/permissive-** 模式中，下列程式碼會引發 C3770「'const S': 不是有效的基底類別」：

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>template 關鍵字和巢狀名稱規範

在 **/permissive-** 模式中，編譯器現在需要 `template` 關鍵字位於範本名稱之前，並接在相依的巢狀名稱規範之後。

下列程式碼在 **/permissive-** 模式中現在會引發 C7510：「'foo': 使用相依範本名稱時，前面必須加上 'template'。注意：請查看所編譯之類別範本具現化 'X<T>' 的參考」：

```cpp
template<typename T> struct Base
{
    template<class U> void foo() {}
};

template<typename T>
struct X : Base<T>
{
    void foo()
    {
        Base<T>::foo<int>();
    }
};
```

若要修正此錯誤，請將 `template` 關鍵字新增至 `Base<T>::foo<int>();` 陳述式，如下列範例所示：

```cpp
template<typename T> struct Base
{
    template<class U> void foo() {}
};

template<typename T>
struct X : Base<T>
{
    void foo()
    {
        // Add template keyword here:
        Base<T>::template foo<int>();
    }
};
```
## <a name="update_159"></a> Visual Studio 2017 15.9 版中的 Bug 修正及行為變更

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

在 Visual Studio 2017 15.9 版的 **/permissive-** 模式中，編譯器會引發 C3861：「'from_template': 找不到識別碼」.

若要修正此錯誤，請在 `from_template_t` 之前宣告 `from_template`。

### <a name="modules-changes"></a>模組變更

在 Visual Studio 2017 15.9 版中，每當模組的命令列選項在模組建立端與模組使用端之間不一致時，編譯器都會引發 C5050。 下列範例中有兩個問題：

- 使用端 (main.cpp) 上未指定 **/EHsc** 選項。
- 建立端上的 C++ 版本是 **/std:c++17**，而在使用端上則是 **/std:c++14**。 

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

編譯器對兩者都引發了 C5050：「警告 C5050: 匯入模組 'm' 時環境可能不相容: 不相符的 C++ 版本。目前的 "201402" 模組版本 "201703"」*。

此外，每當 .ifc 檔案遭竄改時，編譯器都會引發 C7536。 模組介面的標頭下方會包含內容的 SHA2 雜湊。 匯入時，.ifc 檔案會以相同方式雜湊，然後與標頭中提供的雜湊對照，如果兩者不相符，則會引發 C7536：「ifc 完整性檢查失敗。應為 SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'」*。

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>涉及別名及非推算內容的部分排序

涉及非推算內容中別名的部分排序規則裡發生實作發散。 在下列範例中，GCC 及 Microsoft C++ 編譯器 (在 **/permissive-** 模式中) 於 Clang 接受程式碼時會引發錯誤。 

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

實作發散的原因是標準字眼中的迴歸，其中核心問題 2235 的解決辦法移除了某些會允許排序這些多載的文字。 目前的 C++ 標準並不提供將這些函式部分排序的機制，因此會將他們視為不明確。

建議的因應措施是使用 SFINAE 來移除特定多載，而非仰賴部分排序來解決此問題。 在下列範例中，我們使用協助程式類別 `IsA`，在 `Alloc` 為 `A` 的專屬表示時移除第一個多載：

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

## <a name="see-also"></a>另請參閱

[Visual C++ 語言一致性](visual-cpp-language-conformance.md)
