---
title: :::no-loc(constexpr):::C + +
description: 'C + + 語言 :::no-loc(constexpr)::: 關鍵字指南。'
ms.date: 01/28/2020
f1_keywords:
- :::no-loc(constexpr):::_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- ':::no-loc(constexpr):::'
- ':::no-loc(const):::'
- ':::no-loc(inline):::'
- ':::no-loc(goto):::'
- ':::no-loc(try):::'
- ':::no-loc(if):::'
- ':::no-loc(switch):::'
- ':::no-loc(for):::'
- ':::no-loc(while):::'
ms.openlocfilehash: d66dc333b7ac9fba94221dc4efa723c7919ef88f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229021"
---
# <a name="no-locconstexpr-c"></a>:::no-loc(constexpr):::C + +

關鍵字 **`:::no-loc(constexpr):::`** 是在 c + + 11 中引進，並在 c + + 14 中改良。 這表示* :::no-loc(const)::: ant 運算式*。 就像一樣 **`:::no-loc(const):::`** ，它可以套用至變數：當任何程式碼嘗試 mod y 值時，就會引發編譯器錯誤 :::no-loc(if)::: 。 不同 **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** 于，也可以套用至函式和類別 :::no-loc(const)::: ructors。 **`:::no-loc(constexpr):::`** 表示值（或傳回值）是 ant，而在可能的情況 :::no-loc(const)::: 下，會在編譯時期計算。

在 **`:::no-loc(constexpr):::`** 需要整數的任何地方 :::no-loc(const)::: ，例如樣板引數和陣列宣告中，都可以使用整數值。 而在編譯時期（而非執行時間）計算值時，它可協助您的程式執行速度更快，並使用較少的記憶體。

