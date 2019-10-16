---
title: 容器 (現代 C++)
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: 37b540132fc9ddc03d5eaafd33c545b5db5e7935
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926252"
---
# <a name="containers-modern-c"></a>容器 (現代 C++)

根據預設，會在中 C++ 使用[向量](../standard-library/vector-class.md)做為慣用的順序容器。 這相當於`List<T>` .net 語言中的。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用 [[對應](../standard-library/map-class.md)（ `unordered_map`not）] 做為預設的關聯容器。 將[set](../standard-library/set-class.md)、 [multimap](../standard-library/multimap-class.md)和[多重集](../standard-library/multiset-class.md)用於退化 & 多個案例。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

當需要效能優化時，請考慮使用：

- 內嵌時的[陣列](../standard-library/array-class-stl.md)類型很重要，例如，做為類別成員。

- 未排序的關聯容器，例如[unordered_map](../standard-library/unordered-map-class.md)。 這些專案具有較低的每個元素額外負荷和持續時間查詢，但可能難以正確且有效率地使用。

- 已`vector`排序。 如需詳細資訊，請參閱[演算法](../cpp/algorithms-modern-cpp.md)。

請勿使用 C 樣式陣列。 對於需要直接存取資料的舊版 api，請改用存取子方法（例如`f(vec.data(), vec.size());` ）。

如需容器的詳細資訊，請參閱[ C++標準程式庫容器](../standard-library/stl-containers.md)。

## <a name="see-also"></a>另請參閱

[歡迎回到 C++ (現代 C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
