---
title: 橢圓和瓦里亞迪奇範本
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 8326a6b9e75db6adc37a68aa5d5741b004d27d30
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031520"
---
# <a name="ellipsis-and-variadic-templates"></a>橢圓和瓦里亞迪奇範本

本文演示如何將省略號 ()`...`與C++可變範本一起使用. 橢圓在C和C++中有許多用途。 其中包括函數的變數參數清單。 C`printf()`運行時庫中的函數是最廣為人知的示例之一。

*可變範本*是支援任意數量的參數的類或函數範本。 此機制對於C++庫開發人員特別有用,因為您可以將其應用於類範本和函數範本,從而提供廣泛的類型安全和非普通功能和靈活性。

## <a name="syntax"></a>語法

雜音範本以兩種方式使用省略號。 在參數名稱的左側,它表示*參數包*,在參數名稱的右側,它將參數包擴展到單獨的名稱中。

下面是*可變範本類別*定義語法的基本範例:

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

在前面的範例中,*參數*是參數包。 類別`classname`可以接受可變數量的參數,如以下範例所示:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

通過使用可變範本類定義,還可以至少需要一個參數:

```cpp
template <typename First, typename... Rest> class classname;
```

下面是*可變範本函式*法的基本範例:

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

然後展開*參數*包以使用,如下一節"**理解可變範本"中**所示。

其他形式的可變樣本函數語法是可能的, 包括但不限於這些範例:

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

也允許像**康斯特**這樣的指定者:

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

與可變樣本類別定義一樣,您可以產生至少需要一個參數的函數:

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

可變樣本使用`sizeof...()`運算子(與較舊的`sizeof()`運算子無關):

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

- 在範本參數清單 ()`template <parameter-list>``typename...`中引入了範本參數包。

- 在參數聲明子句 ()`func(parameter-list)`中,「頂級」橢圓引入函數參數包,省略號定位很重要:

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- 若省略符號在參數名稱之後顯示，您有參數封裝展開。

## <a name="example"></a>範例

說明可變樣本函式機制的一個好方法是在重寫`printf`: 的一些功能時使用它:

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
> 大多數包含可變範本函數的實現使用某種形式的遞歸,但它與傳統遞歸略有不同。  傳統的遞歸涉及使用同一簽名調用自己的函數。 (它可能重載或範本化,但每次都選擇相同的簽名。變幻性遞歸涉及使用不同(幾乎總是減少)參數數調用變數函數範本,從而每次標記出不同的簽名。 仍然需要"基本情況",但遞歸的性質不同。
