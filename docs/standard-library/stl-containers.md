---
title: C++ 標準程式庫容器
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, template class containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 240a05822ea93493c917469fc18fa8a9c224359d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568619"
---
# <a name="c-standard-library-containers"></a>C++ 標準程式庫容器

標準程式庫提供用來存放相關物件集合的各種類型安全容器。 這些容器是類別範本；當您宣告容器變數時，您會指定容器將會保留的項目類型。 容器可與初始設定式清單一起建構。 它們有成員函式，可供加入和移除項目以及執行其他作業。

您可以使用[迭代器](../standard-library/iterators.md)，逐一執行容器中的項目以及存取個別元素。 您可以透過使用迭代器的成員函式與運算子，以及全域函式，來明確地使用迭代器。 您也能以隱含的方式使用，例如透過使用 range-for 迴圈。 所有 C++ 標準程式庫容器的迭代器具有一個通用介面，但每個容器都會定義它自己的特製化迭代器。

容器可以分為三類：序列容器、關聯容器和容器配接器。

## <a name="sequence_containers"></a> 序列容器

序列容器維護您指定之插入項目的順序。

`vector` 容器的行為就像陣列，不過可以視需要自動擴增。 它是隨機存取和連續儲存，而且長度有高度彈性。 因此 (和基於其他原因)，`vector` 是大多數應用程式慣用的序列容器。 若不確定要使用何種序列容器，就使用 vector 開始吧！ 如需詳細資訊，請參閱 [vector 類別](../standard-library/vector-class.md)。

`array` 容器具有 `vector` 的某些強項，不過，長度不如後者有彈性。 如需詳細資訊，請參閱 [array 類別](../standard-library/array-class-stl.md)。

`deque` (雙向佇列) 容器允許在容器開頭和結尾快速插入和刪除。 它與 `vector` 有相同的隨機存取和彈性長度優點，但不是連續的。 如需詳細資訊，請參閱 [deque 類別](../standard-library/deque-class.md)。

`list` 容器是可在容器中任何位置雙向存取、快速插入和快速刪除的雙向連結清單，不過，您不能隨機存取容器中的項目。 如需詳細資訊，請參閱 [list 類別](../standard-library/list-class.md)。

`forward_list` 容器是單向連結清單，即 `list` 的正向存取版本。 如需詳細資訊，請參閱 [forward_list 類別](../standard-library/forward-list-class.md)。

## <a name="associative-containers"></a>關聯容器

在關聯容器中，項目是依照預先定義的順序插入，例如，做為遞增排序。 未排序的關聯容器也可供使用。 關聯容器可分組為兩個子集：對應 (map) 和集合 (set)。

`map` 有時稱為字典，包含的索引鍵/值組。 索引鍵用於排序順序，而值與該索引鍵相關聯。 例如，`map` 可能包含索引鍵和對應值。前者表示文字中的每個唯一字詞，後者表示每個字詞顯示在文字中的次數。 `map` 未排序的版本為 `unordered_map`。 如需詳細資訊，請參閱 [map 類別](../standard-library/map-class.md)和 [unordered_map 類別](../standard-library/unordered-map-class.md)。

`set` 只是唯一項目的遞增容器—值也是索引鍵。 `set` 未排序的版本為 `unordered_set`。 如需詳細資訊，請參閱 [set 類別](../standard-library/set-class.md)和 [unordered_set 類別](../standard-library/unordered-set-class.md)。

`map` 和 `set` 只允許索引鍵或項目的一個執行個體插入至容器。 如果需要項目的多個執行個體，請使用 `multimap` 或 `multiset`。 未排序的版本為 `unordered_multimap` 和 `unordered_multiset`。 如需詳細資訊，請參閱 [multimap 類別](../standard-library/multimap-class.md)、[unordered_multimap 類別](../standard-library/unordered-multimap-class.md)、[multiset 類別](../standard-library/multiset-class.md)及 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)。

已排序的對應和集合支援雙向迭代器，而未排序的對應項目則支援正向迭代器。 如需詳細資訊，請參閱[迭代器](../standard-library/iterators.md)。

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>關聯容器中的異質查閱 (C++14)

已排序的關聯容器 (map、multimap、set 和 multiset) 現可支援異質查閱，這表示您不再需要傳遞完全相同的物件類型做為成員函式中的索引鍵或項目，例如 `find()` 和 `lower_bound()`。 您反而可以傳遞任何已定義多載 `operator<` 的類型，以便與索引鍵類型進行比較。

