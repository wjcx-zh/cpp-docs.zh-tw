---
title: 函式 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
ms.openlocfilehash: 5beadbbf283a64f12dab7f0ee39a267ec1797861
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213433"
---
# <a name="functions-c"></a>函式 (C++)

函式是執行某項作業的程式碼區塊。 函式可以選擇性地定義輸入參數，以讓呼叫端將引數傳遞給函式。 函式可以選擇性地傳回值做為輸出。 函式適用於將一般作業封裝在單一可重複使用的區塊中，而且其名稱最好可清楚描述該函式的作用。 下列函式會接受來自呼叫端的兩個整數，並傳回其總和。*a*和*b*是*parameters*類型的參數 **`int`** 。

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

您可以從程式中任意數目的位置叫用或*呼叫*函式。 傳遞給函式的值是*引數*，其類型必須與函式定義中的參數類型相容。

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

函式長度沒有實際限制，但良好的設計目標在於函式可以執行單一完整定義的工作。 如果可能，應該將複雜演算法分解成容易了解的較簡單函式。

在類別範圍定義的函式稱為成員函式。 與其他語言不同，在 C++ 中，函式也可以定義於命名空間範圍 (包括隱含全域命名空間)。 這類函式稱為*免費函數*或*非成員函式*;它們在標準程式庫中廣泛使用。

函式可能會多載，這表示如果函式的不同版本因型式參數的數目和/或類型*不同，可能*會共用相同的名稱。 如需詳細資訊，請參閱[函數](../cpp/function-overloading.md)多載。

## <a name="parts-of-a-function-declaration"></a>函式宣告的組件

最小函式*宣告包含傳回*類型、函式名稱和參數清單（可能是空的），以及提供其他指示給編譯器的選擇性關鍵字。 下列範例是函式宣告：

```cpp
int sum(int a, int b);
```

函式定義包含宣告，加上*主體*，這是大括弧之間的所有程式碼：

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

後面接著一個分號的函式宣告可能會出現在程式的多個位置。 它必須出現在每個轉譯單位中該函式的任何呼叫之前。 根據「一個定義規則 (ODR)」，函式定義只能出現在程式中一次。

函式宣告的必要組件如下：

1. 傳回型別，指定函式所傳回之值的型別， **`void`** 如果沒有傳回值，則為。 在 c + + 11 中， **`auto`** 是有效的傳回型別，可指示編譯器從 return 語句推斷型別。 在 c + + 14 中， `decltype(auto)` 也允許。 如需詳細資訊，請參閱下面的＜傳回型別中的類型推斷＞。

1. 函式名稱，開頭必須為字母或底線，而且不能包含空格。 一般而言，標準程式庫函式名稱中的前置底線表示私用成員函式或不是要供您的程式碼使用的非成員函式。

1. 參數清單，是以大括號分隔並以逗號隔開的零或多個參數集合，指定類型以及選擇性指定可用來存取函式主體內值的本機名稱。

函式宣告的選擇性組件如下：

1. **`constexpr`**，這表示函數的傳回值是常數值，可以在編譯時期計算。

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. 其連結規格， **`extern`** 或 **`static`** 。

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   如需詳細資訊，請參閱[轉譯單位和連結](../cpp/program-and-linkage-cpp.md)。

1. **`inline`**，指示編譯器將函式的每個呼叫都取代為函式程式碼本身。 如果函式執行速度快速並在效能關鍵的程式碼區段中重複予以叫用，則內嵌有助於提高效能。

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   如需詳細資訊，請參閱[內嵌函數](../cpp/inline-functions-cpp.md)。

1. **`noexcept`** 運算式，指定函數是否可以擲回例外狀況。 在下列範例中，如果運算式評估為，則函數不會擲回例外狀況 `is_pod` **`true`** 。

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   如需詳細資訊，請參閱 [`noexcept`](../cpp/noexcept-cpp.md)。

1. （僅限成員函式）Cv 限定詞，指定函數是 **`const`** 或 **`volatile`** 。

