---
title: "C++ 編譯器一致性改善 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: BrianPeek
ms.author: brpeek
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
translationtype: Human Translation
ms.sourcegitcommit: f9e63f47a8df69b52a6a12688e84602981d20dae
ms.openlocfilehash: 2d86588df2b20861dff5b940d2f0c7c3afd857fb
ms.lasthandoff: 03/21/2017

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


如需到 Visual Studio 2015 Update 3 為止的完整一致性改善清單，請參閱 [Visual C++ What's New 2003 through 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx)(從 2003 到 2015 的 Visual C++ 新功能)。

## <a name="bug-fixes"></a>Bug 修正
### <a name="copy-list-initialization"></a>Copy-list-initialization
Visual Studio 2017 使用 Visual Studio 2015 中攔截不到且可能導致當機或未定義執行階段行為的初始設定式清單，正確地引發與建立物件相關的編譯器錯誤。  根據 N4594 13.3.1.7p1，在 copy-list-initialization 中，編譯器需要考慮使用明確建構函式來進行多載解析，但必須在實際選擇該多載時引發錯誤。 

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
在 constexpr 內容中條件式評估作業的左運算元無效時，Visual Studio 2017 會正確地引發錯誤。 下列程式碼是在 Visual Studio 2015 中編譯，但無法在 Visual Studio 2017 中編譯：

```cpp  
template<int N>
struct array 
{
       int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
       return arr.size() == 10 || arr.size() == 11; // error starting in Visual Studio 2017
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
或者先執行靜態轉型來轉換物件，再將其傳遞︰
```cpp  
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```
針對使用 CStringW 所建置和管理的字串，應該使用提供的「運算子 LPCWSTR()」將 CStringW 物件轉型為格式字串所預期的 C 指標。

```cpp  
CStringW str1;
CStringW str2;
str1.Format(… , static_cast<LPCWSTR>(str2));
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
根據 C++ 標準，宣告於匿名命名空間中的類別具有內部連結，因此無法匯出。 在 Visual Studio 2015 和更早的版本中，並未強制執行此規則。 在 Visual Studio 2017 中，會部分強制執行此規則。 下列範例會在 Visual Studio 2017 中引發這個錯誤：「錯誤 C2201: 'const `anonymous namespace'::S1::`vftable'': 必須具有外部連結以便匯出/匯入。」

```cpp
namespace
{
    struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
}
```

### <a name="classes-declared-in-anonymous-namespaces"></a>宣告於匿名命名空間中的類別
根據 C++ 標準，宣告於匿名命名空間中的類別具有內部連結，因此無法匯出。 在 Visual Studio 2015 和更早的版本中，並未強制執行此規則。 在 Visual Studio 2017 中，會部分強制執行此規則。 下列範例會在 Visual Studio 2017 中引發這個錯誤：「錯誤 C2201: 'const `anonymous namespace'::S1::`vftable'': 必須具有外部連結以便匯出/匯入。」

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>實值類別成員的預設初始設定式 (C++/CLI)
在 Visual Studio 2015 和以前版本中，編譯器允許 (但忽略) 實值類別成員的預設成員初始設定式。  實值類別的預設初始化一律會以零初始化成員；不允許預設建構函式。  在 Visual Studio 2017 中，預設成員初始設定式會引發編譯器錯誤，如這個範例中所示︰

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

## <a name="see-also"></a>另請參閱  
[Visual C++ 語言一致性](visual-cpp-language-conformance.md)  

