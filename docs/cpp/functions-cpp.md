---
title: 函式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 01/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24eded7bac023bd2291e0c574012f72ba86b6bcf
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053795"
---
# <a name="functions-c"></a>函式 (C++)

函式是執行某項作業的程式碼區塊。 函式可以選擇性地定義輸入參數，以讓呼叫端將引數傳遞給函式。 函式可以選擇性地傳回值做為輸出。 函式適用於將一般作業封裝在單一可重複使用的區塊中，而且其名稱最好可清楚描述該函式的作用。 下列函式會接受來自呼叫端的兩個整數，並傳回其總和;並*b*會*參數*型別的**int**。

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

此函式可以叫用，或*稱為*，從任何數目的程式中的位置。 傳遞至函數的值為*引數*，其類型必須是函式定義中的參數類型相容。

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

函式長度沒有實際限制，但良好的設計目標在於函式可以執行單一完整定義的工作。 如果可能，應該將複雜演算法分解成容易了解的較簡單函式。

在類別範圍定義的函式稱為成員函式。 與其他語言不同，在 C++ 中，函式也可以定義於命名空間範圍 (包括隱含全域命名空間)。 這類函式會呼叫*免費函式*或是*非成員函式*; 它們廣泛用於標準程式庫。

函式可能*多載*，這表示不同版本的函式可能會共用相同的名稱，如果它們的差異數目及/或型式參數的型別。 如需詳細資訊，請參閱 <<c0> [ 函式多載](../cpp/function-overloading.md)。

## <a name="parts-of-a-function-declaration"></a>函式宣告的組件

最小的函式*宣告*包含傳回型別、 函式名稱和參數清單 （這可能是空的），以及提供編譯器其他指示的選擇性關鍵字。 下列範例是函式宣告：

```cpp
int sum(int a, int b);
```

函式定義包含宣告，再加上*主體*，這是大括號之間的所有程式碼：

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

後面接著一個分號的函式宣告可能會出現在程式的多個位置。 它必須出現在每個轉譯單位中該函式的任何呼叫之前。 根據「一個定義規則 (ODR)」，函式定義只能出現在程式中一次。

函式宣告的必要組件如下：

1. 傳回的型別，指定函式會傳回值的型別，或是**void**如果未不傳回任何值。 在 C + + 11 中，**自動**是有效的傳回型別，它會指示編譯器推斷 return 陳述式的類型。 在 C++14 中，也允許 decltype(auto)。 如需詳細資訊，請參閱下面的＜傳回類型中的類型推斷＞。

1. 函式名稱，開頭必須為字母或底線，而且不能包含空格。 一般而言，標準程式庫函式名稱中的前置底線表示私用成員函式或不是要供您的程式碼使用的非成員函式。

1. 參數清單，是以大括號分隔並以逗號隔開的零或多個參數集合，指定類型以及選擇性指定可用來存取函式主體內值的本機名稱。

函式宣告的選擇性組件如下：

1. `constexpr`，表示函式的傳回值是常數值，可在編譯時期計算。

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. 連結規格， **extern**或是**靜態**。

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   如需詳細資訊，請參閱 <<c0> [ 程式和連結](../cpp/program-and-linkage-cpp.md)。

1. **內嵌**，這個值會指示編譯器將本身的函式程式碼取代每個呼叫的函式。 如果函式執行速度快速並在效能關鍵的程式碼區段中重複予以叫用，則內嵌有助於提高效能。

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   如需詳細資訊，請參閱 <<c0> [ 內嵌函式](../cpp/inline-functions-cpp.md)。

1. A`noexcept`運算式，指定是否函式可能會擲回例外狀況。 在下列範例中，此函式不會擲回例外狀況如果`is_pod`運算式會評估 **，則為 true**。

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   如需詳細資訊，請參閱 < [noexcept](../cpp/noexcept-cpp.md)。

1. （只有成員函式）Cv 限定詞，指定函式是否**const**或是**volatile**。

1. （只有成員函式）**虛擬**， `override`，或`final`。 **虛擬**指定可以在衍生類別中覆寫函式。 `override` 表示衍生類別中的函式會覆寫虛擬函式。 `final` 表示無法覆寫任何進一步衍生類別中的函式。 如需詳細資訊，請參閱 <<c0> [ 虛擬函式](../cpp/virtual-functions.md)。

1. （只有成員函式）**靜態**套用至成員函式表示函式不是任何物件類別的執行個體相關聯。

