---
title: constexpr (C++)
ms.date: 08/05/2019
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
ms.openlocfilehash: 5c98436f537b34b1c9050e057971938d48792db1
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821106"
---
# <a name="constexpr-c"></a>constexpr (C++)

關鍵字**constexpr**是在 c + + 11 中引進, 並在 c + + 14 中改良。 這表示*常數運算式*。 就像**const**一樣, 它可以套用至變數, 以便在任何程式碼嘗試修改值時引發編譯器錯誤。 不同于**const**, **constexpr**也可以套用至函式和類別的函式。 **constexpr**表示值 (或傳回值) 是常數, 而且可能的話, 會在編譯時期計算。

在需要 const 整數 (例如樣板引數和陣列宣告) 的任何地方, 都可以使用**constexpr**整數值。 而在編譯時期 (而非執行時間) 可以計算值時, 它可以協助您的程式執行速度更快, 並使用較少的記憶體。

為了限制編譯時間常數計算的複雜性, 以及其對編譯時間的潛在影響, c + + 14 標準要求常數運算式中的類型必須是[常數值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>語法

> **constexpr** *常值型別* *識別碼* **=** *常數運算式* **;** 
>  **constexpr** *常值型別* *識別碼* **{** *常數運算式* **}** **;** 
>  **constexpr** *常值型別* *識別碼* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>參數

*params*<br/>
一或多個參數, 每個都必須是常數值型別, 而且本身必須是常數運算式。

## <a name="return-value"></a>傳回值

Constexpr 變數或函數必須傳回常值[類型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="constexpr-variables"></a>constexpr 變數

Const 和 constexpr 變數的主要差異在於可以延遲到執行時間才初始化 const 變數。 Constexpr 變數必須在編譯時期初始化。  所有的 constexpr 變數都是常數。

- 如果變數具有常數值型別且已初始化, 則可以使用**constexpr**來宣告變數。 如果初始化是由「函式」執行, 則必須將此「函式」宣告為**constexpr**。

- 如果所參考的物件已由常數運算式初始化，而且在初始化期間叫用的任何隱含轉換也是常數運算式，則參考可以宣告為 constexpr。

- **Constexpr**變數或函數的所有宣告都必須具有**constexpr**規範。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>constexpr 函式

**Constexpr**函式是在使用程式碼需要時, 其傳回值可以在編譯時期計算的函式。 使用程式碼需要在編譯時期傳回值, 例如, 初始化**constexpr**變數或提供非類型樣板引數。 當其引數為**constexpr**值時, **constexpr**函數會產生編譯時間常數。 使用非**constexpr**引數呼叫時, 或在編譯時期不需要其值時, 會在執行時間產生值, 就像一般函數一樣。 (這種雙重行為可讓您不必撰寫相同函式的**constexpr**和非**constexpr**版本)。

**Constexpr**函數或函式會隱含地**內嵌**。

下列規則適用于 constexpr 函式:

- **Constexpr**函數必須接受並只傳回[常數值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

- **Constexpr**函數可以是遞迴的。

- 它不能是[虛擬](../cpp/virtual-cpp.md)的。 如果封入類別具有任何虛擬基類, 則無法將此函式定義為 constexpr。

- 主體可以定義為 `= default` 或 `= delete`。

- 主體不能包含**goto**語句或 try 區塊。

- 非 constexpr 範本的明確特製化可以宣告為**constexpr**:

- **Constexpr**範本的明確特製化也不需要也是**constexpr**:

下列規則適用于 Visual Studio 2017 和更新版本中的**constexpr**函式:

- 它可能包含**if**和**switch**語句, 以及所有迴圈語句, 包括**for**、範圍架構的 for、 **while**和**do while**。

- 它可能包含區域變數宣告, 但變數必須初始化、必須是常數值型別, 而且不能是靜態或執行緒區域。 本機宣告的變數不需要是 const, 而且可能會變動。

- Constexpr 非靜態成員函式不一定要以隱含方式 const。

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 在 Visual Studio 偵錯工具中, 當您在偵測到未優化的偵錯工具組建時, 您可以藉由在其中放置中斷點, 來判斷是否在編譯時期評估**constexpr**函數。 如果叫用中斷點，便已在執行階段呼叫此函式。  否則便是在編譯時期呼叫函式。

## <a name="extern-constexpr"></a>extern constexpr

[/Zc: externConstexpr](../build/reference/zc-externconstexpr.md)編譯器選項會使編譯器將[外部連結](../c-language/external-linkage.md)套用至使用**extern constexpr**所宣告的變數。 在舊版的 Visual Studio 中, 如果指定了 **/zc: externConstexpr** , Visual Studio 會將內部連結套用至**constexpr**變數, 即使使用**extern**關鍵字也一樣。 從 Visual Studio 2017 更新15.6 開始提供 **/zc: externConstexpr**選項, 預設為關閉。 /Permissive-選項不會啟用 **/zc: externConstexpr**。

## <a name="example"></a>範例

下列範例會顯示**constexpr**變數、函式和使用者定義型別。 在 main () 中的最後一個語句中, **constexpr**成員函式 GetValue () 是執行時間呼叫, 因為在編譯時期不需要知道此值。

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
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

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
