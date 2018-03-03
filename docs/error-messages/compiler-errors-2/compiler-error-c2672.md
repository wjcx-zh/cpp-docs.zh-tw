---
title: "編譯器錯誤 C2672 |Microsoft 文件"
ms.date: 10/24/2017
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C2672
dev_langs:
- C++
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52663aed470aff254d07cba6a65f484269d8703d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2672"></a>編譯器錯誤 C2672

> '*函式*': 沒有相符的多載找到函式

編譯器找不到符合指定的函式多載函式。 找不到相符的參數或沒有符合的函式會在內容中有必要的協助工具的任何函式。

由特定的標準程式庫容器或演算法時，您的型別必須提供可存取的成員或 friend 函式符合需求的容器或演算法。 例如，迭代器類型應該衍生自`std::iterator<>`。 比較作業或使用其他運算子的容器項目類型，可能需要類型被視為左、 右運算元。 使用類型的右方運算元可以為之型別的非成員函式需要運算子的實作。

## <a name="example"></a>範例

版本的編譯器，Visual Studio 2017 之前並未執行存取檢查某些範本內容中的限定名稱。 這可能會干擾預期 SFINAE 行為，其中，替代預期會因無法存取名稱而失敗。 這可能會在執行階段因編譯器錯誤地呼叫運算子的錯誤多載而導致當機或意外行為。 在 Visual Studio 2017 中，會引發編譯器錯誤。

此範例會在 Visual Studio 2015 中編譯，但 Visual Studio 2017 中引發錯誤。 若要修正此問題，請存取的範本參數成員評估的位置。

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