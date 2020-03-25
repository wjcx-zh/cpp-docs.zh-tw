---
title: 編譯器錯誤 C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 9f844b54285a7df69bfb4387a7afcc82dfef9252
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177127"
---
# <a name="compiler-error-c2672"></a>編譯器錯誤 C2672

> '*function*'：找不到符合的多載函式

編譯器找不到符合指定函數的多載函式。 找不到接受相符參數的函數，或沒有相符的函式在內容中具有必要的存取範圍。

當特定標準程式庫容器或演算法使用時，您的型別必須提供可存取的成員或 friend 函式，以滿足容器或演算法的需求。 例如，您的反覆運算器類型應該衍生自 `std::iterator<>`。 在容器元素類型上進行比較作業或其他運算子的使用，可能需要將類型視為左側和右運算元。 使用類型做為右運算元，可能需要將運算子實作為類型的非成員函式。

## <a name="example"></a>範例

Visual Studio 2017 之前的編譯器版本不會對某些範本內容中的限定名稱執行存取檢查。 這可能會干擾預期 SFINAE 行為，其中，替代預期會因無法存取名稱而失敗。 這可能會在執行階段因編譯器錯誤地呼叫運算子的錯誤多載而導致當機或意外行為。 在 Visual Studio 2017 中，會引發編譯器錯誤。

這個範例會在 Visual Studio 2015 中進行編譯，但會在 Visual Studio 2017 中引發錯誤。 若要修正此問題，請讓範本參數成員在評估時可存取。

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```
