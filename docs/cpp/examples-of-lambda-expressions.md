---
title: Lambda 運算式的範例
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
ms.openlocfilehash: 585e76119b0e848e322c88ad0149ebb42c6b5b1d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221597"
---
# <a name="examples-of-lambda-expressions"></a>Lambda 運算式的範例

本文說明如何在您的程式中使用 Lambda 運算式。 如需 lambda 運算式的總覽，請參閱[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。 如需 lambda 運算式結構的詳細資訊，請參閱[Lambda 運算式語法](../cpp/lambda-expression-syntax.md)。

## <a name="declaring-lambda-expressions"></a><a name="declaringLambdaExpressions"></a>宣告 Lambda 運算式

### <a name="example-1"></a>範例 1

因為 lambda 運算式具有類型，所以您可以將它指派給 **`auto`** 變數或 [`function`](../standard-library/function-class.md) 物件，如下所示：

### <a name="code"></a>程式碼

```cpp
// declaring_lambda_expressions1.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{

    using namespace std;

    // Assign the lambda expression that adds two numbers to an auto variable.
    auto f1 = [](int x, int y) { return x + y; };

    cout << f1(2, 3) << endl;

    // Assign the same lambda expression to a function object.
    function<int(int, int)> f2 = [](int x, int y) { return x + y; };

    cout << f2(3, 4) << endl;
}
```

### <a name="output"></a>輸出

```Output
5
7
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [`auto`](../cpp/auto-cpp.md) 、 [ `function` 類別](../standard-library/function-class.md)和[函式呼叫](../cpp/function-call-cpp.md)。

雖然 Lambda 運算式最常在函式的主體中宣告，但您也可以在可初始化變數的任何位置宣告 Lambda 運算式。

### <a name="example-2"></a>範例 2

當宣告運算式時，Microsoft c + + 編譯器會將 lambda 運算式系結至其已捕捉的變數，而不是呼叫運算式時。 下列範例示範 Lambda 運算式以傳值方式擷取區域變數 `i`，以及以傳址方式擷取區域變數 `j`： 因為 Lambda 運算式是以傳值方式擷取 `i` 的值，因此之後在程式中重新指派 `i` 的值並不會影響運算式的結果。 不過，因為 Lambda 運算式是以傳址方式擷取 `j` 的值，因此之後重新指派 `j` 的值會影響運算式的結果。

### <a name="code"></a>程式碼

```cpp
// declaring_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   int i = 3;
   int j = 5;

   // The following lambda expression captures i by value and
   // j by reference.
   function<int (void)> f = [i, &j] { return i + j; };

   // Change the values of i and j.
   i = 22;
   j = 44;

   // Call f and print its result.
   cout << f() << endl;
}
```

### <a name="output"></a>輸出

```Output
47
```

[[在本文中](#top)]

## <a name="calling-lambda-expressions"></a><a name="callingLambdaExpressions"></a>呼叫 Lambda 運算式

如下程式碼片段所示，您可以立即呼叫 Lambda 運算式。 第二個程式碼片段顯示如何將 lambda 當做引數傳遞至 c + + 標準程式庫演算法，例如 `find_if` 。

### <a name="example-1"></a>範例 1

此範例會宣告一個 Lambda 運算式，此運算式會傳回兩個整數相加的總和並立即以引數 `5` 和 `4` 呼叫運算式：

### <a name="code"></a>程式碼

```cpp
// calling_lambda_expressions1.cpp
// compile with: /EHsc
#include <iostream>

int main()
{
   using namespace std;
   int n = [] (int x, int y) { return x + y; }(5, 4);
   cout << n << endl;
}
```

### <a name="output"></a>輸出

```Output
9
```

### <a name="example-2"></a>範例 2

此範例將 Lambda 運算式當做引數傳遞至 `find_if` 函式。 如果 lambda 運算式的 **`true`** 參數是偶數，則會傳回此值。

### <a name="code"></a>程式碼

```cpp
// calling_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    // Create a list of integers with a few initial elements.
    list<int> numbers;
    numbers.push_back(13);
    numbers.push_back(17);
    numbers.push_back(42);
    numbers.push_back(46);
    numbers.push_back(99);

    // Use the find_if function and a lambda expression to find the
    // first even number in the list.
    const list<int>::const_iterator result =
        find_if(numbers.begin(), numbers.end(),[](int n) { return (n % 2) == 0; });

    // Print the result.
    if (result != numbers.end()) {
        cout << "The first even number in the list is " << *result << "." << endl;
    } else {
        cout << "The list contains no even numbers." << endl;
    }
}
```

### <a name="output"></a>輸出

```Output
The first even number in the list is 42.
```

### <a name="remarks"></a>備註

如需函式的詳細資訊 `find_if` ，請參閱 [`find_if`](../standard-library/algorithm-functions.md#find_if) 。 如需執行一般演算法之 c + + 標準程式庫函式的詳細資訊，請參閱 [`<algorithm>`](../standard-library/algorithm.md) 。

[[在本文中](#top)]

## <a name="nesting-lambda-expressions"></a><a name="nestingLambdaExpressions"></a>嵌套 Lambda 運算式

### <a name="example"></a>範例

如本範例所示，您可以在 Lambda 運算式中與另一個 Lambda 運算式形成巢狀。 內部的 Lambda 運算式會將其引數乘以 2 並傳回結果。 外部的 Lambda 運算式會以內部 Lambda 運算式的引數呼叫該運算式並將結果加上 3。

### <a name="code"></a>程式碼

```cpp
// nesting_lambda_expressions.cpp
// compile with: /EHsc /W4
#include <iostream>

