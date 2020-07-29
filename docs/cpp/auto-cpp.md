---
title: auto (C++)
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 675f6919b6804cfb1d2c5395d046cb5fa39e625d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229190"
---
# <a name="auto-c"></a>`auto`C + +

從所宣告變數的初始化運算式，來推斷其類型。

> [!NOTE]
> C + + 標準定義了這個關鍵字的原始和修訂的意義。 在 Visual Studio 2010 之前， **`auto`** 關鍵字會在*自動*儲存類別中宣告變數，也就是具有本機存留期的變數。 從 Visual Studio 2010 開始， **`auto`** 關鍵字會宣告一個變數，其型別是從其宣告中的初始化運算式推斷而來。 [ `/Zc:auto`&#91; &#93;](../build/reference/zc-auto-deduce-variable-type.md)編譯器選項控制關鍵字的意義 **`auto`** 。

## <a name="syntax"></a>語法

> **`auto`***declarator*宣告子*初始化運算式***`;`**

> **`[](auto`***param1* **`, auto`***param2***`) {};`**

## <a name="remarks"></a>備註

**`auto`** 關鍵字會指示編譯器使用宣告變數或 lambda 運算式參數的初始化運算式來推算其類型。

我們建議您在 **`auto`** 大部分情況下使用關鍵字，除非您真的想要轉換，因為它提供下列優點：

- **穩定性：** 如果運算式的型別已變更，這會包含函式傳回型別變更時的情況，這只是有效的。

- **效能：** 您保證不會進行任何轉換。

- **可用性：** 您不必擔心型別名稱的拼寫問題和打字錯誤。

- **效率：** 您的編碼可能更有效率。

您可能不想使用的轉換案例 **`auto`** ：

- 想要特定類型但不執行任何動作時。

- 運算式範本 helper 類型，例如 `(valarray+valarray)` 。

若要使用 **`auto`** 關鍵字，請使用它來取代類型，以宣告變數，並指定初始化運算式。 此外，您可以使用規範和宣告子 **`auto`** （例如 **`const`** 、 **`volatile`** 、指標（ **`*`** ）、reference （ **`&`** ）和右值參考（ **`&&`** ））來修改關鍵字。 編譯器會評估初始化運算式，然後使用該資訊來推斷變數類型。

初始化運算式可以是指派（等號語法）、直接初始化（函式樣式語法）、 [`operator new`](new-operator-cpp.md) 運算式，或初始化運算式可以是[範圍架構 `for` 語句（c + +）](../cpp/range-based-for-statement-cpp.md)語句中的*範圍*宣告參數。 如需詳細資訊，請參閱此檔稍後的[初始化運算式](../cpp/initializers.md)和程式碼範例。

**`auto`** 關鍵字是類型的預留位置，但它本身不是類型。 因此， **`auto`** 關鍵字不能用於轉型或運算子 [`sizeof`](../cpp/sizeof-operator.md) ，例如和（適用于 c + +/cli） [`typeid`](../extensions/typeid-cpp-component-extensions.md) 。

## <a name="usefulness"></a>實用性

**`auto`** 關鍵字是宣告具有複雜類型之變數的簡單方式。 例如，您可以使用宣告 **`auto`** 一個變數，其中初始化運算式牽涉到範本、函式的指標或成員的指標。

您也可以使用 **`auto`** 來宣告和初始化 lambda 運算式的變數。 您無法自行宣告變數類型，因為只有編譯器才知道 Lambda 運算式的類型。 如需詳細資訊，請參閱[Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)。

## <a name="trailing-return-types"></a>尾端傳回型別

您可以 **`auto`** 搭配類型規範使用， **`decltype`** 以協助撰寫範本庫。 使用 **`auto`** 和宣告樣板函式， **`decltype`** 其傳回類型取決於其樣板引數的類型。 或者，使用 **`auto`** 和 **`decltype`** 來宣告包裝呼叫另一個函式的範本函式，然後傳回該其他函式的傳回型別。 如需詳細資訊，請參閱 [`decltype`](../cpp/decltype-cpp.md)。

## <a name="references-and-cv-qualifiers"></a>參考和 cv 限定詞

請注意，使用會捨棄 **`auto`** 參考、 **`const`** 限定詞和 **`volatile`** 限定詞。 請考慮下列範例：

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

在上述範例中，myAuto 是 **`int`** ，而不是 **`int`** 參考，因此，如果未卸載參考辨識符號，則輸出會是 `11 11` ，而不是 `11 12` 這種情況 **`auto`** 。

## <a name="type-deduction-with-braced-initializers-c14"></a>使用括弧初始化運算式的類型推斷（c + + 14）

下列程式碼範例顯示如何 **`auto`** 使用大括弧初始化變數。 請注意 B 與 C 之間的差異，以及 A 和 E 之間的差異。

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

下表列出使用關鍵字的限制 **`auto`** ，以及編譯器發出的對應診斷錯誤訊息。

|錯誤號碼|說明|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**`auto`** 關鍵字無法與任何其他類型規範結合。|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|使用關鍵字宣告的符號 **`auto`** 必須有初始化運算式。|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|您不正確地使用 **`auto`** 關鍵字來宣告型別。 例如，您已宣告方法傳回類型或陣列。|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md)、 [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|參數或樣板引數不能以關鍵字宣告 **`auto`** 。|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|方法或樣板參數不能以 **`auto`** 關鍵字宣告。|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|符號無法在初始化之前使用。 實際上，這表示不能使用變數來初始化它自己。|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|您不能轉換成以關鍵字宣告的類型 **`auto`** 。|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|宣告子清單中以關鍵字宣告的所有符號，都 **`auto`** 必須解析成相同的類型。 如需詳細資訊，請參閱宣告[和定義](declarations-and-definitions-cpp.md)。|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md)、 [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md)和[typeid](../extensions/typeid-cpp-component-extensions.md)運算子不能套用至使用關鍵字所宣告的符號 **`auto`** 。|

## <a name="examples"></a>範例

這些程式碼片段說明 **`auto`** 關鍵字可以使用的一些方式。

下列宣告相同。 在第一個語句中，變數 `j` 會宣告為類型 **`int`** 。 在第二個語句中，變數 `k` 會推算為類型， **`int`** 因為初始化運算式（0）是整數。

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

下列宣告相同，但第二個宣告比第一個宣告簡單。 使用關鍵字的其中一個最具說服力的理由 **`auto`** 是簡單的。

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

下列程式碼片段會宣告變數的類型 `iter` ，以及 `elem` **`for`** 和範圍 **`for`** 迴圈開始時。

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

下列程式碼片段會使用 **`new`** 運算子和指標宣告來宣告指標。

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

下列程式碼片段會將變數初始化 `x` 為類型 **`int`** 、變數 `y` 為類型的參考 **`const int`** ，並將變數 `fp` **`int`** 初始化為傳回類型之函式的指標。

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>另請參閱

[`auto`關鍵字](../cpp/auto-keyword.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[`/Zc:auto`（推算變數類型）](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[`sizeof`操作](../cpp/sizeof-operator.md)<br/>
[`typeid`](../extensions/typeid-cpp-component-extensions.md)<br/>
[`operator new`](new-operator-cpp.md)<br/>
[宣告和定義](declarations-and-definitions-cpp.md)<br/>
[Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)<br/>
[初始設定式](../cpp/initializers.md)<br/>
[`decltype`](../cpp/decltype-cpp.md)
