---
title: list 類別
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: c38c6823f48d61cf616f7b91a96dfcc040d666ed
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246489"
---
# <a name="list-class"></a>list 類別

「C++ 標準程式庫」list 類別是序列容器的範本類別，這些容器是以線性排列方式維護其元素，可讓在序列內任何位置進行的插入和刪除都相當有效率。 此序列會儲存為雙向連結的元素清單，每一個都包含某種 *Type* 類型的成員。

## <a name="syntax"></a>語法

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>參數

*型別*\
要存放在清單中的元素資料類型。

*配置器*\
代表預存配置器物件的類型，封裝有關清單之記憶體配置和解除配置的詳細資訊。 這個引數為選擇性，而且預設值是**allocator**\<*類型*>。

## <a name="remarks"></a>備註

選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 當需要隨機存取任何元素，且只要在序列結尾處插入或刪除元素，則向量應該是管理序列的慣用容器。 當需要隨機存取，且需要在序列的開頭和結尾進行插入和刪除時，類別 deque 容器的效能是很好的。

list 成員函式 [merge](#merge)、[reverse](#reverse)、[unique](#unique)、[remove](#remove) 及 [remove_if](#remove_if) 已針對 list 物件上的運算進行最佳化，可為它們的泛型對應項提供高效能的替代方案。

當成員函式必須插入或清除清單的元素時，就會發生清單重新配置。 在所有這種情況下，只有指向受控制序列的清除部份的迭代器或參考會變成無效。

包括「C++ 標準程式庫」標準標頭 \<list> 以定義[容器](../standard-library/stl-containers.md)範本類別清單和數個支援範本。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[list](#list)|建構特定大小的清單，或具有特定值之元素的清單，或具有特定 `allocator` 的清單，或是做為其他清單的複本。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|類型，表示清單物件的 `allocator` 類別。|
|[const_iterator](#const_iterator)|一種類型，提供可讀取清單中任何 **const** 元素的雙向迭代器。|
|[const_pointer](#const_pointer)|此類型提供的指標**const**清單中的項目。|
|[const_reference](#const_reference)|一種類型，提供對儲存在清單中以供讀取和執行 **const** 運算之 **const** 元素的參考。|
|[const_reverse_iterator](#const_reverse_iterator)|一種類型，提供可讀取清單中任何 **const** 元素的雙向迭代器。|
|[difference_type](#difference_type)|類型，提供兩個指出相同清單內之元素的迭代器間的差異。|
|[iterator](#iterator)|類型，提供可以讀取或修改清單中之任何元素的雙向迭代器。|
|[pointer](#pointer)|類型，提供清單中的元素指標。|
|[reference](#reference)|一種類型，提供對儲存在清單中以供讀取和執行 **const** 運算之 **const** 元素的參考。|
|[reverse_iterator](#reverse_iterator)|類型，提供可以讀取或修改反轉清單中之元素的雙向迭代器。|
|[size_type](#size_type)|計算清單中元素數目的類型。|
|[value_type](#value_type)|類型，表示儲存在清單中的資料類型。|

### <a name="functions"></a>函式

|||
|-|-|
|[assign](#assign)|清除清單中的元素，並複製一組新的元素至目標 list。|
|[back](#back)|傳回清單的最後一個元素的參考。|
|[begin](#begin)|傳回迭代器，其定址清單中的第一個元素。|
|[cbegin](#cbegin)|傳回 const 迭代器，其定址清單中的第一個元素。|
|[cend](#cend)|傳回 const 迭代器，其定址清單中最後一個元素的下一個位置。|
|[clear](#clear)|清除清單的所有元素。|
|[crbegin](#crbegin)|傳回 const 迭代器，其定址反轉清單中的第一個元素。|
|[crend](#crend)|傳回 const 迭代器，其定址反轉清單中最後一個元素的下一個位置。|
|[emplace](#emplace)|將就地建構的元素插入清單的指定位置。|
|[emplace_back](#emplace_back)|將就地建構的元素加入至清單的結尾。|
|[emplace_front](#emplace_front)|將就地建構的元素加入至清單的開頭。|
|[empty](#empty)|測試清單是否為空的。|
|[end](#end)|傳回迭代器，其定址清單中最後一個元素的後接位置。|
|[erase](#erase)|從清單中的指定位置移除元素或某個元素範圍。|
|[front](#front)|傳回清單中第一個元素的參考。|
|[get_allocator](#get_allocator)|傳回用來建構清單的 `allocator` 物件複本。|
|[insert](#insert)|將某個元素或一些元素或某個元素範圍，插入清單的指定位置。|
|[max_size](#max_size)|傳回清單的最大長度。|
|[merge](#merge)|從引數清單中移除元素，並將其插入目標清單中，然後以遞增順序或其他指定的順序，排序新合併的元素集合。|
|[pop_back](#pop_back)|刪除清單結尾的項目。|
|[pop_front](#pop_front)|刪除清單開頭的元素。|
|[push_back](#push_back)|將元素加入至清單的結尾。|
|[push_front](#push_front)|將元素加入至清單的開頭。|
|[rbegin](#rbegin)|傳回迭代器，其定址反轉清單中的第一個元素。|
|[remove](#remove)|清除清單中符合指定之值的項目。|
|[remove_if](#remove_if)|從清單中清除符合指定述詞的元素。|
|[rend](#rend)|傳回迭代器，其定址反轉清單中最後一個元素的後接位置。|
|[resize](#resize)|指定清單的新大小。|
|[reverse](#reverse)|反轉項目在清單中出現的順序。|
|[size](#size)|傳回清單中項目的數目。|
|[sort](#sort)|將清單的元素以遞增順序或以其他順序關聯進行排序。|
|[splice](#splice)|從引數清單中移除元素，並將它們插入目標清單。|
|[swap](#swap)|交換兩個清單的項目。|
|[unique](#unique)|從清單移除相鄰的重複元素，或移除符合其他某些二元述詞的相鄰元素。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator=](#op_eq)|用另一個清單複本取代清單的元素。|

## <a name="requirements"></a>需求

**標頭**：\<list>

## <a name="allocator_type"></a> allocator_type

類型，表示清單物件的配置器類別。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>備註

`allocator_type` 範本參數同義*Allocator*。

### <a name="example"></a>範例

請參閱 [get_allocator](#get_allocator) 的範例。

## <a name="assign"></a> 指派

清除清單上的項目，並複製一組新的項目至目標清單。

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>參數

*第一個*\
複製來源的引數清單中，項目範圍的第一個項目的位置。

*最後一個*\
複製來源的引數清單中，項目範圍之外第一個項目的位置。

*計數*\
插入清單中項目的複本數目。

*val*\
插入清單中之項目的值。

*IList*\
initializer_list，包含要插入之項目。

### <a name="remarks"></a>備註

在清除目標清單中任何現有的項目之後，assign 從原始清單或從其他清單中將項目指定的範圍插入至目標清單，或是將指定之值的新項目複本插入到目標清單

### <a name="example"></a>範例

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a> 上一步

傳回清單的最後一個元素的參考。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>傳回值

清單的最後一個元素。 如果清單是空的，傳回值為未定義。

### <a name="remarks"></a>備註

如果 `back` 的傳回值已指派給 `const_reference`，則無法修改清單物件。 如果 `back` 的傳回值已指派給 `reference`，則可以修改清單物件。

使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空清單中的元素，將會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。

### <a name="example"></a>範例

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a> 開始

傳回迭代器，其定址清單中的第一個元素。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>傳回值

雙向迭代器，其定址清單中的第一個元素，或空清單之後的位置。

### <a name="remarks"></a>備註

如果傳回值`begin`指派給`const_iterator`，無法修改 list 物件中的項目。 如果傳回值`begin`指派給`iterator`，可以修改 list 物件中的項目。

### <a name="example"></a>範例

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a> cbegin

傳回**const**迭代器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

A **const**雙向存取迭代器指向第一個項目範圍或只是空白範圍結尾之外的位置 (空白範圍， `cbegin() == cend()`)。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮`Container`的可修改 (非**const**) 的任何一種支援的容器`begin()`和`cbegin()`。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a> cend

傳回 `const` 迭代器，為範圍中最後一個項目之外的位置定址。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

指向範圍結尾之外的 `const` 雙向存取迭代器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮`Container`的可修改 (非**const**) 的任何一種支援的容器`end()`和`cend()`。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="clear"></a> 清除

清除清單的所有元素。

```cpp
void clear();
```

### <a name="example"></a>範例

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a> const_iterator

一種類型，提供可讀取清單中任何 **const** 元素的雙向迭代器。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

類型 `const_iterator` 無法用來修改元素的值。

### <a name="example"></a>範例

請參閱 [back](#back) 的範例。

## <a name="const_pointer"></a> const_pointer

提供的指標**const**清單中的項目。

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

類型 `const_pointer` 無法用來修改元素的值。

在大部分情況下，應該使用 [iterator](#iterator) 存取 list 物件中的元素。

## <a name="const_reference"></a> const_reference

一種類型，提供對儲存在清單中以供讀取和執行 **const** 運算之 **const** 元素的參考。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>備註

類型 `const_reference` 無法用來修改元素的值。

### <a name="example"></a>範例

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a> const_reverse_iterator

一種類型，提供可讀取清單中任何 **const** 元素的雙向迭代器。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `const_reverse_iterator` 無法修改元素的值，且會用來逐一查看反轉的 list。

### <a name="example"></a>範例

請參閱 [rbegin](#rbegin) 的範例。

## <a name="crbegin"></a> crbegin

傳回 const 迭代器，其定址反轉清單中的第一個元素。

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 list 中的第一個元素 (或未反轉 `list` 中的作為最後一個元素的項目)。

### <a name="remarks"></a>備註

`crbegin` 是與反轉 list 搭配使用，就如同 [list::begin](#begin) 是與 `list` 搭配使用一樣。

有 `crbegin` 的傳回值時，無法修改 list 物件。 [list::rbegin](#rbegin) 可用來向後逐一查看清單。

### <a name="example"></a>範例

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a> crend

傳回 const 迭代器，其定址反轉清單中最後一個元素的下一個位置。

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>傳回值

常數反轉雙向迭代器，定址對象是反轉 [list](../standard-library/list-class.md) 中最後一個元素後面的位置 (未反轉 `list` 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`crend` 是與反轉 list 搭配使用，就如同 [list::end](#end) 是與 `list` 搭配使用一樣。

有 `crend` 的傳回值時，無法修改 `list` 物件。

`crend` 可以用來測試反轉迭代器是否已到達其 `list` 的結尾。

`crend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a> difference_type

帶正負號的整數類型，可以用來表示範圍 (介於迭代器所指的元素) 中清單的元素數。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 是透過容器的迭代器減去或遞增時會傳回的類型。 `difference_type` 通常用來代表迭代器 `first` 和 `last` 之間範圍 [ `first`, `last`) 內的元素數目，包括 `first` 所指的元素以及上限到 `last` 所指元素 (但不包含此元素) 的元素範圍。

請注意，儘管 `difference_type` 適用於符合輸入迭代器需求的所有迭代器，其中包括可反轉容器 (例如 set) 所支援之雙向迭代器的類別，但只有隨機存取容器 (例如 [vector 類別](../standard-library/vector-class.md)) 所提供的隨機存取迭代器，才支援迭代器之間的減法。

### <a name="example"></a>範例

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a> emplace

將就地建構的元素插入清單的指定位置。

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>參數

*其中*\
目標 [list](../standard-library/list-class.md) 中第一個元素的插入位置。

*val*\
加入至 `list` 結尾的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，`list` 會保持不變，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a> emplace_back

將就地建構的元素加入至清單的結尾。

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>參數

*val*\
新增到 [list](../standard-library/list-class.md) 結尾的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，`list` 會保持不變，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a> emplace_front

將就地建構的元素加入至清單的開頭。

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>參數

*val*\
新增到 [list](../standard-library/list-class.md) 開頭的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，`list` 會保持不變，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a> 空白

測試清單是否為空的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

如果清單是空的，便會傳回 **true**；如果清單不是空的，則傳回 **false**。

### <a name="example"></a>範例

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a> 結束

傳回迭代器，其定址清單中最後一個元素的後接位置。

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>傳回值

雙向迭代器，其定址清單中最後一個元素的後接位置。 如果清單是空的，則 `list::end == list::begin`。

### <a name="remarks"></a>備註

`end` 用來測試是否迭代器已到達其清單的結尾。

### <a name="example"></a>範例

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a> 清除

從清單中的指定位置移除元素或某個元素範圍。

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>參數

*其中*\
要從清單中移除之元素項目的位置。

*第一個*\
從清單中移除的第一個元素的位置。

*最後一個*\
從清單中移除的最後一個元素之後的位置。

### <a name="return-value"></a>傳回值

雙向迭代器，指定所有移除的元素之後的第一個剩餘元素；或者，如果沒有這類元素存在，則為清單結尾的指標。

### <a name="remarks"></a>備註

沒有發生重新配置，因此迭代器和參考只針對刪除的元素變成無效。

`erase` 絕不會擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a> 前端

傳回清單中第一個元素的參考。

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>傳回值

如果清單是空的，傳回為未定義。

### <a name="remarks"></a>備註

如果 `front` 的傳回值已指派給 `const_reference`，則無法修改清單物件。 如果 `front` 的傳回值已指派給 `reference`，則可以修改清單物件。

使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空清單中的元素，將會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。

### <a name="example"></a>範例

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a> get_allocator

傳回用來建構清單的配置器物件複本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>傳回值

清單使用的配置器。

### <a name="remarks"></a>備註

list 類別的配置器會指定此類別管理儲存體的方式。 C++ 標準程式庫容器類別隨附的預設配置器，足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。

### <a name="example"></a>範例

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a> 插入

將某個元素或一些元素或某個元素範圍，插入清單的指定位置。

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>參數

*其中*\
目標 list 中第一個元素插入的位置。

*val*\
插入清單中之項目的值。

*計數*\
插入清單中的元素數目。

*第一個*\
要複製之引數清單的元素範圍中，第一個元素的位置。

*最後一個*\
要複製之引數清單的元素範圍中，最後一個元素之後的位置。

### <a name="return-value"></a>傳回值

前兩個插入函式傳回的迭代器，指向新元素插入至清單的位置。

### <a name="example"></a>範例

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a> 迭代器

類型，提供可以讀取或修改清單中之任何元素的雙向迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>備註

型別`iterator`可用來修改元素的值。

### <a name="example"></a>範例

請參閱 [begin](#begin) 的範例。

## <a name="list"></a> 清單

建構特定大小的清單，或具有特定值之元素的清單，或具有特定配置器的清單，或是做為其他一些清單的所有或部分複本。

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>參數

*Al*\
搭配這個物件使用的配置器類別。

*計數*\
建構的清單中元素的數目。

*val*\
list 中元素的值。

*權限*\
list，其中有要複製的建構的 list。

*第一個*\
要複製的元素範圍中第一個元素的位置。

*最後一個*\
超出要複製之元素範圍的第一個元素的位置。

*IList*\
包含要複製之項目的 initializer_list。

### <a name="remarks"></a>備註

所有建構函式會儲存配置器物件 (*Al*) 並初始化 list。

[get_allocator](#get_allocator) 會傳回一份用來建構清單的配置器物件複本。

前兩個建構函式指定空的初始 list，第二個指定的配置器類型 (*Al*) 使用。

第三個建構函式會指定重複指定數字 (*計數*) 類別的預設值的項目`Type`。

第四個和第五個建構函式指定的重複 (*計數*) 值之項目的*Val*。

第六個建構函式會指定一份清單*右*。

第七個建構函式會移動清單*右*。

第八個建構函式使用 initializer_list 來指定元素。

下面兩個建構函式複製清單的範圍 `[First, Last)`。

沒有建構函式會執行任何暫時重新配置。

### <a name="example"></a>範例

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a> max_size

傳回清單的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

清單的最大可能長度。

### <a name="example"></a>範例

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a> 合併式

從引數清單中移除元素，並將其插入目標清單中，然後以遞增順序或其他指定的順序，排序新合併的元素集合。

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>參數

*權限*\
要與目標清單合併的引數清單。

*Comp*\
比較運算子，用來排序目標清單的元素。

### <a name="remarks"></a>備註

引數清單*右*會與目標清單合併。

引數和目標清單必須以相同的比較關聯排序，而結果序列會依此排序。 第一個成員函式的預設排序為遞增的順序。 第二個成員函式會施加使用者指定的比較作業*comp*類別的`Traits`。

### <a name="example"></a>範例

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="op_eq"></a> 運算子 =

用另一個清單複本取代清單的元素。

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>參數

*權限*\
要複製到 `list` 中的 [list](../standard-library/list-class.md)。

### <a name="remarks"></a>備註

在清除任何現有的項目，在之後`list`，運算子會複製或移動的內容*右*到`list`。

### <a name="example"></a>範例

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a> 指標

提供指向清單中項目的指標。

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>備註

型別`pointer`可用來修改元素的值。

在大部分情況下，應該使用 [iterator](#iterator) 存取 list 物件中的元素。

## <a name="pop_back"></a> pop_back

刪除清單結尾的項目。

```cpp
void pop_back();
```

### <a name="remarks"></a>備註

最後一個項目不能是空的。 `pop_back` 絕不會擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a> pop_front

刪除清單開頭的元素。

```cpp
void pop_front();
```

### <a name="remarks"></a>備註

第一個元素不能是空的。 `pop_front` 絕不會擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a> push_back

將元素加入至清單的結尾。

```cpp
void push_back(void push_back(Type&& val);
```

### <a name="parameters"></a>參數

*val*\
加入至 list 結尾的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，list 會保持不變，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a> push_front

將元素加入至清單的開頭。

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>參數

*val*\
加入至清單的開頭的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，list 會保持不變，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a> rbegin

傳回迭代器，為反轉清單中的第一個項目定址。

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>傳回值

反向雙向迭代器，為反轉清單中的第一個項目定址 (或為未反轉清單中的最後一個項目定址)。

### <a name="remarks"></a>備註

`rbegin` 是與反轉 list 搭配使用，就如同 [begin](#begin) 是與 list 搭配使用一樣。

如果 `rbegin` 的傳回值已指派給 `const_reverse_iterator`，則無法修改清單物件。 如果 `rbegin` 的傳回值已指派給 `reverse_iterator`，則可以修改清單物件。

`rbegin` 可用來向後逐一查看清單。

### <a name="example"></a>範例

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a> 參考

類型，提供儲存在清單中之元素的參考。

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>範例

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a> 移除

清除清單中符合指定之值的項目。

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>參數

*val*\
值，由項目持有時，會導致項目從清單移除。

### <a name="remarks"></a>備註

剩餘項目的順序不受影響。

### <a name="example"></a>範例

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a> remove_if

從清單中清除符合指定述詞的元素。

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>參數

*預測*\
一元述詞，如果元素符合此述詞，就會從清單中刪除該元素。

### <a name="example"></a>範例

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a> rend

傳回迭代器，定址對象是反轉 list 中最後一個元素後面的位置。

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反轉雙向迭代器，定址對象是反轉 list 中最後一個元素後面的位置 (未反轉 list 中第一個元素前面的位置)。

### <a name="remarks"></a>備註

`rend` 是與反轉 list 搭配使用，就如同 [end](#end) 是與 list 搭配使用一樣。

如果 `rend` 的傳回值已指派給 `const_reverse_iterator`，則無法修改清單物件。 如果 `rend` 的傳回值已指派給 `reverse_iterator`，則可以修改清單物件。

`rend` 可以用來測試反轉迭代器是否已到達其清單的結尾。

`rend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a> 調整大小

指定清單的新大小。

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>參數

*_Newsize*\
清單的新大小。

*val*\
如果新大小大於原始大小，便是要新增到清單中之新元素的值。 如果省略此值，就會為新元素指派類別的預設值。

### <a name="remarks"></a>備註

如果清單的大小小於所要求的大小 *_Newsize*，直到達到所要求的大小，將會新增到清單的項目。

如果清單的大小大於所要求的大小，會刪除最接近清單結尾的項目，直到清單達到的大小 *_Newsize*。

如果清單現在的大小與所要求的大小相同，則不會採取任何動作。

[size](#size) 會反映清單的目前大小。

### <a name="example"></a>範例

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a> 反向

反轉項目在清單中出現的順序。

```cpp
void reverse();
```

### <a name="example"></a>範例

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a> reverse_iterator

類型，提供可以讀取或修改反轉清單中之元素的雙向迭代器。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 用來逐一查看反轉的 list。

### <a name="example"></a>範例

請參閱 [rbegin](#rbegin) 的範例。

## <a name="size"></a> 大小

傳回清單中項目的數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

清單目前的長度。

### <a name="example"></a>範例

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a> size_type

計算清單中元素數目的類型。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>範例

請參閱 [size](#size) 的範例。

## <a name="sort"></a> 排序

將清單的項目以遞增順序或以其他使用者指定的順序排序。

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>參數

*Comp*\
用來排序連續元素的比較運算子。

### <a name="remarks"></a>備註

第一個成員函數預設會以遞增順序放置元素。

排序的項目，根據使用者指定的比較運算，成員範本函式*comp*類別的`Traits`。

### <a name="example"></a>範例

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a> splice

從來源清單移除項目，並將項目插入至目的地清單。

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>參數

*其中*\
目的地清單中的位置 (要在此位置之前插入)。

*Source*\
要插入至目的地清單的來源清單。

*Iter*\
要從來源清單插入的項目。

*第一個*\
要從來源清單插入的範圍中的第一個項目。

*最後一個*\
要從來源清單插入的範圍中的最後一個項目，這之後的第一個位置。

### <a name="remarks"></a>備註

第一對成員函式的來源清單中的所有項目插入至目的地清單所參考的位置之前*其中*和從來源清單移除所有項目。 (`&Source`不得等於`this`。)

第二對成員函式插入所參考的項目*Iter*所參考之目的地清單中的位置之前*何處*並移除*Iter*從來源清單。 (若 `Where == Iter || Where == ++Iter`，則不會產生任何變更)。

第三對成員函式插入所指定之範圍 [ `First`， `Last`) 所參考之目的地清單中的項目之前*其中*和從來源清單中移除該範圍的項目。 (如果`&Source == this`，範圍`[First, Last)`不能包含所指向的項目*其中*。)

如果範圍接合插入 `N` 個元素，而且 `&Source != this`，則會將類別為 [iterator](../standard-library/forward-list-class.md#iterator) 的物件遞增 `N` 次。

在所有情況中，迭代器、指標或關於接合的項目的參考都會保持有效，並會傳送至目的地容器。

### <a name="example"></a>範例

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a> 交換

交換兩個清單的項目。

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>參數

*權限*\
提供要交換之元素的清單或其項目要交換與清單的清單*左*。

*左邊*\
清單，其項目是利用清單來交換*右*。

### <a name="example"></a>範例

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a> 唯一

從清單移除相鄰的重複元素，或移除符合其他某些二元述詞的相鄰元素。

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*預測*\
供二元述詞用來比較連續元素。

### <a name="remarks"></a>備註

這個函式假設清單已排序，因此所有重複的元素都是相鄰的。 不相鄰的重複元素將不會被刪除。

第一個成員函式會移除比較為等於其前一元素的每個元素。

第二個成員函式會移除符合述詞函式的每個項目*pred*相較於其前一個項目。 您可以使用任何二元函式宣告的物件中\<功能 > 引數的標頭*pred*或建立您自己。

### <a name="example"></a>範例

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a> value_type

類型，表示儲存在清單中的資料類型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>備註

`value_type` 與範本參數 *Type* 同義。

### <a name="example"></a>範例

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```