1. （僅非靜態成員函式）Ref-qualifier，後者會指定哪個多載函式時選擇的編譯器在隱含物件參數 (\*這) 是右值參考與左值參考。 如需詳細資訊，請參閱 <<c0> [ 函式多載](function-overloading.md#ref-qualifiers)。

下圖顯示函式定義的組件。 陰影區域是函式主體。

![函式定義的組件](../cpp/media/vc38ru1.gif "vc38RU1")函式定義的組件

## <a name="function-definitions"></a>函式定義

A*函式定義*宣告和函式主體中，括在大括號，其中包含區域變數宣告、 陳述式和運算式所組成。 下列範例會顯示完整的函式定義：

```cpp
    int foo(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       if(strcmp(s, "default") != 0)
       {
            value = mc.do_something(i);
       }
       return value;
    }
```

主體內宣告的變數稱為區域變數。 它們會在函式結束時消失；因此，函式永遠不應該傳回區域變數的參考！

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>const 和 constexpr 函式

您可以宣告為成員函式**const**指定函式，不允許變更的任何類別中的資料成員的值。 藉由宣告成員函式做**const**，協助強制執行編譯器*常數正確性*。 有人不小心嘗試修改的物件使用的函式宣告為**const**，就會引發編譯器錯誤。 如需詳細資訊，請參閱 < [const](const-cpp.md)。

宣告為函式`constexpr`它所產生的值時可能可以在編譯時期決定。 Constexpr 函式通常比一般函式更快執行。 如需詳細資訊，請參閱 < [constexpr](constexpr-cpp.md)。

## <a name="function-templates"></a>函式樣板

函式樣板與類別樣板類似；它會根據樣板引數產生具象函式。 在許多情況下，樣板可以推斷型別引數，因此不需要明確指定它們。

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

如需詳細資訊，請參閱[函式樣板](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>函式參數和引數

函式具有零或多個類型的參數清單 (以逗號分隔)，且各有用來在函式主體內進行存取的名稱。 函式樣板可以指定其他類型或值參數。 呼叫端會傳遞引數，而引數是類型與參數清單相容的具象值。

根據預設，會以傳值方式將引數傳遞給函式，這表示函式會收到所傳遞物件的複本。 針對大型物件，建立複本可能十分耗費資源，而且不一定是必要的。 若要使以傳址 （特別是左值參考） 傳遞的引數，將加入參數的參考數量詞：

```cpp
void DoSomething(std::string& input){...}
```

函式修改透過傳址方式所傳遞的引數時，會修改原始物件，而不是本機複本。 若要防止函式修改這類引數，請將參數限定為 const&：

```cpp
void DoSomething(const std::string& input){...}
```

**C + + 11:** 若要明確處理透過右值參考或左值參考傳遞引數，使用雙連字號的參數上表示通用參考：

```cpp
void DoSomething(const std::string&& input){...}
```

一個關鍵字所宣告的函式**void**的參數宣告清單會採用任何引數，只要關鍵字**void**為第一個和唯一引數宣告清單的成員。 類型引數**void**其他位置清單中會產生錯誤。 例如: 

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

請注意，雖然您不能指定**void**除了如所述的引數，型別衍生自型別**void** (例如指標**void**和陣列**void**) 可以出現任何位置引數宣告清單。

### <a name="default-arguments"></a>預設引數

函式簽章中的最後一個參數或參數可能獲指派預設引數，這表示除非呼叫端想要指定其他值，否則在呼叫函式時可能會省略引數。

```cpp
int DoSomething(int num,
    string str,
    Allocator& alloc = defaultAllocator)
{ ... }

// OK both parameters are at end
int DoSomethingElse(int num,
    string str = string{ "Working" },
    Allocator& alloc = defaultAllocator)
{ ... }

// C2548: 'DoMore': missing default parameter for parameter 2
int DoMore(int num = 5, // Not a trailing parameter!
    string str,
    Allocator& = defaultAllocator)
{...}
```

如需詳細資訊，請參閱 <<c0> [ 預設引數](../cpp/default-arguments.md)。

## <a name="function-return-types"></a>函式傳回型別

函式可能不會傳回另一個函式或內建陣列;不過它可以傳回這些類型的指標或*lambda*，這會產生函式物件。 除了這些情況下，函式可能會傳回位於範圍內，任何類型的值，或者它可能會傳回任何值，在此情況下傳回的型別是**void**。

### <a name="trailing-return-types"></a>尾端傳回類型

"ordinary" 傳回型別位於函式簽章左邊。 A*尾端傳回型別*位於最右邊的簽章，並在前面加上-> 運算子。 傳回值的類型取決於樣板參數時，尾端傳回型別特別適用於函式樣板。

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

當**自動**使用尾端傳回型別結合，只是做為預留位置的任何 decltype 運算式所產生，，和本身不會執行類型推斷。

## <a name="function-local-variables"></a>函式區域變數

函式主體內宣告的變數稱為*區域變數*或只是*本機*。 非靜態區域變數只顯示於函式主體內，如果它們宣告於堆疊上，則會在函式結束時消失。 如果建構區域變數並以傳值方式傳回區域變數，則編譯器通常會執行傳回值最佳化，以避免不必要的複製作業。 如果您以傳址方式傳回區域變數，則編譯器會發出警告，因為呼叫端使用該參考的任何嘗試都是在終結區域變數之後。

在 C++ 中，區域變數可能宣告為靜態。 變數只會顯示在函式主體內，但函式的所有執行個體都有變數的單一複本。 區域靜態物件會在 `atexit` 指定的終止時被終結。 如果因為程式的控制流程略過其宣告而未建構靜態物件，就不會嘗試終結該物件。

##  <a name="type_deduction"></a> 傳回型別 (C + + 14) 中的類型推斷

在 c++14 中，您可以使用**自動**指示編譯器推斷傳回型別，從函式主體，而不需要提供尾端傳回型別。 請注意，**自動**一律會推斷為傳值傳回。 使用 `auto&&` 指示編譯器推斷參考。

在此範例中，**自動**會推斷為 lhs 與 rhs 總和的非常數值複本。

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

請注意，**自動**不會保留的推斷的類型的 const-ness。 針對轉送它的傳回值需要保留 const-ness 或 ref-ness 的其引數的函式，您可以使用**decltype （auto)** 關鍵字，它會使用**decltype**型別推斷規則和會保留所有的型別資訊。 **decltype （auto)** 可能用於在左邊的 ordinary 傳回值，或做為結尾的傳回值。