int main()
{
    using namespace std;

    // The following lambda expression contains a nested lambda
    // expression.
    int timestwoplusthree = [](int x) { return [](int y) { return y * 2; }(x) + 3; }(5);

    // Print the result.
    cout << timestwoplusthree << endl;
}
```

### <a name="output"></a>輸出

```Output
13
```

### <a name="remarks"></a>備註

在此範例中，`[](int y) { return y * 2; }` 是巢狀 Lambda 運算式。

[[在本文中](#top)]

## <a name="higher-order-lambda-functions"></a><a name="higherOrderLambdaExpressions"></a>高階 Lambda 函數

### <a name="example"></a>範例

許多程式設計語言都支援*更高順序函式*的概念。 高階函式是以另一個 Lambda 運算式為其引數或傳回 Lambda 運算式的 Lambda 運算式。 您可以使用 [`function`](../standard-library/function-class.md) 類別，讓 c + + lambda 運算式的行為類似于高階函數。 下列範例說明傳回 `function` 物件的 Lambd 運算式，以及使用 `function` 物件做為其引數的 Lambda 運算式。

### <a name="code"></a>程式碼

```cpp
// higher_order_lambda_expression.cpp
// compile with: /EHsc /W4
#include <iostream>
#include <functional>

int main()
{
    using namespace std;

    // The following code declares a lambda expression that returns
    // another lambda expression that adds two numbers.
    // The returned lambda expression captures parameter x by value.
    auto addtwointegers = [](int x) -> function<int(int)> {
        return [=](int y) { return x + y; };
    };

    // The following code declares a lambda expression that takes another
    // lambda expression as its argument.
    // The lambda expression applies the argument z to the function f
    // and multiplies by 2.
    auto higherorder = [](const function<int(int)>& f, int z) {
        return f(z) * 2;
    };

    // Call the lambda expression that is bound to higherorder.
    auto answer = higherorder(addtwointegers(7), 8);

    // Print the result, which is (7+8)*2.
    cout << answer << endl;
}
```

### <a name="output"></a>輸出

```Output
30
```

[[在本文中](#top)]

## <a name="using-a-lambda-expression-in-a-function"></a><a name="methodLambdaExpressions"></a>在函式中使用 Lambda 運算式

### <a name="example"></a>範例

您可以在函式的主體中使用 Lambda 運算式。 Lambda 運算式可以存取封入函式能夠存取的任何函式或資料成員。 您可以明確或隱含地捕捉 **`this`** 指標，以提供封入類別之函式和資料成員的存取權。
**Visual Studio 2017 15.3 版和更新**版本（適用于 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ）： **`this`** `[*this]` 當 lambda 將用於非同步或並行作業，而該程式碼可能會在原始物件超出範圍之後執行時，以值 Capture （）。

您可以 **`this`** 在函式中明確使用指標，如下所示：

```cpp
// capture "this" by reference
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [this](int n) { cout << n * _scale << endl; });
}

// capture "this" by value (Visual Studio 2017 version 15.3 and later)
void ApplyScale2(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [*this](int n) { cout << n * _scale << endl; });
}
```

您也可以 **`this`** 隱含地捕捉指標：

```cpp
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [=](int n) { cout << n * _scale << endl; });
}
```

下列範例示範封裝小數位數值的 `Scale` 類別。

```cpp
// function_lambda_expression.cpp
// compile with: /EHsc /W4
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

class Scale
{
public:
    // The constructor.
    explicit Scale(int scale) : _scale(scale) {}

    // Prints the product of each element in a vector object
    // and the scale value to the console.
    void ApplyScale(const vector<int>& v) const
    {
        for_each(v.begin(), v.end(), [=](int n) { cout << n * _scale << endl; });
    }

private:
    int _scale;
};

int main()
{
    vector<int> values;
    values.push_back(1);
    values.push_back(2);
    values.push_back(3);
    values.push_back(4);

    // Create a Scale object that scales elements by 3 and apply
    // it to the vector object. Does not modify the vector.
    Scale s(3);
    s.ApplyScale(values);
}
```

### <a name="output"></a>輸出

```Output
3
6
9
12
```

### <a name="remarks"></a>備註

`ApplyScale` 函式使用 Lambda 運算式列印小數位數值和 `vector` 物件中每個元素的乘積。 Lambda 運算式會隱含地捕捉， **`this`** 讓它可以存取 `_scale` 成員。

[[在本文中](#top)]

## <a name="using-lambda-expressions-with-templates"></a><a name="templateLambdaExpressions"></a>搭配範本使用 Lambda 運算式

### <a name="example"></a>範例

因為 Lambda 運算式具有類型，因此您可以搭配 C++ 範本使用。 下列範例顯示 `negate_all` 和 `print_all` 函式。 函式會 `negate_all` 將一元套用 **`operator-`** 至物件中的每個元素 `vector` 。 `print_all` 函式會將 `vector` 物件中的每個元素印出至主控台。

### <a name="code"></a>程式碼

```cpp
// template_lambda_expression.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

