---
title: 容器 (現代 C++)
ms.date: 1/18/2018
ms.topic: conceptual
ms.openlocfilehash: 2da57bfca8b04f50a223dddfb886835c69f746a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392332"
---
# <a name="containers-modern-c"></a>容器 (現代 C++)

根據預設，使用[向量](../standard-library/vector-class.md)做為慣用的循序容器，在C++。 這相當於`List<T>`以.NET 語言。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[地圖](../standard-library/map-class.md)(不`unordered_map`) 做為預設關聯容器。 使用[設定](../standard-library/set-class.md)， [multimap](../standard-library/multimap-class.md)，並[multiset](../standard-library/multiset-class.md)變質 & 多案例。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

當需要效能最佳化時，請考慮使用：

- [陣列](../standard-library/array-class-stl.md)輸入當內嵌很重要的比方說，做為類別成員。

- 這類未排序關聯容器[unordered_map](../standard-library/unordered-map-class.md)。 這些額外負荷已降低每個項目和固定時間搜尋，但它們可以是使用正確且有效率的工作變得更難。

- 排序`vector`。 如需詳細資訊，請參閱[演算法](../cpp/algorithms-modern-cpp.md)。

請勿使用 c-style 陣列。 對於較舊的 Api 需要直接存取資料，使用存取子方法例如`f(vec.data(), vec.size());`改。

如需有關容器的詳細資訊，請參閱 < [ C++標準程式庫容器](../standard-library/stl-containers.md)。

## <a name="see-also"></a>另請參閱

[歡迎回到 C++ (現代 C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