下列範例 (從程式碼為基礎[N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html))，會顯示**decltype （auto)** 來啟用範本之前，不已知的傳回型別中的函式引數完美轉送具現化。

```cpp
template<typename F, typename Tuple = tuple<T...>, int... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);
}

template<typename F, typename Tuple = tuple<T...>,
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>
   decltype( auto)
    apply(F&& f, Tuple&& args)
{
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());
}
}
```

## <a name="multi_val"></a> 從函式傳回多個值

有各種方式從函式傳回多個值：

1. 封裝中具名的類別或結構物件的值。 需要的類別或結構的定義，以便顯示給呼叫者：

    ```cpp
    #include <string>
    #include <iostream>

    using namespace std;

    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        S s = g();
        cout << s.name << " " << s.num << endl;
        return 0;
    }
    ```

1. 傳回的 std:: tuple 或 std:: pair 物件：

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }

    int main()
    {
        auto t = f();
        cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;

        // --or--

        int myval;
        string myname;
        double mydecimal;
        tie(myval, myname, mydecimal) = f();
        cout << myval << " " << myname << " " << mydecimal << endl;

        return 0;
    }
    ```

1. **Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): 使用結構化繫結。 結構化繫結的優點是，儲存傳回值的變數會初始化宣告它們，同時在某些情況下可能會更具效率。 在這個陳述式-`auto[x, y, z] = f();`-在方括號引進並初始化會在整個函式區塊的範圍的名稱。

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }
    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        auto[x, y, z] = f(); // init from tuple
        cout << x << " " << y << " " << z << endl;

        auto[a, b] = g(); // init from POD struct
        cout << a << " " << b << endl;
        return 0;
    }
    ```

1. 除了使用本身的傳回值，您可以 「 傳回 」 值定義任何數目的參數，使用依參照傳遞，讓函式可以修改或初始化之物件的呼叫端提供的值。 如需詳細資訊，請參閱 <<c0> [ 參考類型函式引數](reference-type-function-arguments.md)。

## <a name="function-pointers"></a>函式指標

C++ 支援函式指標的方式與 C 語言相同。 不過，較具類型安全的替代方案通常是使用函式物件。

建議**typedef**能用來宣告函式指標類型的別名，如果宣告函式傳回的函式指標類型。  例如

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

如果沒有這樣做，函式宣告的適當語法可能會從函式指標的宣告子語法推算，方法是將識別項 (在上述範例中為 `fp`) 取代為函式名稱和引數清單，如下所示：

```cpp
int (*myFunction(char* s))(int);
```

上述宣告相當於上面使用 typedef 的宣告。

## <a name="see-also"></a>另請參閱

[函式多載](../cpp/function-overloading.md)<br/>
[具有變數引數清單的函式](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[明確的預設和已刪除的函式](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[函式上的引數相依名稱 (Koenig) 查閱](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[預設引數](../cpp/default-arguments.md)<br/>
[內嵌函式](../cpp/inline-functions-cpp.md)