// Negates each element in the vector object. Assumes signed data type.
template <typename T>
void negate_all(vector<T>& v)
{
    for_each(v.begin(), v.end(), [](T& n) { n = -n; });
}

// Prints to the console each element in the vector object.
template <typename T>
void print_all(const vector<T>& v)
{
    for_each(v.begin(), v.end(), [](const T& n) { cout << n << endl; });
}

int main()
{
    // Create a vector of signed integers with a few elements.
    vector<int> v;
    v.push_back(34);
    v.push_back(-43);
    v.push_back(56);

    print_all(v);
    negate_all(v);
    cout << "After negate_all():" << endl;
    print_all(v);
}
```

### <a name="output"></a>輸出

```Output
34
-43
56
After negate_all():
-34
43
-56
```

### <a name="remarks"></a>備註

如需 c + + 範本的詳細資訊，請參閱[範本](../cpp/templates-cpp.md)。

[[在本文中](#top)]

## <a name="handling-exceptions"></a><a name="ehLambdaExpressions"></a>處理例外狀況

### <a name="example"></a>範例

Lambda 運算式的主體遵循結構化例外狀況處理（SEH）和 C++ 例外狀況處理這兩種規則。 您可以處理在 Lambda 運算式主體中引發的例外狀況，也可以延後至封閉範圍再處理例外狀況。 下列範例會使用函式 **`for_each`** 和 lambda 運算式來填入 `vector` 具有另一個值的物件。 它會使用 **`try`** / **`catch`** 區塊來處理第一個向量的無效存取。

### <a name="code"></a>程式碼

```cpp
// eh_lambda_expression.cpp
// compile with: /EHsc /W4
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    // Create a vector that contains 3 elements.
    vector<int> elements(3);

    // Create another vector that contains index values.
    vector<int> indices(3);
    indices[0] = 0;
    indices[1] = -1; // This is not a valid subscript. It will trigger an exception.
    indices[2] = 2;

    // Use the values from the vector of index values to
    // fill the elements vector. This example uses a
    // try/catch block to handle invalid access to the
    // elements vector.
    try
    {
        for_each(indices.begin(), indices.end(), [&](int index) {
            elements.at(index) = index;
        });
    }
    catch (const out_of_range& e)
    {
        cerr << "Caught '" << e.what() << "'." << endl;
    };
}
```

### <a name="output"></a>輸出

```Output
Caught 'invalid vector<T> subscript'.
```

### <a name="remarks"></a>備註

如需例外狀況處理的詳細資訊，請參閱[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。

[[在本文中](#top)]

## <a name="using-lambda-expressions-with-managed-types-ccli"></a><a name="managedLambdaExpressions"></a>使用 Lambda 運算式搭配 Managed 類型（c + +/CLI）

### <a name="example"></a>範例

Lambda 運算式的擷取子句不能包含屬於 Managed 類型的變數。 不過，您可以將屬於 Managed 類型的引數傳遞至 Lambda 運算式的參數清單。 下列範例包含以傳值方式擷取區域 Unmanaged 變數 `ch` 並以 <xref:System.String?displayProperty=fullName> 物件做為其參數的 Lambda 運算式：

### <a name="code"></a>程式碼

```cpp
// managed_lambda_expression.cpp
// compile with: /clr
using namespace System;

int main()
{
    char ch = '!'; // a local unmanaged variable

    // The following lambda expression captures local variables
    // by value and takes a managed String object as its parameter.
    [=](String ^s) {
        Console::WriteLine(s + Convert::ToChar(ch));
    }("Hello");
}
```

### <a name="output"></a>輸出

```Output
Hello!
```

### <a name="remarks"></a>備註

您也可以使用 Lambda 運算式搭配 STL/CLR 程式庫。 如需詳細資訊，請參閱[STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)。

> [!IMPORTANT]
> 在這些 common language runtime （CLR）受管理的實體中不支援 lambda： **`ref class`** 、 **`ref struct`** 、 **`value class`** 和 **`value struct`** 。

[[在本文中](#top)]

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)<br/>
[Lambda 運算式語法](../cpp/lambda-expression-syntax.md)<br/>
[`auto`](../cpp/auto-cpp.md)<br/>
[`function`課堂](../standard-library/function-class.md)<br/>
[`find_if`](../standard-library/algorithm-functions.md#find_if)<br/>
[`<algorithm>`](../standard-library/algorithm.md)<br/>
[函式呼叫](../cpp/function-call-cpp.md)<br/>
[範本](../cpp/templates-cpp.md)<br/>
[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)<br/>
[STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)
