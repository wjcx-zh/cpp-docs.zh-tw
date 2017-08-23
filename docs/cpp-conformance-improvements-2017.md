---
title: "C++ 編譯器一致性改善 | Microsoft Docs"
ms.custom: 
ms.date: 06/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 467fc9fdbdf1df73590e5ca498067eb2a5b5c900
ms.openlocfilehash: 42b93960a6e0b829f3501c92a081953cf1051be4
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
   
# <a name="c-conformance-improvements-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 中的 C++ 編譯器一致性改善

## <a name="new-language-features"></a>新的語言功能  
編譯器支援一般化 constexpr 和 NSDMI 彙總，現在完整呈現 C++14 標準中新增的功能。 請注意，編譯器仍缺乏一些來自 C++11 和 C++98 標準的功能。 請參閱 [Visual C++ 語言一致性](visual-cpp-language-conformance.md)，以取得顯示編譯器目前狀態的表格。

### <a name="c11"></a>C++11：
**多個程式庫中的運算式 SFINAE 支援**：Visual C++ 編譯器會持續改善其運算式 SFINAE 支援，這是進行範本引數推算和替換的必要項目，而 decltype 和 constexpr 運算式可能會顯示為範本參數。 如需詳細資訊，請參閱 [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3) (Visual Studio 2017 RC 中的運算式 SFINAE 增強功能)。 


### <a name="c-14"></a>C++ 14：
**NSDMI for Aggregates**：彙總是陣列或類別，但沒有使用者提供的建構函式、私人或受保護的非靜態資料成員、基底類別和虛擬函式。 從 C++14 開始，彙總可能會包含成員初始設定式。 如需詳細資訊，請參閱 [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html) (成員初始設定式和彙總)。

**擴充 constexpr**：宣告為 constexpr 的運算式現在允許包含特定類型的宣告、if 和 switch 陳述式、loop 陳述式，以及存留期開始於 constexpr 運算式評估內的物件變動。 此外，constexpr 非靜態成員函式不再需要是隱含 const。 如需詳細資訊，請參閱 [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html) (放寬 constexpr 函式的條件約束)。 

### <a name="c17"></a>C++17：
**Terse static_assert** (可與 /std:c++latest 搭配使用)：在 C++17 中，static_assert 的訊息參數為選擇性。 如需詳細資訊，請參閱 [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf) (擴充 static_assert v2)。 

**[[fallthrough]] 屬性** (可與 /std:c++latest 搭配使用)：[[fallthrough]] 屬性可以用於 switch 陳述式的內容，作為故意要有失敗行為之編譯器的提示。 在這類情況下，如此可避免編譯器發出警告。 如需詳細資訊，請參閱 [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf) ([[fallthrough]] 屬性的用語)。 