當您在宣告容器變數時指定 `std::less<>` 或 `std::greater<>` "diamond functor" 比較運算子，則會根據加入與否來啟用異質查閱，如下所示：

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

如果您使用預設比較運算子，則容器行為就像在 C++ 11 或更早版本中一樣。

下列範例示範如何多載 `operator<`，讓 `std::set` 的使用者只要傳入可與每個物件的 `BigObject::id` 成員進行比較的小字串即可進行查閱。

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

map、multimap、set 和 multiset 中的下列成員函式已多載來支援異質查閱：

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>容器配接器

容器配接器是為了簡化和清晰而限制介面的序列或關聯容器的變化。 容器配接器不支援迭代器。

`queue` 容器遵循 FIFO (先進先出) 語意。 第一個「推入」(也就是插入佇列) 的項目是第一個「推出」(也就是從佇列移除) 的項目。 如需詳細資訊，請參閱 [queue 類別](../standard-library/queue-class.md)。

`priority_queue` 容器的排序方式會讓具有最大值的項目一定在佇列中的第一個。 如需詳細資訊，請參閱 [priority_queue 類別](../standard-library/priority-queue-class.md)。

`stack` 容器遵循 LIFO (後進先出) 語意。 最後一個推入至堆疊的項目是第一個推出的項目。 如需詳細資訊，請參閱 [stack 類別](../standard-library/stack-class.md)。

由於容器配接器不支援迭代器，因此無法與 C++ 標準程式庫演算法一起使用。 如需詳細資訊，請參閱[演算法](../standard-library/algorithms.md)。

## <a name="requirements-for-container-elements"></a>容器項目的需求

一般而言，插入至 C++ 標準程式庫容器的項目可以是任何可複製的物件類型。 僅可移動的項目 (例如，使用 `vector<unique_ptr<T>>` 建立的項目如 `unique_ptr<>`) 也能正常運作，只要您不會呼叫嘗試對其進行複製的成員函式。

不允許解構函式擲回例外狀況。

已排序的關聯容器 (本文件稍早所述) 必須已定義公用的比較運算子。 根據預設，此運算子是 `operator<`，但是也支援不能搭配 `operator<` 一起使用的類型。

容器的某些作業可能也需要公用預設建構函式和公用等價運算子。 例如，未排序的關聯容器需要相等和雜湊支援。

## <a name="accessing-container-elements"></a>存取容器項目

容器項目是透過使用迭代器進行存取。 如需詳細資訊，請參閱 [Iterator](../standard-library/iterators.md)。

> [!NOTE]
> 您也可以使用[範圍架構的 for 迴圈](../cpp/range-based-for-statement-cpp.md)來逐一執行 C++ 標準程式庫集合。

## <a name="comparing-containers"></a>比較容器

所有容器多都載 operator==，以便比較兩個具有相同項目類型的同類型容器。 您可以使用 ==，將一個 vector\<string> 與另一個 vector\<string> 進行比較，但無法用來比較 vector\<string> 與 list\<string> 或比較 vector\<string> 與 vector\<char*>。  在 C++98/03 中，您可以使用 [std::equal](algorithm-functions.md#equal) 或 [std::mismatch](algorithm-functions.md#mismatch) 來比較不同的容器類型和/或項目類型。 在 C++11 中，您也可以使用 [std::is_permutation](algorithm-functions.md#is_permutation)。 但在上述所有情況下，函式會假設容器的長度相同。 如果第二個範圍比第一個範圍短，則會造成未定義的行為。 如果第二個範圍比較長，則結果仍然可能不正確，因為超過第一個範圍的結尾就不會繼續比較。

### <a name="comparing-dissimilar-containers-c14"></a>比較不同的容器 (C++14)

在 C + + 14 和更新版本，您可以使用其中一種比較不同的容器和/或不同的項目類型`std::equal`， `std::mismatch`，或`std::is_permutation`函式採用兩個完整範圍的多載。 這些多載可讓您比較具有不同長度的容器。 這些多載比較不容易發生使用者錯誤並已最佳化，以在比較不同長度的容器時的常數時間傳回 false。 因此，我們建議您使用這些多載，除非 (1) 您有非常清楚的理由不要使用，或 (2) 您使用未受益於雙重範圍最佳化的 [std::list](../standard-library/list-class.md) 容器。

## <a name="see-also"></a>另請參閱

[容器](../cpp/containers-modern-cpp.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
[\<範例容器>](../standard-library/sample-container.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
