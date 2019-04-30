---
title: 省略符號和 Variadic 範本
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 387cf4478192cb9470804c219eee8046f8e47abe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392215"
---
# <a name="ellipses-and-variadic-templates"></a>省略符號和 Variadic 範本

這篇文章示範如何使用省略符號 (`...`) 與C++variadic 範本。 省略符號已在 C 中有許多用途和C++。 這些包括函式的變數引數清單。 `printf()` C 執行階段程式庫函式是眾所皆知的範例之一。

A *variadic 樣板*是支援任意數目的引數的類別或函式範本。 這項機制會特別有幫助C++程式庫開發人員因為您可以將它套用至類別樣板和函式樣板，並藉此提供各種不同的型別安全和重要的功能和彈性。

## <a name="syntax"></a>語法

省略符號用於兩種方式，在 variadic 範本。 參數名稱左邊，它表示*參數封裝*，和右邊的參數名稱，它會展開參數封裝至不同的名稱。

以下是基本的範例*variadic 樣板類別*定義語法：

```cpp
template<typename... Arguments> class classname;
```

對於參數封裝和展開，您可以依您的喜好在省略符號周圍加入空白，如下面這些範例所示：

```cpp
template<typename ...Arguments> class classname;
```

或這個：

```cpp
template<typename ... Arguments> class classname;
```

請注意，本文使用第一個範例中顯示的慣例 (省略符號附加至 `typename`)。

在上述範例中，*引數*是參數封裝。 此類別`classname`可以接受變動數目的引數，如下列範例所示：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

藉由使用 variadic 樣板類別定義，您也可以要求至少一個參數：

```cpp
template <typename First, typename... Rest> class classname;
```

以下是基本的範例*variadic 樣板函式*語法：

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

*引數*下一節所示，供使用，然後展開參數封裝**了解 variadic 範本**。

可能會有其他形式的 variadic 樣板函式語法，包括但不是限於這些範例：

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

規範喜歡**const**也允許：

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

為使用 variadic 樣板類別定義，您可以進行需要至少一個參數的函式：

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

使用 Variadic 樣板`sizeof...()`運算子 (不相關的舊版`sizeof()`運算子):

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>進一步了解省略符號位置

在過去，本文說明了定義參數封裝和展開的省略符號位置，「在參數名稱左邊的它表示參數封裝，在參數名稱右邊，它展開參數封裝至不同的名稱」。 這在技術上是對的，但是在轉譯程式碼上可能會造成混淆。 請考慮：

- 在範本參數清單 (`template <parameter-list>`)，`typename...`引入樣板參數封裝。

- 在參數宣告子句 (`func(parameter-list)`)、 「 最上層 」 省略符號引入函式參數封裝，並省略符號位置非常重要：

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- 若省略符號在參數名稱之後顯示，您有參數封裝展開。

## <a name="example"></a>範例

說明 variadic 範本功能機制的好方法是使用它在重寫的部分的功能`printf`:

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>Output

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
>  合併 variadic 樣板函式的大部分實作會使用遞迴的某種形式，但它是與傳統遞迴稍有不同。  傳統遞迴涉及使用相同的簽章來呼叫本身函式。 （可能是多載或設為範本，但每次都會選擇相同的簽章）。Variadic 遞迴包含使用不同 （幾乎一定會減少） 的數字的引數，並藉此戳記不同的簽章每次呼叫 variadic 函式樣板。 「 基底案例 」 仍需要，但遞迴性質不同。