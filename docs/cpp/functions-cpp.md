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
ms.openlocfilehash: 1425ddebffc150158e88e44b1d2c22e3f85e5a31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375742"
---
# <a name="functions-c"></a>函式 (C++)

函式是執行某項作業的程式碼區塊。 函式可以選擇性地定義輸入參數，以讓呼叫端將引數傳遞給函式。 函式可以選擇性地傳回值做為輸出。 函式適用於將一般作業封裝在單一可重複使用的區塊中，而且其名稱最好可清楚描述該函式的作用。 以下函數接受調用方的兩個整數並返回其總和;*a*與*b*是**int**型態的*參數*。

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

函式可以從應用程式中的任何數量的位置呼叫或*呼叫*。 傳遞給函數的值是*參數*,其類型必須與函數定義中的參數類型相容。

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

函式長度沒有實際限制，但良好的設計目標在於函式可以執行單一完整定義的工作。 如果可能，應該將複雜演算法分解成容易了解的較簡單函式。

在類別範圍定義的函式稱為成員函式。 與其他語言不同，在 C++ 中，函式也可以定義於命名空間範圍 (包括隱含全域命名空間)。 此類函數稱為*自由函數*或*非成員函數*;它們在標準庫中廣泛使用。

函數可能*過載*,這意味著函數的不同版本如果因形式參數的數量和/或類型而異,則可以共用相同的名稱。 有關詳細資訊,請參閱[函數重載](../cpp/function-overloading.md)。

## <a name="parts-of-a-function-declaration"></a>函式宣告的組件

最小函數*聲明*由返回類型、函數名稱和參數清單(可能為空)以及向編譯器提供其他指令的可選關鍵字組成。 以下範例是函數聲明:

```cpp
int sum(int a, int b);
```

函數定義由聲明加上*正文*組成,這是大括弧之間的所有代碼:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

後面接著一個分號的函式宣告可能會出現在程式的多個位置。 它必須出現在每個轉譯單位中該函式的任何呼叫之前。 根據「一個定義規則 (ODR)」，函式定義只能出現在程式中一次。

函式宣告的必要組件如下：

1. 返回類型,它指定函數返回的值的類型,如果未返回值,則**為 void。** 在 C++11 中 **,auto**是一種有效的返回類型,它指示編譯器從返回語句推斷該類型。 在 C++14 中，也允許 decltype(auto)。 如需詳細資訊，請參閱下面的＜傳回型別中的類型推斷＞。

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

1. 已連桿規範,**外部**或**靜態**。

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   有關詳細資訊,請參閱[翻譯單元和連結](../cpp/program-and-linkage-cpp.md)。

1. **內聯**,指示編譯器用函數代碼本身替換函數的每個調用。 如果函式執行速度快速並在效能關鍵的程式碼區段中重複予以叫用，則內嵌有助於提高效能。

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   有關詳細資訊,請參閱[內聯函數](../cpp/inline-functions-cpp.md)。

1. 表達式`noexcept`,它指定函數是否可以引發異常。 在下面的範例中,如果`is_pod`表達式計算為**true,** 則函數不會引發異常。

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   有關詳細資訊,請參閱[no](../cpp/noexcept-cpp.md)

1. (僅限成員函數)cv 修飾詞,用於指定函數是**const**還是**易失性**。

1. (僅限成員函數)**虛擬**`override`、`final`或 。 **虛擬**指定可以在派生類中重寫函數。 `override` 表示衍生類別中的函式會覆寫虛擬函式。 `final` 表示無法覆寫任何進一步衍生類別中的函式。 有關詳細資訊,請參閱[虛擬函數](../cpp/virtual-functions.md)。

1. (僅限成員函數)應用於成員函數的**靜態**表示函數不與類的任何物件實例相關聯。