為了限制編譯時間 ant 計算的複雜性 :::no-loc(const)::: ，以及其對編譯時間的潛在影響，c + + 14 標準要求 ant 運算式中的類型 :::no-loc(const)::: 必須是[常數值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>語法

> **`:::no-loc(constexpr):::`***常數值型別* *ident :::no-loc(if)::: ier* **=** * :::no-loc(const)::: ant 運算式* **;**\
> **`:::no-loc(constexpr):::`***常數值型別* *ident :::no-loc(if)::: ier* **{** * :::no-loc(const)::: ant-expression* **}** **;**\
> **`:::no-loc(constexpr):::`***常數值型別* *ident :::no-loc(if)::: ier* **（** *params* **）** **;**\
> **`:::no-loc(constexpr):::`***ctor* **（** *params* **）** **;**

## <a name="parameters"></a>參數

*化*\
一或多個參數，每個都必須是常數值型別，而且本身必須是 :::no-loc(const)::: ant 運算式。

## <a name="return-value"></a>傳回值

**`:::no-loc(constexpr):::`** 變數或函數必須傳回常值[類型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="no-locconstexpr-variables"></a>:::no-loc(constexpr)::: 變數

:::no-loc(if):::和變數之間的主要 d ference **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** 是 **`:::no-loc(const):::`** 可以延遲到執行時間才初始化變數。 **`:::no-loc(constexpr):::`** 變數必須在編譯時期初始化。  所有 **`:::no-loc(constexpr):::`** 變數都是 **`:::no-loc(const):::`** 。

- **`:::no-loc(constexpr):::`** 當變數具有常數值型別且已初始化時，可以使用來宣告變數。 如果初始化是 :::no-loc(for)::: 由 ructor 每個 med-v 進行 :::no-loc(const)::: ，則 :::no-loc(const)::: ructor 必須宣告為 **`:::no-loc(constexpr):::`** 。

- 參考可以宣告為 **`:::no-loc(constexpr):::`** 同時符合這兩個條件時：所參考的物件是由 :::no-loc(const)::: ant 運算式初始化，而且在初始化期間叫用的任何隱含轉換也都是 :::no-loc(const)::: ant 運算式。

- 變數或函數的所有宣告都 **`:::no-loc(constexpr):::`** 必須有 **`:::no-loc(constexpr):::`** 規格 :::no-loc(if)::: ier。

```cpp
:::no-loc(constexpr)::: float x = 42.0;
:::no-loc(constexpr)::: float y{108};
:::no-loc(constexpr)::: float z = exp(5, 3);
:::no-loc(constexpr)::: int i; // Error! Not initialized
int j = 0;
:::no-loc(constexpr)::: int k = j + 1; //Error! j not a :::no-loc(const):::ant expression
```

## <a name="no-locconstexpr-functions"></a><a name=":::no-loc(constexpr):::_functions"></a>:::no-loc(constexpr):::函數

函式 **`:::no-loc(constexpr):::`** 是在使用程式碼需要時，其傳回值會在編譯時期可的函式。 使用程式碼需要在編譯時期傳回值以初始化 **`:::no-loc(constexpr):::`** 變數，或提供非類型樣板引數。 當其引數為 **`:::no-loc(constexpr):::`** 值時， **`:::no-loc(constexpr):::`** 函數會產生編譯時期 :::no-loc(const)::: ant。 以非 **`:::no-loc(constexpr):::`** 引數呼叫時，或在編譯時期不需要其值時，它會在執行時間產生值，就像一般函數一樣。 （這種雙重行為可讓您不必撰寫 **`:::no-loc(constexpr):::`** 相同功能的和非 **`:::no-loc(constexpr):::`** 版本）。

**`:::no-loc(constexpr):::`** 函數或 :::no-loc(const)::: ructor 是隱含的 **`:::no-loc(inline):::`** 。

下列規則適用于函式 :::no-loc(constexpr)::: ：

- 函式 **`:::no-loc(constexpr):::`** 必須接受並只傳回[常數值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

- **`:::no-loc(constexpr):::`** 函數可以是遞迴的。

- 它不能是[虛擬](../cpp/virtual-cpp.md)的。 :::no-loc(const)::: **`:::no-loc(constexpr):::`** 當封閉式類別具有任何虛擬基類時，無法定義 ructor。

- 主體可以定義為 `= default` 或 `= delete`。

- 主體可以不包含任何 **`:::no-loc(goto):::`** 語句或 **`:::no-loc(try):::`** 區塊。

- 非範本的明確特製化 **`:::no-loc(constexpr):::`** 可以宣告為 **`:::no-loc(constexpr):::`** ：

- 範本的明確特製化 **`:::no-loc(constexpr):::`** 也不一定是 **`:::no-loc(constexpr):::`** ：

下列規則適用于 **`:::no-loc(constexpr):::`** Visual Studio 2017 和更新版本中的函式：

- 它可能包含 **`:::no-loc(if):::`** 和 **`:::no-loc(switch):::`** 語句，以及所有迴圈語句，包括 **`:::no-loc(for):::`** 、以範圍為基礎的 **`:::no-loc(for):::`** 、 **`:::no-loc(while):::`** 和**do- :::no-loc(while)::: **。

- 它可能包含區域變數宣告，但必須初始化變數。 它必須是常數值型別，而且不能是 **`static`** 或執行緒區域。 本機宣告的變數不一定要是 **`:::no-loc(const):::`** ，而且可能會變動。

- **`:::no-loc(constexpr):::`** 非成員函 **`static`** 式不需要隱含地進行 **`:::no-loc(const):::`** 。

```cpp
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 在 Visual Studio 偵錯工具中，當您在偵測到未優化的 Debug 組建時，您可以藉由在其中放置中斷點，來判斷函式是否 **`:::no-loc(constexpr):::`** 在編譯時期進行評估。 如果叫用中斷點，便已在執行階段呼叫此函式。  否則便是在編譯時期呼叫函式。

## <a name="extern-no-locconstexpr"></a>extern:::no-loc(constexpr):::

[/Zc： externConstexpr](../build/reference/zc-extern:::no-loc(constexpr):::.md)編譯器選項會使編譯器將[外部連結](../c-language/external-linkage.md)套用至使用**extern :::no-loc(constexpr)::: **所宣告的變數。 在舊版的 Visual Studio 中，根據預設，或當 **/zc： externConstexpr-** is 規格 :::no-loc(if)::: ied 時，Visual Studio 會套用內部連結至 **`:::no-loc(constexpr):::`** 變數，即使使用關鍵字時也一樣 **`extern`** 。 從 Visual Studio 2017 更新15.6 開始提供 **/zc： externConstexpr**選項，預設為關閉。 [/Permissive-](../build/reference/permissive-standards-con:::no-loc(for):::mance.md)選項不會啟用 **/zc： externConstexpr**。

## <a name="example"></a>範例

下列範例會顯示 **`:::no-loc(constexpr):::`** 變數、函式和使用者定義型別。 在中的最後一個語句中 `main()` ， **`:::no-loc(constexpr):::`** 成員函 `GetValue()` 式是執行時間呼叫，因為在編譯時期不需要知道此值。

```cpp
// :::no-loc(constexpr):::.cpp
// Compile with: cl /EHsc /W4 :::no-loc(constexpr):::.cpp
#include <iostream>

using namespace std;

// Pass by value
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
:::no-loc(constexpr)::: float exp2(:::no-loc(const)::: float& x, :::no-loc(const)::: int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
:::no-loc(constexpr)::: int length(:::no-loc(const)::: T(&)[N])
{
    return N;
}

// Recursive :::no-loc(constexpr)::: function
:::no-loc(constexpr)::: int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    :::no-loc(constexpr)::: explicit Foo(int i) : _i(i) {}
    :::no-loc(constexpr)::: int GetValue() :::no-loc(const):::
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is :::no-loc(const)::::
    :::no-loc(constexpr)::: Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    :::no-loc(constexpr)::: float x = exp(5, 3);
    :::no-loc(constexpr)::: float y { exp(2, 5) };
    :::no-loc(constexpr)::: int val = foo.GetValue();
    :::no-loc(constexpr)::: int f5 = fac(5);
    :::no-loc(const)::: int nums[] { 1, 2, 3, 4 };
    :::no-loc(const)::: int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>需求

Visual Studio 2015 或更新版本。

## <a name="see-also"></a>另請參閱

[宣告和定義](../cpp/declarations-and-definitions-cpp.md)\
[:::no-loc(const):::](../cpp/:::no-loc(const):::-cpp.md)
