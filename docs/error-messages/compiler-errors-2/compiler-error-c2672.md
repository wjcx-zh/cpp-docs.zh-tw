---
title: 編譯器錯誤 C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: df0f656c9db23739ec62629088b9cc5f7950a92d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570439"
---
# <a name="compiler-error-c2672"></a>編譯器錯誤 C2672

> '*函式*': 沒有相符的多載函式找到

編譯器找不到符合指定的函式多載函式。 找不到相符的參數或沒有相符的函式會採用具有所需的協助工具，在內容中的任何函式。

當使用特定的標準程式庫容器或演算法，可存取的成員或 friend 函式符合演算法之容器的需求，必須提供您的型別。 比方說，迭代器類型應該衍生自`std::iterator<>`。 比較作業或其他容器項目類型的運算子使用，可能需要型別會被視為左側和右側的運算元。 使用類型的右運算元可以為類型的非成員函式需要運算子的實作。

## <a name="example"></a>範例

版本的編譯器，Visual Studio 2017 之前並未執行存取檢查部分範本內容中限定名稱。 這可能會干擾預期 SFINAE 行為，其中，替代預期會因無法存取名稱而失敗。 這可能會在執行階段因編譯器錯誤地呼叫運算子的錯誤多載而導致當機或意外行為。 在 Visual Studio 2017 中，會引發編譯器錯誤。

此範例是在 Visual Studio 2015 中編譯，但 Visual Studio 2017 中引發錯誤。 若要修正此問題，讓範本參數成員可存取評估的位置。

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