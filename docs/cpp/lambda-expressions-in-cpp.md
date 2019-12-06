---
title: C++ 中的 Lambda 運算式
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: e206ea8d67bb333065bf43f7f9c2dc373a5a5258
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857485"
---
# <a name="lambda-expressions-in-c"></a>C++ 中的 Lambda 運算式

在 c + + 11 和更新版本中，lambda 運算式（通常稱為*lambda*）是一種便利的方式，可在叫用或將它當做引數傳遞至函式的位置定義匿名函式物件（*關閉*）。 Lambda 通常用來封裝要傳遞給演算法或非同步方法的數行程式碼。 本文定義什麼是 Lambda、Lambda 與其他程式設計技術的比較、描述 Lamdba 的優點並提供基本範例。

## <a name="related-topics"></a>相關主題

- [Lambda 運算式與函數物件的比較](lambda-expression-syntax.md)
- [使用 lambda 運算式](examples-of-lambda-expressions.md)
- [constexpr lambda 運算式](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Lambda 運算式的組件

ISO C++ 標準顯示將傳遞為 `std::sort()` 函式第三個引數的簡單 Lambda：

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

下圖顯示 Lambda 的組件：

![Lambda 運算式的結構化元素](../cpp/media/lambdaexpsyntax.png "Lambda 運算式的結構化項目")

1. *capture 子句*（在C++規格中也稱為*lambda introducer* ）。

1. *參數清單*選擇性. （也稱為*lambda*宣告子）

1. *可變規格*選擇性.

1. *例外狀況-規格*選擇性.

1. *尾端-傳回類型*選擇性.

1. *lambda 主體*。

### <a name="capture-clause"></a>擷取子句

Lambda 可以在其主體中引進新的變數（在**c + + 14**中），而且它也可以從周圍的範圍存取或*捕捉*變數。 Lambda 的開頭是 capture 子句（標準語法中的*lambda-introducer* ），它會指定要捕捉的變數，以及捕捉是以傳值或傳址方式。 含有 `&` 前置詞的變數會以傳址方式來存取，而不含 &amp; 前置詞的變數會以傳值方式來存取。

空白的擷取子句 `[ ]` 表示 Lambda 運算式主體不存取封閉範圍中的任何變數。

您可以使用預設的「捕捉」模式（標準語法中的「*捕捉-預設值*」）來指示如何捕捉 lambda 中所參考的任何外部變數： `[&]` 表示您參考的所有變數都是以傳址方式來捕捉，而 `[=]` 表示它們是以傳值方式來捕捉。 您可以使用預設擷取模式，然後明確指定特定變數的相反模式。 例如，如果 Lambda 主體以傳址方式存取外部變數 `total`，並以傳值方式存取外部變數 `factor`，則下列擷取子句相等：

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

使用 capture-default 時，只會捕捉 lambda 中提到的變數。

如果 capture 子句包含 capture-default `&`，則該 capture 子句 `capture` 中的任何 `identifier` 都不能有 `& identifier`的格式。 同樣地，如果 capture 子句包含 capture-default `=`，則該 capture 子句的 `capture` 不會有 `= identifier`的形式。 識別碼**或在**capture 子句中不能出現一次以上。 下列程式碼片段說明部分範例。

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

後面接著省略號的 capture 就是套件擴充，如下列[variadic 範本](../cpp/ellipses-and-variadic-templates.md)範例所示：

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

若要在類別方法的主體中使用 lambda 運算式，請將**this**指標傳遞至 capture 子句，以提供對封入類別之方法和資料成員的存取。

**Visual Studio 2017 15.3 和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：藉由在 capture 子句中指定 `*this`，可以藉由值來捕捉**此**指標。 [以值方式捕捉] 表示整個*關閉*（也就是 encapulates lambda 運算式的匿名函式物件）會複製到叫用 lambda 的每一個呼叫位置。 當 lambda 將以平行或非同步作業的方式執行時，Capture 會很有用，特別是在某些硬體架構（例如 NUMA）上。

如需示範如何使用 lambda 運算式搭配類別方法的範例，請參閱[Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)中的「範例：在方法中使用 lambda 運算式」。

使用擷取子句時，建議您記住這幾個重點，特別是同時使用 Lambda 與多執行緒時：

- 傳址擷取可用來修改外部變數，但傳值擷取方式不能。 （**可**變動的是要修改的複本，而不是原始的副本）。

- 傳址擷取方式會反映對外部變數的更新，但傳值擷取方式不會。

- 傳址擷取方式採用存留期相依性，但傳值擷取方式沒有存留期相依性。 非同步執行 Lambda 時，這點特別重要。 如果您在非同步 Lambda 中以傳址方式擷取區域變數，該區域變數極可能會在 Lambda 執行之前消失，導致在執行階段存取違規。

### <a name="generalized-capture-c-14"></a>一般化擷取 (C++ 14)

在 C++14，您可以在擷取子句中引進並初始化新的變數，而這些變數不需要存在於 Lambda 函式的封閉範圍中。 初始化可以表示為任何任意運算式；新變數的類型是透過運算式所產生的類型推斷而來。 這項功能的其中一個優點是在 C++14 中，您可以從周圍範圍擷取僅移動變數 (例如 std::unique_ptr) 並在 Lambda 中使用它們。

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>參數清單

除了擷取變數之外，Lambda 還可以接受輸入參數。 參數清單（標準語法中的*lambda*宣告子）是選擇性的，而且在大部分的方面類似于函式的參數清單。

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

在 **C++ 14**中，如果參數類型是泛型，您可以使用 auto 關鍵字做為類型規範。 這會告訴編譯器建立函式呼叫運算子做為樣板。 參數清單中的每個 auto 執行個體都相當於不同的類型參數。

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Lambda 運算式可接受另一個 Lambda 運算式當做其引數。 如需詳細資訊，請參閱[Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)主題中的「高階 Lambda 運算式」。

由於參數清單是選擇性的，因此如果您未將引數傳遞至 lambda 運算式，而且其 lambda 宣告子不包含*例外狀況規格*、*尾端傳回類型***或可**變動，則可以省略空括弧。

### <a name="mutable-specification"></a>可變動規格

一般來說，lambda 的函式呼叫運算子是依值 const，但使用可變動**的關鍵字會**取消此項。它不會產生可變動的資料成員。 可變動規格可讓 Lambda 運算式主體修改以傳值方式擷取的變數。 本文稍後的部分範例會示範**如何使用可變動的。**

### <a name="exception-specification"></a>例外狀況規格

您可以使用 `noexcept` 例外狀況規格，表示 Lambda 運算式不會擲回任何例外狀況。 如同一般函式，如果 lambda C++運算式宣告 `noexcept` 例外狀況規格，而且 lambda 主體擲回例外狀況，則 Microsoft 編譯器會產生警告[C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) ，如下所示：

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

如需詳細資訊，請參閱[例外狀況規格（throw）](../cpp/exception-specifications-throw-cpp.md)。

### <a name="return-type"></a>傳回型別

Lambda 運算式的傳回型別會自動推算出來。 除非您指定*尾端傳回類型*，否則不需要使用[auto](../cpp/auto-cpp.md)關鍵字。 *尾端*傳回型別與一般方法或函式的傳回型別部分類似。 不過，傳回型別必須接在參數清單後面，而且您必須在傳回型別前面包含 trailing-return-type 關鍵字 `->`。

如果 Lambda 主體包含單一 return 陳述式，或者運算式不會傳回值，您可以省略 Lambda 運算式的傳回類型部分。 如果 Lambda 主體包含單一 return 陳述式，編譯器會從傳回運算式的類型推算傳回型別。 否則，編譯器會會推算傳回型別為**void**。 請考慮下列說明此原則的範例程式碼片段。

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Lambda 運算式可能會產生另一個 Lambda 運算式當做其傳回值。 如需詳細資訊，請參閱[Lambda 運算式的範例中的](../cpp/examples-of-lambda-expressions.md)「高階 Lambda 運算式」。

### <a name="lambda-body"></a>Lambda 主體

Lambda 運算式的 lambda 主體（標準語法中的*複合陳述式*）可以包含一般方法或函式主體可包含的任何內容。 一般函式和 Lambda 運算式的主體都可以存取下列類型的變數：

- 擷取自封閉範圍的變數 (如先前所述)。

- 參數

- 區域宣告變數

- 類別資料成員（在類別內部**宣告並加以**捕捉）

- 有靜態儲存期的任何變數 (例如，全域變數)

下列範例包含 Lambda 運算式，這個運算式會以傳值方式明確擷取變數 `n`，並以傳址方式隱含擷取變數 `m`：

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

因為變數 `n` 是以傳值方式擷取，其值在 Lambda 運算式呼叫之後會保持為 `0`。 **可變**的規格允許在 lambda 內修改 `n`。

雖然 Lambda 運算式只能擷取有自動儲存期的變數，但是您可以在 Lambda 運算式的主體中使用有靜態儲存期的變數。 下列範例使用 `generate` 函式和 Lambda 運算式，將值指派給 `vector` 物件的每個項目。 Lambda 運算式會修改這個靜態變數以產生下一個項目的值。

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

如需詳細資訊，請參閱[產生](../standard-library/algorithm-functions.md#generate)。

下列程式碼範例會使用上一個範例中的函式，並加入使用C++標準程式庫演算法 `generate_n`的 lambda 運算式範例。 此 Lambda 運算式會將 `vector` 物件的元素指派給前兩個元素的總和。 使用可變動**的關鍵字，** 讓 lambda 運算式的主體可以修改其外部變數的複本 `x` 和 `y`，而 lambda 運算式會以傳值方式來捕捉。 由於 Lambda 運算式會以傳值方式擷取原始變數 `x` 和 `y`，在 Lambda 執行後，它們的值仍然保持 `1`。

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

如需詳細資訊，請參閱[generate_n](../standard-library/algorithm-functions.md#generate_n)。

## <a name="constexpr-lambda-expressions"></a>constexpr Lambda 運算式

**Visual Studio 2017 15.3 版和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： lambda 運算式可以宣告為 `constexpr`，或在常數運算式中允許對其所捕捉或引進的每個資料成員進行初始化時，用於常數運算式中。

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

如果 lambda 的結果符合 `constexpr` 函數的需求，就會隱含地 `constexpr` 它：

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

如果 lambda 隱含或明確地 `constexpr`，轉換成函式指標會產生 `constexpr` 函數：

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Microsoft 專有

下列 common language runtime （CLR）受管理的實體不支援 lambda： **ref 類別**、 **ref 結構**、實**值類別**或**值結構**。

如果您使用的是 Microsoft 專有的修飾詞，例如[__declspec](../cpp/declspec.md)，您可以在 `parameter-declaration-clause`之後立即將它插入 lambda 運算式，例如：

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

若要判斷 lambda 是否支援修飾詞，請參閱檔中[Microsoft 專有](../cpp/microsoft-specific-modifiers.md)的修飾詞一節中的相關文章。

除了 c + + 11 標準 lambda 功能之外，Visual Studio 支援無狀態 lambda，其可全轉換為使用任意呼叫慣例的函式指標。

## <a name="see-also"></a>請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫的函式物件](../standard-library/function-objects-in-the-stl.md)<br/>
[函式呼叫](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
