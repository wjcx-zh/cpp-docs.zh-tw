---
title: C++ 標準程式庫容器
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, class template containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 01be754dd7b418f64cf495d7563f65b323265df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376693"
---
# <a name="c-standard-library-containers"></a>C++ 標準程式庫容器

標準程式庫提供用來存放相關物件集合的各種類型安全容器。 容器是類範本。 聲明容器變數時,可以指定容器將容納的元素的類型。 容器可與初始設定式清單一起建構。 它們具有用於添加和刪除元素以及執行其他操作的成員函數。

您可以使用[迭代器](../standard-library/iterators.md)，逐一執行容器中的項目以及存取個別元素。 您可以使用反覆運算器的成員函數、運算子和全域函數顯式使用反覆運算器。 您也能以隱含的方式使用，例如透過使用 range-for 迴圈。 所有 C++ 標準程式庫容器的迭代器具有一個通用介面，但每個容器都會定義它自己的特製化迭代器。

容器可以分為三類：序列容器、關聯容器和容器配接器。

## <a name="sequence-containers"></a><a name="sequence_containers"></a> 序列容器

序列容器維護您指定之插入項目的順序。

`vector` 容器的行為就像陣列，不過可以視需要自動擴增。 它是隨機存取和連續儲存，而且長度有高度彈性。 因此 (和基於其他原因)，`vector` 是大多數應用程式慣用的序列容器。 若不確定要使用何種序列容器，就使用 vector 開始吧！ 如需詳細資訊，請參閱 [vector 類別](../standard-library/vector-class.md)。

`array`容器具有一些優點`vector`,但長度並不靈活。 如需詳細資訊，請參閱 [array 類別](../standard-library/array-class-stl.md)。

`deque` (雙向佇列) 容器允許在容器開頭和結尾快速插入和刪除。 它共用的隨機訪問和靈活長度的優點`vector`,但不是連續的。 如需詳細資訊，請參閱 [deque 類別](../standard-library/deque-class.md)。

`list`容器是一個雙連結清單,可在容器中的任何位置實現雙向訪問、快速插入和快速刪除,但不能隨機存取容器中的元素。 如需詳細資訊，請參閱 [list 類別](../standard-library/list-class.md)。

`forward_list` 容器是單向連結清單，即 `list` 的正向存取版本。 如需詳細資訊，請參閱 [forward_list 類別](../standard-library/forward-list-class.md)。

## <a name="associative-containers"></a>關聯容器

在關聯容器中，項目是依照預先定義的順序插入，例如，做為遞增排序。 未排序的關聯容器也可供使用。 關聯容器可分組為兩個子集：對應 (map) 和集合 (set)。

`map` 有時稱為字典，包含的索引鍵/值組。 索引鍵用於排序順序，而值與該索引鍵相關聯。 例如，`map` 可能包含索引鍵和對應值。前者表示文字中的每個唯一字詞，後者表示每個字詞顯示在文字中的次數。 `map` 未排序的版本為 `unordered_map`。 如需詳細資訊，請參閱 [map 類別](../standard-library/map-class.md)和 [unordered_map 類別](../standard-library/unordered-map-class.md)。

`set` 只是唯一項目的遞增容器—值也是索引鍵。 `set` 未排序的版本為 `unordered_set`。 如需詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)和 [unordered_set 類別](../standard-library/unordered-set-class.md)。

`map` 和 `set` 只允許索引鍵或項目的一個執行個體插入至容器。 如果需要項目的多個執行個體，請使用 `multimap` 或 `multiset`。 未排序的版本為 `unordered_multimap` 和 `unordered_multiset`。 如需詳細資訊，請參閱 [multimap 類別](../standard-library/multimap-class.md)、[unordered_multimap 類別](../standard-library/unordered-multimap-class.md)、[multiset 類別](../standard-library/multiset-class.md)及 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

已排序的對應和集合支援雙向迭代器，而未排序的對應項目則支援正向迭代器。 有關詳細資訊,請參閱[反覆運算器](../standard-library/iterators.md)。

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>關聯容器中的異質查閱 (C++14)

有序的關聯容器(映射、多映射、集和多集)現在支援異構查找,這意味著您不再需要傳遞與成員函數(如`find()`和`lower_bound()`) 中的鍵或元素完全相同的物件類型。 您反而可以傳遞任何已定義多載 `operator<` 的類型，以便與索引鍵類型進行比較。

當您在宣告容器變數時指定 `std::less<>` 或 `std::greater<>` "diamond functor" 比較運算子，則會根據加入與否來啟用異質查閱，如下所示：

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

如果您使用預設比較運算子，則容器行為就像在 C++ 11 或更早版本中一樣。

下面的示例演示如何重載`operator<`,使`std::set`使用者 只需傳入一個可以`BigObject::id`與每個對象 的成員進行比較的小字串,即可執行查找。

