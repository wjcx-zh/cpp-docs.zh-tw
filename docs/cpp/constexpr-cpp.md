---
title: 'constexpr (C + +) '
description: C + + 語言 constexpr 關鍵字指南。
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 57ebf4bf69c768bfcd2e4d26a5c3334ca788b08f
ms.sourcegitcommit: a6b97f5d78299ad93675de2fe0f0561f528d26c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90569554"
---
# <a name="no-locconstexpr-c"></a>constexpr (C + +) 

關鍵字 **`constexpr`** 是在 c + + 11 中引進，並在 c + + 14 中改善。 這表示* const ant 運算式*。 就像 **`const`** ，它可以套用至變數：當任何程式碼嘗試 mod y 值時，就會引發編譯器錯誤 if 。 不同 **`const`** **`constexpr`** 于，也可以套用至函式和類別 const ructors。 **`constexpr`** 表示值或傳回值為 const ant，而且可能的話，會在編譯時期計算。

**`constexpr`** 整數值可以在需要整數的任何地方使用 const ，例如在樣板引數和陣列宣告中。 而且，在編譯時期而不是執行時間計算值時，它可協助您的程式執行速度更快且使用較少的記憶體。

為了限制編譯時期 ant 計算的複雜度 const ，以及其對編譯時間的潛在影響，c + + 14 標準要求 ant 運算式中的類型 const 必須是 [常數值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>語法

> **`constexpr`***常數值型別* *ident if ier* **=** * const ant 運算式* **;**\
> **`constexpr`***常數值型別* *ident if ier* **{** * const ant-expression* **}** **;**\
> **`constexpr`***常數值型別* *ident if ier* ** (** *參數* **) ** **;**\
> **`constexpr`***ctor* ** (** *參數* **) ** **;**

## <a name="parameters"></a>參數

*Params*\
一個或多個參數，每個參數都必須是常數值型別，而且本身必須是 const ant 運算式。

## <a name="return-value"></a>傳回值

**`constexpr`** 變數或函數必須傳回常值[類型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="no-locconstexpr-variables"></a>constexpr 變數

if和變數之間的主要 d ference **`const`** **`constexpr`** 是 **`const`** 可以延後到執行時間的變數初始化。 **`constexpr`** 變數必須在編譯時期初始化。  所有 **`constexpr`** 變數都是 **`const`** 。

- **`constexpr`** 當變數具有常值型別且已初始化時，可使用宣告。 如果是 ructor 中的每個 for med-v 初始化 const ，則 const ructor 必須宣告為 **`constexpr`** 。

- **`constexpr`** 當符合這兩個條件時，可以宣告參考：參考的物件是由 const ant 運算式初始化，而在初始化期間叫用的任何隱含轉換也都是 const ant 運算式。

- 變數或函式的所有宣告都 **`constexpr`** 必須有 **`constexpr`** 規格 if ier。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="no-locconstexpr-functions"></a><a name="constexpr_functions"></a>constexpr函數

函式 **`constexpr`** 是一種函式，其傳回值會在使用程式碼需要時于編譯時期可計算。 使用程式碼需要在編譯時傳回值來初始化 **`constexpr`** 變數，或是提供非類型樣板引數。 當其引數為 **`constexpr`** 值時，函式會 **`constexpr`** 產生編譯時期 const ant。 使用非 **`constexpr`** 引數呼叫，或在編譯時期不需要其值時，它會在執行時間產生值，就像一般函數一樣。  (這個雙重行為可讓您不需要撰寫 **`constexpr`** 相同函式 **`constexpr`** 的和非版本。 ) 

**`constexpr`** 函數或 const ructor 是隱含的 **`inline`** 。

下列規則適用于 constexpr 函數：

- **`constexpr`** 函數必須接受並只傳回[常數值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

- **`constexpr`** 函數可以是遞迴的。

- 它不能是 [虛擬](../cpp/virtual-cpp.md)的。 當封入 const **`constexpr`** 類別具有任何虛擬基類時，無法定義 ructor。

- 主體可以定義為 `= default` 或 `= delete`。

- 主體可以不包含任何 **`goto`** 語句或 **`try`** 區塊。

- 非範本的明確特製化 **`constexpr`** 可以宣告為 **`constexpr`** ：

- 範本的明確特製化 **`constexpr`** 也不一定要 **`constexpr`** ：

下列規則適用于 **`constexpr`** Visual Studio 2017 和更新版本中的函數：

- 它可能包含 **`if`** 和 **`switch`** 語句，以及所有迴圈語句，包括 **`for`** 、以範圍為基礎的 **`for`** 、 **`while`** 和** while 等**。

- 它可能包含區域變數宣告，但變數必須初始化。 它必須是常數值型別，而且不能是 **`static`** 或執行緒區域。 本機宣告的變數不一定要是 **`const`** ，而且可能會改變。

- **`constexpr`** 非成員函 **`static`** 式不需要隱含 **`const`** 。

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}
```

> [!TIP]
> 在 Visual Studio 偵錯工具中，當您在偵錯工具中偵測到未優化的偵錯工具時，您可以藉 **`constexpr`** 由將中斷點放在編譯時期，判斷是否正在評估函式。 如果叫用中斷點，便已在執行階段呼叫此函式。  否則便是在編譯時期呼叫函式。

## <a name="extern-no-locconstexpr"></a>Extern constexpr

[/Zc： externConstexpr](../build/reference/zc-externconstexpr.md)編譯器選項會導致編譯器將[外部連結](../c-language/external-linkage.md)套用至使用**extern constexpr **宣告的變數。 在舊版 Visual Studio （預設值）或 **/zc： externConstexpr-** 為 spec ied 時， if Visual Studio 會將內部連結套用至 **`constexpr`** 變數（即使 **`extern`** 使用關鍵字）。 您可以從 Visual Studio 2017 更新15.6 開始取得 **/zc： externConstexpr** 選項，而且預設為關閉。 [/Permissive-](../build/reference/permissive-standards-conformance.md)選項不會啟用 **/zc： externConstexpr**。

## <a name="example"></a>範例

下列範例顯示 **`constexpr`** 變數、函式和使用者定義型別。 在的最後一個語句中 `main()` ， **`constexpr`** 成員函 `GetValue()` 式是執行時間呼叫，因為在編譯時期不需要知道此值。

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
}

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>需求

Visual Studio 2015 或更新版本。

## <a name="see-also"></a>另請參閱

[宣告和定義](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