**一般化範圍架構的 for 迴圈** (不需要編譯器參數)：範圍架構的 for 迴圈不再需要 begin() 和 end() 傳回相同類型的物件。 這可讓 end() 傳回 sentinel 物件，例如 Ranges-V3 提案中所定義範圍使用的物件。 如需詳細資訊，請參閱 [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) (一般化範圍架構的 For 迴圈) 和 [range-v3 library on GitHub](https://github.com/ericniebler/range-v3) (GitHub 上的 range-v3 程式庫)。 

**Visual Studio 2017 15.3 版**：

**constexpr lambda**：Lambda 運算式現在可用於常數運算式。 如需詳細資訊，請參閱 [Constexpr Lambda](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf) \(英文\)。

**函式樣板中的 if constexpr**：函式樣板可以包含 `if constexpr` 陳述式，以啟用編譯時間分支。 如需詳細資訊，請參閱 [if constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html) \(英文\)。

**搭配初始設定式的選取範圍陳述式**：`if` 陳述式可以包含會在陳述式之內於區塊範圍導入變數的初始設定式。 如需詳細資訊，請參閱[搭配初始設定式的選取範圍陳述式](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html) \(英文\)。

**[[maybe_unused]] 和 [[nodiscard]] 屬性**：這兩個新屬性可以個別用來將實體未使用時的警告設為無聲，以及在函式呼叫的傳回值被捨棄時建立警告。 如需詳細資訊，請參閱 [maybe_unused 屬性的用字方式](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf) \(英文\) 及[unused、nodiscard 及 fallthrough 屬性的提案](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf) \(英文\)。

**使用不重複的屬性命名空間**：新的語法可以在屬性清單中僅啟用單一命名空間識別項。 如需詳細資訊，請參閱 [C++ 中的屬性](cpp/attributes2.md)。

**結構化繫結**：現在可以在單一宣告中儲存針對其元件具有個別名稱的值，前提是該值必須為陣列、std::tuple 或 std::pair，或是僅具公用非靜態資料成員。 如需詳細資訊，請參閱[結構化繫結](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf) \(英文\)。

**列舉類別值的建構規則**：當列舉的定義未導入列舉程式，且來源使用 list-initialization 語法時，從範圍列舉的基礎類型到列舉本身之間現在已有隱含/非縮小的轉換。 如需詳細資訊，請參閱[列舉類別值的建構規則](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf) \(英文\)。

**透過值擷取 *this**：Lambda 運算式中的 "\*this" 物件現已可以透過值進行擷取。 這可促成在平行及非同步作業中叫用 Lambda 的案例，特別是在較新的電腦架構上。 如需詳細資訊，請參閱[Lambda 透過值將 \*this 擷取為 [=,\*this]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html) \(英文\)。

**針對 bool 移除 operator++**：`bool` 類型已不再支援 operator++。 如需詳細資訊，請參閱[移除已取代的 operator++ (bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html) \(英文\)。

**移除已取代的 "register" 關鍵字**：先前已取代 (且被 Visual C++ 編譯器忽略) 的 `register` 關鍵字，現在已從語言中移除。 如需詳細資訊，請參閱[移除 register 關鍵字的已取代用途](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html) \(英文\)。

如需到 Visual Studio 2015 Update 3 為止的完整一致性改善清單，請參閱 [Visual C++ What's New 2003 through 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx)(從 2003 到 2015 的 Visual C++ 新功能)。

## <a name="bug-fixes"></a>Bug 修正
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
若要更正錯誤，請將 array::size() 函式宣告為 constexpr，或從 f 中移除 constexpr 限定詞。 

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
                        // as an argument to a variadic function
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
針對使用 CStringW 所建置和管理的字串，應該使用提供的 `operator LPCWSTR()` 將 CStringW 物件轉換為格式字串所預期的 C 指標。

```cpp  
CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));
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
若要更正錯誤，請將運算子 int() 宣告為 const。 

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
為了支援 expression-SFINAE，編譯器現在會在宣告範本而非具現化範本時剖析 decltype 引數。 因此，如果在 decltype 引數中找到非相依特製化，則不會延遲到具現化期間，並且會立即處理，而且會在當下診斷出任何產生的錯誤。  

下列範例顯示在宣告時引發的這類編譯器錯誤︰

```cpp  
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
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
在 Visual Studio 2015 和以前版本中，在某些情況下，編譯器會將預設屬性錯誤地識別為預設索引子。 使用 "default" 識別碼存取屬性，即可解決問題。 在 C++11 中將 default 引進為關鍵字之後，因應措施本身會變成問題。 因此，在 Visual Studio 2017 中，已修正需要因應措施的 Bug，而且編譯器現在會在使用 "default" 來存取類別的預設屬性時引發錯誤。

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
在舊版的 Visual Studio 中，編譯器在某些情況下針對呼叫已刪除之成員範本的語式錯誤會無法發出錯誤。而可能造成在執行階段當機。 下列程式碼現在會產生 C2280：「'int S<int>::f<int>(void)': 嘗試參考被刪除的函式」:
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
Visual Studio 2017 15.3 版改進了類型特性的先決條件檢查，以更嚴格地遵守標準。 此類檢查是可供指派的。 在更新版本 15.3 中，下列程式碼會產生 C2139：

```cpp
struct S; 
enum E; 
 
static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>原生至 Managed 封送處理上的新編譯器警告和執行階段檢查
從 Managed 函式對原生函式的呼叫需要封送處理。 CLR 會執行封送處理，但它並不了解 C++ 語意。 如果您以傳值方式傳遞原生物件，CLR 將會呼叫物件的複製建構函式，或是使用 BitBlt，這可能在執行階段導致未定義的行為。 
 
現在，編譯器如果可以在編譯時期時知道含有已刪除之 copy ctor 的原生物件會在原生和 Managed 界限之間以傳值方式傳遞，就會發出警告。 針對編譯器在編譯時期所不知道的那些情況，它會插入執行階段檢查，如此一來在發生語式錯誤的封送處理時，程式將會立即呼叫 std::terminate。 在更新版本 15.3 中，下列程式碼會產生 C4606：「'A': 跨越原生與管理邊界傳遞引數值需要有效的複製建構函式。 否則不會定義執行階段行為」。
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
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which will result in a double-free later. 
}
```
若要修正錯誤，請移除 `#pragma managed` 指示詞，以將呼叫者標示為原生並避免封送處理。 

### <a name="experimental-api-warning-for-winrt"></a>WinRT 的實驗性 API 警告
針對實驗和意見反應所發行的 WinRT API 會以 `Windows.Foundation.Metadata.ExperimentalAttribute` 裝飾。 在 Visual Studio 2017 15.3 版中，在遇到該屬性時，編譯器會產生警告 C4698。 舊版 Windows SDK 中的一些 API 已經以該屬性裝飾，而對這些 API 的呼叫將會啟動此編譯器警告的觸發。 新版的 Windows SDK 將從所有隨附的型別移除該屬性，但如果您使用舊版的 SDK，則需要針對隨附型別的所有呼叫隱藏這些警告。
下列程式碼會產生警告 C4698：「'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' 僅供評估之用。後續版本可能會變更或移除此功能」：
```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() //C4698
```

若要停用該警告，請加入 #pragma：

```cpp
#pragma warning(push) 
#pragma warning(disable:4698) 
 
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() 
 
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
在 C++ 中，'this' 是 X 之型別指標的 prvalue。您無法取得 'this' 的位址，或將它繫結至 lvalue 參考。 在舊版的 Visual Studio 中，編譯器可讓您執行轉型以避開此限制。 在 Visual Studio 2017 15.3 版中，編譯器會產生錯誤 C2664。

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
不得在樣板類別之成員函式的程式碼外部定義上使用預設引數。編譯器會在 /permissive 底下發出警告，並在 /permissive- 底下發出硬碟錯誤。 

在舊版的 Visual Studio 中，下列語式錯誤的程式碼可能會導致執行階段當機。 Visual Studio 2017 15.3 版會產生「警告 C5034: 'A<T>::f': 在程式碼外部定義的類別範本成員不得使用預設引數」：
```cpp
 
template <typename T> 
struct A { 
    T f(T t, bool b = false); 
}; 
 
template <typename T> 
T A<T>::f(T t, bool b = false) // C5034
{ 
... 
}
```
若要修正錯誤，請移除 "= false" 預設引數。 

### <a name="use-of-offsetof-with-compound-member-designator"></a>使用 offsetrof 搭配複合成員指示項
在 Visual Studio 2017 15.3 版中，如果使用 offsetof(T, m) (其中 m 是「複合成員指示項」)，則會在您使用 /Wall 選項編譯時產生警告。 下列程式碼的語式錯誤，且可能在執行階段造成當機。 Visual Studio 2017 15.3 版會產生「警告 C4841: 使用非標準擴充: offseto 中有複合成員指示項」:

```cpp
  
struct A { 
int arr[10]; 
}; 
 
// warning C4841: non-standard extension used: compound member designator in offsetof 
constexpr auto off = offsetof(A, arr[2]);
```
若要修正程式碼，您可以使用 pragma 來停用警告，或是變更程式碼不要使用 offsetof： 

```cpp
#pragma warning(push) 
#pragma warning(disable: 4841) 
constexpr auto off = offsetof(A, arr[2]); 
#pragma warning(pop) 
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>使用 offsetof 搭配靜態資料成員或成員函式
在 Visual Studio 2017 15.3 版中，如果使用 offsetof(T, m) (其中 m 代表靜態資料成員或成員函式)，將會導致錯誤。 下列程式碼會產生「錯誤 C4597: 未定義的行為: offsetof 套用至成員函式 'foo'」和「錯誤 C4597: 未定義的行為: offsetof 套用至靜態資料成員 'bar'」：
```cpp
 
#include <cstddef> 
 
struct A { 
int foo() { return 10; } 
static constexpr int bar = 0; 
}; 
 
constexpr auto off = offsetof(A, foo); 
Constexpr auto off2 = offsetof(A, bar);
```
 
此程式碼的語式錯誤，且可能在執行階段造成當機。 若要修正錯誤，請變更程式碼以不再叫用未定義的行為。 這是不可移植且 C++ 標準不允許的程式碼。

### <a name="new-warning-on-declspec-attributes"></a>針對 declspec 屬性的新警告
在 Visual Studio 2017 15.3 版中，如果在外部 "C" 連結規格前套用了 __declspec(…)，編譯器不再會忽略該屬性。 先前，編輯器會忽略該屬性，這可能有執行階段隱含式。 當設定 `/Wall /WX` 選項時，下列程式碼會產生「警告 C4768: 連結規格前的 __declspec 屬性被忽略」：

```cpp
 
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

若要修正此警告，請先加入 extern "C"：

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```
這個警告預設關閉，且只會影響以 `/Wall /WX` 編譯的程式碼。

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype 和對已刪除之解構函式的呼叫
在舊版的 Visual Studio 中，在與 'decltype' 相關聯的運算式內容中呼叫已刪除的解構函式時，編譯器並不會偵測到。 在 Visual Studio 2017 15.3 版中，下列程式碼會產生「錯誤 C2280:  'A<T>::~A(void)': 嘗試參考被刪除的函式」：

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
 
在 /Wv:18 下會排除警告，且預設會在警告層級 W2 下開啟。


### <a name="stdisconvertible-for-array-types"></a>陣列類型的 std::is_convertible
舊版編譯器對陣列類型的 [std::is_convertible](standard-library/is-convertible-class.md) 會給出不正確的結果。 這要求程式庫作者在使用 `std::is_convertible<…>` 類型特性時，以特殊案例處理 Visual C++ 編譯器。 下例中，靜態判斷提示能夠通過舊版 Visual Studio，但在 Visual Studio 2017 15.3 版中失敗：

```cpp
#include <type_traits>
 
using Array = char[1];
 
static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

**std::is_convertible<From, To>** 的計算是查看 imaginary 函式是否正確定義：
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

私人解構函式會讓類型成為不可建構的。 **std::is_constructible<T, Args…>** 的計算就好像已撰寫下列宣告：
```cpp 
   T obj(std::declval<Args>()…)
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
為修正程式碼，如果您想要呼叫 ::f()，請移除使用 N::f 的陳述式。

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660：區域函式宣告和引數相依查閱
區域函式宣告會將函式宣告隱藏在封閉範圍中，停用引數相依查閱。
不過，舊版的 Visual C++ 編譯器在這種情況下會執行引數相依查閱，有可能導致選擇錯誤的多載和未預期的執行階段行為。 錯誤通常是因為區域函式宣告的簽章不正確而發生。 在下列範例中，Visual Studio 2017 15.3 版會正確引發「C2660 'f': 函式不接受 2 個引數」：

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

若要修正此問題，請變更或移除 **f(S)** 簽章。

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038：初始設定式清單中的初始化順序
類別成員會依其宣告的順序初始化，而不是依它們在初始設定式清單中出現的順序。 當初始設定式清單的順序和宣告順序不一致時，舊版編譯器未發出警告。 如果某個成員的初始化依存於清單中另一個已初始化的成員，這可能導致未定義的執行階段行為。 在下列範例中，Visual Studio 2017 15.3 版 (使用 /Wall) 會引發警告「C5038: 資料成員 'A::y' 會在資料成員 'A::x' 之後初始化」：

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};

```
若要修正問題，請排列整理初始設定式清單的順序，讓它和宣告順序相同。 當一或兩個初始設定式參考基底類別成員時，就會引發類似的警告。

請注意，這個警告預設關閉，且只會影響以 /Wall 編譯的程式碼。

## <a name="see-also"></a>另請參閱  
[Visual C++ 語言一致性](visual-cpp-language-conformance.md)  