```cpp
#include <set>
#include <string>
#include <iostream>
#include <functional>

using namespace std;

class BigObject
{
public:
    string id;
    explicit BigObject(const string& s) : id(s) {}
    bool operator< (const BigObject& other) const
    {
        return this->id < other.id;
    }

    // Other members....
};

inline bool operator<(const string& otherId, const BigObject& obj)
{
    return otherId < obj.id;
}

inline bool operator<(const BigObject& obj, const string& otherId)
{
    return obj.id < otherId;
}

int main()
{
    // Use C++14 brace-init syntax to invoke BigObject(string).
    // The s suffix invokes string ctor. It is a C++14 user-defined
    // literal defined in <string>
    BigObject b1{ "42F"s };
    BigObject b2{ "52F"s };
    BigObject b3{ "62F"s };
    set<BigObject, less<>> myNewSet; // C++14
    myNewSet.insert(b1);
    myNewSet.insert(b2);
    myNewSet.insert(b3);
    auto it = myNewSet.find(string("62F"));
    if (it != myNewSet.end())
        cout << "myNewSet element = " << it->id << endl;
    else
        cout << "element not found " << endl;

    // Keep console open in debug mode:
    cout << endl << "Press Enter to exit.";
    string s;
    getline(cin, s);
    return 0;
}

//Output: myNewSet element = 62F
```

地圖、多映射、集和多集中中的以下成員函數已過載,以支援異構查找:

1. 尋找

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>容器配接器

容器配接器是為了簡化和清晰而限制介面的序列或關聯容器的變化。 容器適配器不支援反覆運算器。

`queue` 容器遵循 FIFO (先進先出) 語意。 第一個「推入」**(也就是插入佇列) 的項目是第一個「推出」**(也就是從佇列移除) 的項目。 如需詳細資訊，請參閱 [queue 類別](../standard-library/queue-class.md)。

`priority_queue` 容器的排序方式會讓具有最大值的項目一定在佇列中的第一個。 如需詳細資訊，請參閱 [priority_queue 類別](../standard-library/priority-queue-class.md)。

`stack` 容器遵循 LIFO (後進先出) 語意。 最後一個推入至堆疊的項目是第一個推出的項目。 如需詳細資訊，請參閱 [stack 類別](../standard-library/stack-class.md)。

由於容器適配器不支援反覆運算器,因此不能將其與C++標準庫演演演算法一起使用。 如需詳細資訊，請參閱[演算法](../standard-library/algorithms.md)。

## <a name="requirements-for-container-elements"></a>容器項目的需求

一般而言，插入至 C++ 標準程式庫容器的項目可以是任何可複製的物件類型。 僅可移動的項目 (例如，使用 `vector<unique_ptr<T>>` 建立的項目如 `unique_ptr<>`) 也能正常運作，只要您不會呼叫嘗試對其進行複製的成員函式。

析構函數不允許引發異常。

已排序的關聯容器 (本文件稍早所述) 必須已定義公用的比較運算子。 根據預設，此運算子是 `operator<`，但是也支援不能搭配 `operator<` 一起使用的類型。

容器的某些作業可能也需要公用預設建構函式和公用等價運算子。 例如，未排序的關聯容器需要相等和雜湊支援。

## <a name="accessing-container-elements"></a>存取容器項目

容器項目是透過使用迭代器進行存取。 有關詳細資訊,請參閱[反覆運算器](../standard-library/iterators.md)。

> [!NOTE]
> 您也可以使用[範圍架構的 for 迴圈](../cpp/range-based-for-statement-cpp.md)來逐一執行 C++ 標準程式庫集合。

## <a name="comparing-containers"></a>比較容器

所有容器多都載 operator==，以便比較兩個具有相同項目類型的同類型容器。 可以使用 *\<將 向量字串>另一個\<向量 字串>,但不能使用它將\<向量 字串>比較\<到列表 字串>或\<向量 字串>\<向量 字串>。  在 C++98/03 中,可以使用[std::等於](algorithm-functions.md#equal)或[std:::不匹配](algorithm-functions.md#mismatch)來比較不同的容器類型和/或元素類型。 在 C++11 中,您還可以使用[std::is_permutation](algorithm-functions.md#is_permutation)。 但在所有這些情況下,函數假定容器的長度相同。 如果第二個範圍比第一個範圍短，則會造成未定義的行為。 如果第二個範圍比較長，則結果仍然可能不正確，因為超過第一個範圍的結尾就不會繼續比較。

### <a name="comparing-dissimilar-containers-c14"></a>比較不同的容器 (C++14)

在 C++14 及更高版本中,可以使用具有兩個完整`std::equal`範圍的`std::mismatch``std::is_permutation`、或函數重載之一比較不同的容器和/或不同的元素類型。 這些多載可讓您比較具有不同長度的容器。 這些多載比較不容易發生使用者錯誤並已最佳化，以在比較不同長度的容器時的常數時間傳回 false。 因此,我們建議您使用這些重載,除非您有明確的理由不使用,或者您使用的是[std::list](../standard-library/list-class.md)容器,該容器不受益於雙範圍優化。

## <a name="see-also"></a>另請參閱

[平行容器](../parallel/concrt/parallel-containers-and-objects.md)\
[\<範例容器>](../standard-library/sample-container.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