1. (僅限非靜態成員函數)ref 限定符,它向編譯器指定函數的重載,以選擇隱式物件參數 (this)\*何時是 rvalue 引用與 lvalue 引用。 有關詳細資訊,請參閱[函數重載](function-overloading.md#ref-qualifiers)。

下圖顯示函式定義的組件。 陰影區域是函式主體。

![函式定義的部分](../cpp/media/vc38ru1.gif "函式定義的部分") <br/>
函式定義的部分

## <a name="function-definitions"></a>函式定義

*函數定義*由聲明和函數體組成,以大括弧括起來,其中包含變數聲明、語句和表達式。 下面的範例顯示了一個完整的函數定義:

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

## <a name="const-and-constexpr-functions"></a>const 與 constexpr 函式

可以將成員函數聲明為**const,** 以指定不允許該函數更改類中任何資料成員的值。 透過指定成員函數宣告為**const,** 您可以幫助編譯器強制執行*const 正確性*。 如果有人錯誤地嘗試使用聲明為**const**的函數修改物件,則引發編譯器錯誤。 有關詳細資訊,請參閱[const](const-cpp.md)。

在編譯`constexpr`時可以確定函數生成的值的時間。 缺點函數通常執行速度比常規函數快。 有關詳細資訊,請參閱[constexpr](constexpr-cpp.md)。

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

有關詳細資訊,請參閱[函數範本](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>函式參數和引數

函式具有零或多個類型的參數清單 (以逗號分隔)，且各有用來在函式主體內進行存取的名稱。 函式樣板可以指定其他類型或值參數。 呼叫端會傳遞引數，而引數是類型與參數清單相容的具象值。

根據預設，會以傳值方式將引數傳遞給函式，這表示函式會收到所傳遞物件的複本。 針對大型物件，建立複本可能十分耗費資源，而且不一定是必要的。 要導致透過引用傳遞參數(特別是 lvalue 引用),向參數加入引飾詞:

```cpp
void DoSomething(std::string& input){...}
```

函式修改透過傳址方式所傳遞的引數時，會修改原始物件，而不是本機複本。 為了防止函數修改此類參數,將參數限定為 const&:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:** 要顯式處理由 rvalue 引用或 lvalue 引用傳遞的參數,請使用參數上的雙放大器,以指示通用引用:

```cpp
void DoSomething(const std::string&& input){...}
```

參數聲明清單中使用單個關鍵字**void**聲明的函數不採用任何參數,只要關鍵字**void**是參數聲明清單的第一個也是唯一的成員。 清單中其他位置的類型**void**的參數會產生錯誤。 例如：

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

請注意,雖然指定**void**參數是非法的,但此處概述的除外,但從類型**void**派生的類型(如指向**void**的指標和**void**陣列)可以出現在參數聲明清單的任意位置。

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

有關詳細資訊,請參閱[預設參數](../cpp/default-arguments.md)。

## <a name="function-return-types"></a>函式傳回型別

函數不能返回其他函數或內置陣列;但是,它可以返回指向這些類型的指標,或生成函數物件的*lambda*。 除這些情況外,函數可以返回作用網域中任何類型的值,或者它可能不返回任何值,在這種情況下,傳回類型為**void**。

### <a name="trailing-return-types"></a>尾端傳回類型

"ordinary" 傳回型別位於函式簽章左邊。 *尾隨返回類型*位於簽名的最右側,前面有 -> 運算符。 傳回值的類型取決於樣板參數時，尾端傳回類型特別適用於函式樣板。

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

當**自動**與尾隨返回類型結合使用時,它只是作為 deltype 表達式生成的任何位置符,並且本身不執行類型推導。

## <a name="function-local-variables"></a>函式區域變數

在函數體內聲明的變數稱為*局部變數*或只是*局部*變數 。 非靜態區域變數只顯示於函式主體內，如果它們宣告於堆疊上，則會在函式結束時消失。 建構局部變數並按值返回時,編譯器通常可以執行*命名返回值優化*以避免不必要的複製操作。 如果您以傳址方式傳回區域變數，則編譯器會發出警告，因為呼叫端使用該參考的任何嘗試都是在終結區域變數之後。

在 C++ 中，區域變數可能宣告為靜態。 變數只會顯示在函式主體內，但函式的所有執行個體都有變數的單一複本。 區域靜態物件會在 `atexit` 指定的終止時被終結。 如果因為程式的控制流程略過其宣告而未建構靜態物件，就不會嘗試終結該物件。

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>在退貨類型中鍵入扣除 (C++14)

在 C++14 中,可以使用**auto**指示編譯器從函數體推斷返回類型,而無需提供尾隨返回類型。 請注意,**自動**始終推匯出到按值返回。 使用 `auto&&` 指示編譯器推斷參考。

在此範例中,**自動**將推斷為 lhs 和 rh 和總和的非 const 值副本。

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

請注意,**自動**不會保留它推導的類型的共性。 對於返回值需要保留其參數的 const 或 ref-ness 的轉寄函數,可以使用**decltype(自動)** 關鍵字,該關鍵字使用**decltype 類型**推理規則並保留所有類型資訊。 **deltype(自動)** 可用作左側的普通返回值,或用作尾隨返回值。

以下範例(基於[N3493](https://wg21.link/n3493)中的代碼)顯示**用於**在迴轉類型中啟用函數參數的完美轉發(直到範本實例化之前,這些函數參數是不知道的)。

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

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>從函數傳回多個值

從函數傳回多個值的方法有多種:

1. 封裝命名類或結構物件中的值。 要求類別或結構定義對呼叫方可見:

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

1. 返回一個 std::元組或下:p:航空物體:

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

1. **Visual Studio 2017 版本 15.3 及更高版本**(提供[/std:c++17):](../build/reference/std-specify-language-standard-version.md)使用結構化綁定。 結構化綁定的優點是,存儲返回值的變數在聲明它們的同時初始化,在某些情況下,這些變數的效率會高得多。 在此語句中`auto[x, y, z] = f();`-- -- 括弧引入並初始化整個函數塊範圍內的名稱。

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

1. 除了使用返回值本身外,還可以通過定義任意數量的參數來使用逐個引用來"返回"值,以便函數可以修改或初始化調用方提供的物件的值。 有關詳細資訊,請參閱[參考型態函數參數](reference-type-function-arguments.md)。

## <a name="function-pointers"></a>函式指標

C++ 支援函式指標的方式與 C 語言相同。 不過，較具類型安全的替代方案通常是使用函式物件。

如果聲明返回函數指標類型的函數,則建議使用**typedef**聲明函數指標類型的別名。  例如：

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
[內聯函數](../cpp/inline-functions-cpp.md)
