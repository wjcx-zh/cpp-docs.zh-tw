---
title: 自動 （c + +）
ms.date: 11/04/2016
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 3d77a17d490f8d7680f095367c309ce0e4f366b7
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776332"
---
# <a name="auto-c"></a>自動 （c + +）

從所宣告變數的初始化運算式，來推斷其類型。

## <a name="syntax"></a>語法

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>備註

**自動**關鍵字會指示編譯器使用的宣告的變數或 lambda 運算式參數的初始化運算式來推算其類型。

我們建議您改用**自動**關鍵字用於大部分的情況 — 除非您確實要進行轉換，因為它提供下列優點：

- **強固性：** 如果運算式的類型變更，這包括函式的傳回類型變更時，它就會運作。

- **效能：** 您可以保證會有任何轉換。

- **可用性：** 您不必擔心類型名稱拼字困難和錯字。

- **效率：** 您的程式碼可能更有效率。

轉換情況下，您可能不想要使用**自動**:

- 想要特定類型但不執行任何動作時。

- 運算式樣板 helper 類型 — 比方說， `(valarray+valarray)`。

若要使用**自動**關鍵字，而不是類型可用來宣告一個變數，並指定初始化運算式。 此外，您可以在其中修改**自動**關鍵字，例如使用規範和宣告子**const**， **volatile**，指標 (`*`)，參考 (`&`)，和右值參考 (`&&`)。 編譯器會評估初始化運算式，然後使用該資訊來推斷變數類型。

初始化運算式可以是指派 （等號語法），直接初始化 （函式樣式語法）， [new 運算子](new-operator-cpp.md)運算式或初始化運算式可以是*範圍宣告*中的參數[範圍架構 for 陳述式 （c + +）](../cpp/range-based-for-statement-cpp.md)陳述式。 如需詳細資訊，請參閱 <<c0> [ 初始設定式](../cpp/initializers.md)和本文件稍後的程式碼範例。

**自動**關鍵字是類型的預留位置，但它本身不是型別。 因此，**自動**關鍵字不能在轉換或運算子這類[sizeof](../cpp/sizeof-operator.md)以及 (C + /cli CLI) [typeid](../extensions/typeid-cpp-component-extensions.md)。

## <a name="usefulness"></a>實用性

**自動**關鍵字是簡單的方式來宣告包含複雜的類型的變數。 例如，您可以使用**自動**宣告變數，其中初始化運算式包括樣板、 函式指標或成員的指標。

您也可以使用**自動**宣告並初始化 lambda 運算式的變數。 您無法自行宣告變數類型，因為只有編譯器才知道 Lambda 運算式的類型。 如需詳細資訊，請參閱 < [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)。

## <a name="trailing-return-types"></a>尾端傳回型別

您可以使用**自動**連同**decltype**類型規範，以協助撰寫樣板庫。 使用**自動**並**decltype**宣告樣板函式的傳回類型取決於樣板引數的類型。 或者，您也可以使用**自動**並**decltype**宣告樣板函式會包裝對其他函式，呼叫，然後傳回該其他函式的傳回型別。 如需詳細資訊，請參閱 < [decltype](../cpp/decltype-cpp.md)。

## <a name="references-and-cv-qualifiers"></a>參考和 cv 限定詞

請注意，使用**自動**卸除參考、 const 限定詞和 volatile 限定詞。 參考下列範例：

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}
```

在上述範例中，myAuto 是 int，不是 int 參考，因此輸出`11 11`，而非`11 12`，會發生這個狀況，如果尚未捨棄參考辨識符號**自動**。

## <a name="type-deduction-with-braced-initializers-c14"></a>使用括號初始設定式 (C + + 14) 的類型推斷

下列程式碼範例示範如何初始化自動變數使用大括號。 請注意 B 與 C 和 A 之間的差異和 e。

```cpp
#include <initializer_list>

int main()
{
    // std::initializer_list<int>
    auto A = { 1, 2 };

    // std::initializer_list<int>
    auto B = { 3 };

    // int
    auto C{ 4 };

    // C3535: cannot deduce type for 'auto' from initializer list'
    auto D = { 5, 6.7 };

    // C3518 in a direct-list-initialization context the type for 'auto'
    // can only be deduced from a single initializer expression
    auto E{ 8, 9 };

    return 0;
}
```

## <a name="restrictions-and-error-messages"></a>限制和錯誤訊息

下表列出使用的限制**自動**關鍵字，且編譯器會發出對應診斷錯誤訊息。

|錯誤代碼|描述|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**自動**關鍵字無法與任何其他類型規範結合。|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|以宣告的符號**自動**關鍵字必須有初始設定式。|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|您誤用**自動**關鍵字來宣告類型。 例如，您已宣告方法傳回類型或陣列。|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md)， [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|參數或樣板引數不能以宣告**自動**關鍵字。|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|方法或樣板參數不能以宣告**自動**關鍵字。|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|符號無法在初始化之前使用。 實際上，這表示不能使用變數來初始化它自己。|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|您無法轉換成使用宣告型別**自動**關鍵字。|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|以宣告的宣告子清單中的所有符號**自動**關鍵字必須解析為相同的型別。 如需詳細資訊，請參閱 <<c0> [ 宣告和定義](declarations-and-definitions-cpp.md)。|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md)並[typeid](../extensions/typeid-cpp-component-extensions.md)運算子不能套用至使用宣告的符號**自動**關鍵字。|

## <a name="examples"></a>範例

這些程式碼片段說明的方式的一些**自動**關鍵字可用。

下列宣告相同。 第一個陳述式中，變數`j`宣告為類型**int**。第二個陳述式中，變數`k`型別推算**int**因為初始化運算式 (0) 是一個整數。

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

下列宣告相同，但第二個宣告比第一個宣告簡單。 若要使用的最受矚目的原因之一**自動**關鍵字是簡單。

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

下列程式碼片段會宣告變數的類型`iter`並`elem`時**如**和範圍**的**迴圈開始。

```cpp
// cl /EHsc /nologo /W4
#include <deque>
using namespace std;

int main()
{
    deque<double> dqDoubleData(10, 0.1);

    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)
    { /* ... */ }

    // prefer range-for loops with the following information in mind
    // (this applies to any range-for with auto, not just deque)

    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples
    { /* ... */ }

    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE
    { /* ... */ }

    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE
    { /* ... */ }
}
```

下列程式碼片段會使用**新**運算子和指標宣告來宣告指標。

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

下一個程式碼片段會宣告每個宣告陳述式中的多個符號。 請注意，每個陳述式中的所有符號都會解析成相同類型。

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

此程式碼片段使用條件運算子 (`?:`) 將變數 `x` 宣告為值為 200 的整數：

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

下列程式碼片段會初始化變數`x`鍵入**int**、 變數`y`類型的參考來**const int**，和變數`fp`函式指標傳回型別**int**。

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto & y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../cpp/auto-keyword.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[/Zc:auto (推算變數類型)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 運算子](../cpp/sizeof-operator.md)<br/>
[typeid](../extensions/typeid-cpp-component-extensions.md)<br/>
[operator new](new-operator-cpp.md)<br/>
[宣告和定義](declarations-and-definitions-cpp.md)<br/>
[Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)<br/>
[初始設定式](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)