1. （僅限成員函式） **`virtual`** 、 **`override`** 或 **`final`** 。 **`virtual`** 指定可在衍生類別中覆寫函數。 **`override`** 表示衍生類別中的函式會覆寫虛擬函式。 **`final`** 表示無法在任何進一步的衍生類別中覆寫函數。 如需詳細資訊，請參閱[虛擬](../cpp/virtual-functions.md)函式。

1. （僅限成員函式） **`static`** 套用至成員函式表示函式未與類別的任何物件實例相關聯。

1. （僅限非靜態成員函式）Ref-限定詞，指定當隱含物件參數（ `*this` ）為右值參考，或左值參考時，編譯器所要選擇的函數多載。 如需詳細資訊，請參閱[函數](function-overloading.md#ref-qualifiers)多載。

下圖顯示函式定義的組件。 陰影區域是函式主體。

![函式定義的部分](../cpp/media/vc38ru1.gif "函式定義的部分") <br/>
函式定義的部分

## <a name="function-definitions"></a>函式定義

*函式定義*包含宣告和函式主體，以大括弧括住，其中包含變數宣告、語句和運算式。 下列範例顯示完整的函式定義：

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

您可以將成員函式宣告為 **`const`** ，以指定不允許函數變更類別中任何資料成員的值。 藉由將成員函式宣告為 **`const`** ，您可以協助編譯器強制執行*const 正確性*。 如果有人錯誤地嘗試使用宣告為的函式來修改物件 **`const`** ，則會引發編譯器錯誤。 如需詳細資訊，請參閱[const](const-cpp.md)。

宣告函式，就像 **`constexpr`** 它所產生的值可能會在編譯時期決定一樣。 Constexpr 函式的執行速度通常比一般函數快。 如需詳細資訊，請參閱 [`constexpr`](constexpr-cpp.md)。

## <a name="function-templates"></a>函式樣板

函式樣板與類別樣板類似；它會根據樣板引數產生具象函式。 在許多情況下，樣板可以推斷類型引數，因此不需要明確指定它們。

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

如需詳細資訊，請參閱[函數範本](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>函式參數和引數

函式具有零或多個類型的參數清單 (以逗號分隔)，且各有用來在函式主體內進行存取的名稱。 函式樣板可以指定其他類型或值參數。 呼叫端會傳遞引數，而引數是類型與參數清單相容的具象值。

根據預設，會以傳值方式將引數傳遞給函式，這表示函式會收到所傳遞物件的複本。 針對大型物件，建立複本可能十分耗費資源，而且不一定是必要的。 若要讓引數以傳址方式傳遞（特別是左值參考），請將參考數量詞新增至參數：

```cpp
void DoSomething(std::string& input){...}
```

函式修改透過傳址方式所傳遞的引數時，會修改原始物件，而不是本機複本。 若要防止函數修改這類引數，請將參數限定為 const&：

```cpp
void DoSomething(const std::string& input){...}
```

**C + + 11：** 若要明確處理由右值參考或左值參考所傳遞的引數，請在參數上使用雙連字號來表示通用參考：

```cpp
void DoSomething(const std::string&& input){...}
```

**`void`** 只要關鍵字 **`void`** 是引數宣告清單的第一個和唯一成員，使用參數宣告清單中的單一關鍵字所宣告的函式就不會採用引數。 清單中其他位置的類型引數會 **`void`** 產生錯誤。 例如：

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

請注意，雖然 **`void`** 除了這裡所述之外，指定引數是不合法的，但衍生自類型的類型 **`void`** （例如 **`void`** 的指標和陣列 **`void`** ）可以出現在引數宣告清單的任何位置。

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

如需詳細資訊，請參閱[預設引數](../cpp/default-arguments.md)。

## <a name="function-return-types"></a>函式傳回型別

函式不能傳回另一個函數或內建陣列;不過，它可以傳回這些類型的指標，或是會產生函式物件的*lambda*。 除了這些情況之外，函式可能會傳回範圍內任何類型的值，或不會傳回任何值，在此情況下，傳回類型為 **`void`** 。

### <a name="trailing-return-types"></a>尾端傳回類型

"ordinary" 傳回型別位於函式簽章左邊。 *尾端傳回類型*位在簽章的最右邊，且前面加上 **`->`** 運算子。 傳回值的類型取決於樣板參數時，尾端傳回類型特別適用於函式樣板。

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

當 **`auto`** 與尾端傳回型別搭配使用時，它只會當做 decltype 運算式所產生的預留位置，而且本身不會執行型別推斷。

## <a name="function-local-variables"></a>函式區域變數

在函式主體內宣告的變數稱為「區域變數」（ *local variable* ），或簡稱為 *「區域變數」。* 非靜態區域變數只顯示於函式主體內，如果它們宣告於堆疊上，則會在函式結束時消失。 當您建立本機變數並以傳值方式傳回它時，編譯器通常會執行*已命名的傳回值優化*，以避免不必要的複製作業。 如果您以傳址方式傳回區域變數，則編譯器會發出警告，因為呼叫端使用該參考的任何嘗試都是在終結區域變數之後。

在 C++ 中，區域變數可能宣告為靜態。 變數只會顯示在函式主體內，但函式的所有執行個體都有變數的單一複本。 區域靜態物件會在 `atexit` 指定的終止時被終結。 如果因為程式的控制流程略過其宣告而未建構靜態物件，就不會嘗試終結該物件。

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>傳回類型中的類型推斷（c + + 14）

在 c + + 14 中，您可以使用 **`auto`** 指示編譯器從函式主體推斷傳回型別，而不需要提供尾端傳回型別。 請注意， **`auto`** 一律會會推算為逐值。 使用 `auto&&` 指示編譯器推斷參考。

在此範例中，將會推算 **`auto`** 為 lhs 和 rhs 總和的非 const 值複本。

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

請注意，不 **`auto`** 會保留其所會推算之類型的常數性質。 如果轉送函式的傳回值需要保留其引數的常數性質或 ref 特性，您可以使用 **`decltype(auto)`** 關鍵字，這會使用 **`decltype`** 型別推斷規則並保留所有型別資訊。 **`decltype(auto)`** 可用來做為左側的一般傳回值，或做為尾端的傳回值。

下列範例（以[N3493](https://wg21.link/n3493)的程式碼為基礎）顯示 **`decltype(auto)`** 如何使用，在範本具現化之前，能夠完美地轉送不知道的傳回型別中的函式引數。

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
```

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>從函式傳回多個值

有各種方式可從函式傳回一個以上的值：

1. 封裝已命名的類別或結構物件中的值。 要求呼叫者可以看到類別或結構定義：

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

1. 傳回 std：：元組或 std：:p 空中物件：

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

1. **Visual Studio 2017 15.3 和更新版本**（適用于 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ）：使用結構化系結。 結構化系結的優點是，儲存傳回值的變數會在宣告時初始化，在某些情況下可能會大幅提高效率。 在語句中 `auto[x, y, z] = f();` ，方括弧會引進並初始化整個函式區塊範圍內的名稱。

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

1. 除了使用傳回值本身之外，您還可以藉由定義任意數目的參數來「傳回」值，以使用「傳遞參考」，讓函式可以修改或初始化呼叫者所提供的物件值。 如需詳細資訊，請參閱[參考型別函式引數](reference-type-function-arguments.md)。

## <a name="function-pointers"></a>函式指標

C++ 支援函式指標的方式與 C 語言相同。 不過，較具類型安全的替代方案通常是使用函式物件。

如果宣告的函式會傳回函式 **`typedef`** 指標類型，建議使用來宣告函數指標類型的別名。  例如：

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

如果沒有這樣做，函式宣告的適當語法可能會從函式指標的宣告子語法推算，方法是將識別項 (在上述範例中為 `fp`) 取代為函式名稱和引數清單，如下所示：

```cpp
int (*myFunction(char* s))(int);
```

上述宣告相當於使用上述的宣告 **`typedef`** 。

## <a name="see-also"></a>另請參閱

[函數多載](../cpp/function-overloading.md)<br/>
[具有變數引數清單的函式](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[明確預設和已刪除的函式](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[函式上的引數相依名稱（Koenig）查閱](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[預設引數](../cpp/default-arguments.md)<br/>
[內嵌函數](../cpp/inline-functions-cpp.md)
