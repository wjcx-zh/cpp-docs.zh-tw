---
title: 省略符號和 Variadic 範本
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 9c9294089b9f0a144946b7f6b81da2a71ca710bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189256"
---
# <a name="ellipses-and-variadic-templates"></a>省略符號和 Variadic 範本

本文說明如何搭配C++ variadic 範本使用省略號（`...`）。 在 C 和C++中，省略號有許多用途。 這些包括函數的變數引數清單。 C 執行時間程式庫中的 `printf()` 函數是其中一個最知名的範例。

*Variadic 範本*是支援任意數目之引數的類別或函數範本。 這項機制對C++程式庫開發人員特別有用，因為您可以將它套用至類別樣板和函式樣板，進而提供各種型別安全和非一般功能和彈性。

## <a name="syntax"></a>語法

Variadic 範本會以兩種方式使用省略號。 在參數名稱的左邊，它表示*參數套件*，而在參數名稱的右邊，它會將參數套件展開成不同的名稱。

以下是*variadic 範本類別*定義語法的基本範例：

```cpp
template<typename... Arguments> class classname;
```

對於參數封裝和展開，您可以依您的喜好在省略符號周圍加入空白，如下面這些範例所示：

```cpp
template<typename ...Arguments> class classname;
```

或是這個：

```cpp
template<typename ... Arguments> class classname;
```

請注意，本文使用第一個範例中顯示的慣例 (省略符號附加至 `typename`)。

在上述範例中，*引數*是參數套件。 類別 `classname` 可以接受可變數目的引數，如下列範例所示：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

藉由使用 variadic 範本類別定義，您也可以至少需要一個參數：

```cpp
template <typename First, typename... Rest> class classname;
```

以下是*variadic 範本函數*語法的基本範例：

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

然後會展開*引數*參數套件以供使用，如下一節所示：**瞭解 variadic 範本**。

其他形式的 variadic 範本函式語法都可行，包括（但不限於）下列範例：

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

也可以使用像是**const**的規範：

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

如同 variadic 範本類別定義，您可以建立需要至少一個參數的函式：

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Variadic 範本會使用 `sizeof...()` 運算子（與較舊的 `sizeof()` 運算子無關）：

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

- 在範本參數清單（`template <parameter-list>`）中，`typename...` 引進範本參數套件。

- 在參數宣告子句（`func(parameter-list)`）中，「頂層」省略號會引進函式參數套件，而省略號位置很重要：

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- 若省略符號在參數名稱之後顯示，您有參數封裝展開。

## <a name="example"></a>範例

有一個說明 variadic 範本函式機制的好方法，就是在 `printf`的一些功能重新撰寫時使用它：

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

## <a name="output"></a>輸出

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
>  大部分納入 variadic 範本函式的整合都會使用某種形式的遞迴，但與傳統的遞迴有些微不同。  傳統遞迴牽涉到使用相同簽章呼叫本身的函式。 （它可能會多載或樣板化，但每次都會選擇相同的簽章。）Variadic 遞迴牽涉到呼叫 Variadic 函式樣板，方法是使用不同（幾乎一律遞減）的引數數目，因此每次都會將不同的簽章標記為。 仍然需要「基底案例」，但遞迴的本質並不相同。
