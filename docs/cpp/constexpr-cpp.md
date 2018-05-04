---
title: constexpr （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f95f6c98138ff1eb52750c1b8593795ca28c784
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="constexpr-c"></a>constexpr (C++)

關鍵字**constexpr**已導入了 C + + 11 和更佳的 C + + 14。 這表示*常數運算式*。 像**const**，它可以套用至變數，讓任何程式碼嘗試修改值時，就會引發編譯器錯誤。 不同於**const**， **constexpr**也可以套用至函式和類別建構函式。 **constexpr**表示的值或傳回值，是常數，可能的話，會在編譯時期計算。

A **constexpr**只要 const 整數為必要項，例如在樣板引數和陣列宣告，就可以使用整數值。 而且，當可以計算出的值，而不是執行階段編譯時期，它可讓您的程式更快速執行並使用較少的記憶體。

為了限制運算編譯時間常數的複雜性以及其可能造成的編譯時間影響，C + + 14 標準要求參與常數運算式的類型必須受限為[常值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>語法

```
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);
```

## <a name="parameters"></a>參數

 *params*  
必須是常值型別，而必須使用本身的一個或多個參數必須是常數運算式。

## <a name="return-value"></a>傳回值


 Constexpr 變數或函式必須傳回[常值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="constexpr-variables"></a>constexpr 變數

 const 和 constexpr 變數之間的主要差異是 const 變數的初始化可以延遲到執行階段，而 constexpr 變數則必須在編譯時期初始化。  所有的 constexpr 變數都是常數。

- 變數可宣告為**constexpr**，如果它具有常值型別，並已初始化。 如果建構函式執行初始化，則建構函式必須宣告為**constexpr**。

- 如果所參考的物件已由常數運算式初始化，而且在初始化期間叫用的任何隱含轉換也是常數運算式，則參考可以宣告為 constexpr。

- 所有宣告**constexpr**變數或函式必須有**constexpr**規範。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> constexpr 函式

A **constexpr**函式是耗用程式碼需要它時，可以在編譯計算其傳回的值。  當其引數為**constexpr**值，而且耗用程式碼需要傳回值在編譯時期，例如初始化**constexpr**變數，或提供非類型樣板引數，它會產生編譯時間常數。 當呼叫與非**constexpr**引數，或不在編譯時間需要其值時，便會像一般函式的執行階段產生值。  (這種雙行為讓您不必撰寫**constexpr**和非-**constexpr**相同函式的版本。)

A **constexpr**函式或建構函式已隱含**內嵌**。

下列規則適用於 constexpr 函式：

- A **constexpr**函式必須接受並僅傳回[常值型別](trivial-standard-layout-and-pod-types.md#literal_types)。

- A **constexpr**函式可以是遞迴式。

- 它不能[虛擬](../cpp/virtual-cpp.md)。 建構函式不能定義為 constexpr 封入類別有任何虛擬基底類別。

- 主體可以定義為 **= 預設**或 **= 刪除**。

- 主體不可以包含**goto**陳述式或 try 區塊。

- 非 constexpr 範本的明確特製化可以宣告為**constexpr**:

- 明確特製化**constexpr**範本就不需要也是**constexpr**:

下列規則適用於**constexpr**函式在 Visual Studio 2017 和更新版本：

- 它可以包含**如果**和**切換**陳述式，以及所有迴圈陳述式包括**如**、 範圍架構 for，**時**，和**不要-雖然**。
 
- 它可能包含本機變數宣告，但變數必須進行初始化、 必須是常值型別，而且不能是靜態或執行緒區域。 在本機宣告的變數不需要是 const，可能會變動。

- Constexpr 非靜態成員函式不需要為 const 隱含。


```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 注意： 在 Visual Studio 偵錯工具中，當偵錯非 optimised 偵錯組建中，您所見是否**constexpr**函式在編譯時期將中斷點放入評估。 如果叫用中斷點，便已在執行階段呼叫此函式。  否則便是在編譯時期呼叫函式。

## <a name="extern-constexpr"></a>extern constexpr

[/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)編譯器選項會使編譯器套用[外部連結]()變數宣告可透過**extern constexpr**。 在舊版的 Visual Studio，而且依預設或 **/Zc:externConstexpr-** 指定時，Visual Studio 會套用到內部連結**constexpr**變數，即使**extern**關鍵字使用。 **/Zc:externConstexpr**選項才可以使用 Visual Studio 2017 更新 15.6 中啟動。 和預設為關閉。 /Permissive-option 不會啟用 /Zc:externConstexpr。

## <a name="example"></a>範例

 下列範例所示**constexpr**變數、 函式和使用者定義型別。 請注意，在 main （），最後一個陳述式**constexpr**成員函式 getvalue （） 是執行階段呼叫，因為不需要在編譯時期已知的值。

```cpp
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

// Compile time computation of array length
template<typename T, int N>
constexpr int length(const T(&ary)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n*fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue()
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    //foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    //Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    //Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;

}

```

## <a name="requirements"></a>需求

Visual Studio 2015

## <a name="see-also"></a>另請參閱

- [宣告和定義](../cpp/declarations-and-definitions-cpp.md)
- [const](../cpp/const-cpp.md)
