---
title: deque 類別
ms.date: 11/04/2016
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
ms.openlocfilehash: 1edcabf526d0f3aa2ba52ba3fd0fc656c5ae6b9c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838539"
---
# <a name="deque-class"></a>deque 類別

以線性排列方式排列指定類型的項目，並且像向量一樣允許快速隨機存取任何項目，可有效率地在容器背面插入和刪除。 不過，與向量不同的是，`deque` 類別也支援在此容器前面有效率的插入和刪除。

## <a name="syntax"></a>語法

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>參數

*類型*\
要存放在 deque 中的項目資料類型。

*分配器*\
代表預存配置器物件的類型，封裝 deque 之記憶體配置和解除配置的詳細資訊。 這個自**變數是選擇性 \<Type> **的，預設值是配置器。

## <a name="remarks"></a>備註

選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。 當任何專案的隨機存取是在高階，而且只需要在序列結尾處插入或刪除元素時，[向量](../standard-library/vector-class.md)應該是管理序列的慣用容器。 如果您非常需要在序列內的任何位置有效地插入和刪除項目 (定時)，則清單容器的效能會更優異。 在此序列中間的這類作業需要複製和指派項目，且和此序列中的項目數目成比例 (線性時間)。

當成員函式必須插入或清除 deque 的項目時，就會發生 deque 重新配置：

- 如果您將元素插入空的序列，或者將元素清除以保留空的序列，則 [begin](#begin) 和 [end](#end) 稍早所傳回的迭代器會變成無效。

- 如果將一個項目插入 deque 的第一個位置，則指定現有項目的所有迭代器 (而非參考) 都會變成無效。

- 如果將一個元素插入 deque 的結尾，則指定現有元素的 [end](#end) 和所有迭代器 (而非參考) 都會變成無效。

- 如果在 deque 前面清除了一個項目，則只有遭清除項目的迭代器和參考會變成無效。

- 如果從 deque 結尾清除了最後一個項目，則只有最後一個項目的迭代器和遭清除項目的參考會變成無效。

否則，插入或刪除一個項目會讓所有迭代器和參考失效。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[deque](#deque)|建構 `deque`。 提供數個用來以不同方式設定新內容的函式 `deque` ：空白、使用指定的空專案數載入、從另一個專案移動或複製的內容、 `deque` 使用反覆運算器複製或移動的內容，以及一個複製到時間的元素 `deque` `count` 。 有些建構函式可使用自訂的 `allocator` 來建立項目。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|類型，表示 `allocator` 物件的 `deque` 類別。|
|[const_iterator](#const_iterator)|一種類型，提供可以存取和讀取 as 中專案的隨機存取反覆運算器。 `deque`**`const`**|
|[const_pointer](#const_pointer)|類型，提供 `deque` 中的項目指標做為 `const.`。|
|[const_reference](#const_reference)|類型，提供在 `deque` 中供讀取和其他作業使用之項目做為 `const.` 的參考。|
|[const_reverse_iterator](#const_reverse_iterator)|一種類型，提供可以存取和讀取 as 中專案的隨機存取反覆運算器 `deque` **`const`** 。 會以反向檢視 deque。 如需詳細資訊，請參閱 [reverse_iterator 類別](../standard-library/reverse-iterator-class.md)。|
|[difference_type](#difference_type)|類型，提供兩個隨機存取迭代器的差異，這些迭代器參考相同 `deque` 中的項目。|
|[迭 代](#iterator)|類型，提供隨機存取迭代器，該迭代器可讀取或修改 `deque` 中的任何項目。|
|[指標](#pointer)|類型，其提供 `deque` 中項目的指標。|
|[reference](#reference)|類型，提供儲存在 `deque` 中之項目的參考。|
|[reverse_iterator](#reverse_iterator)|類型，提供隨機存取迭代器，該迭代器可讀取或修改 `deque` 中的項目。 會以反向順序檢視 deque。|
|[size_type](#size_type)|計算 `deque` 中項目數目的類型。|
|[value_type](#value_type)|類型，表示儲存在 `deque` 中的資料類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[assign](#assign)|清除 `deque` 中的項目，並複製新的項目序列至目標 `deque`。|
|[at](#at)|傳回 `deque` 中指定位置的項目參考。|
|[返回](#back)|傳回 `deque` 的最後一個項目的參考。|
|[開始](#begin)|傳回 `deque` 中對第一個項目定址的隨機存取迭代器。|
|[cbegin](#cbegin)|傳回 `deque` 中第一個項目的常數迭代器。|
|[cend](#cend)|傳回隨機存取 **`const`** 反覆運算器，其指向結尾的範圍之外 `deque` 。|
|[清楚](#clear)|清除 `deque` 的所有項目。|
|[crbegin](#crbegin)|傳回 `deque` 中以相反順序檢視之第一個項目的隨機存取常數迭代器。|
|[crend](#crend)|傳回 `deque` 中以相反順序檢視之第一個項目的隨機存取常數迭代器。|
|[emplace](#emplace)|將就地建構的項目插入 `deque` 的指定位置。|
|[emplace_back](#emplace_back)|將就地建構的項目加入 `deque` 的結尾。|
|[emplace_front](#emplace_front)|將就地建構的項目加入 `deque` 的開頭。|
|[empty](#empty)|**`true`** 如果 `deque` 包含零個元素，以及 **`false`** 包含一或多個元素，則傳回。|
|[結束](#end)|傳回指向 `deque` 結尾之外的隨機存取迭代器。|
|[erase](#erase)|從指定位置移除在 `deque` 中的項目或某個項目範圍。|
|[前面](#front)|傳回 `deque` 中第一個項目的參考。|
|[get_allocator](#get_allocator)|傳回用來建構 `allocator` 的 `deque` 物件複本。|
|[insert](#insert)|將一個項目、多個項目或一定範圍的項目在指定位置插入 `deque`。|
|[max_size](#max_size)|傳回 `deque` 的最大可能長度。|
|[pop_back](#pop_back)|清除 `deque` 結尾的項目。|
|[pop_front](#pop_front)|清除 `deque` 開頭的項目。|
|[push_back](#push_back)|將項目加入 `deque` 的結尾。|
|[push_front](#push_front)|將項目加入 `deque` 的開頭。|
|[rbegin](#rbegin)|傳回反轉的 `deque` 中第一個項目的隨機存取迭代器。|
|[rend](#rend)|傳回在反轉的 `deque` 中恰好指向最後一個項目之外的隨機存取迭代器。|
|[調整](#resize)|指定 `deque` 的新大小。|
|[shrink_to_fit](#shrink_to_fit)|捨棄多餘的容量。|
|[size](#size)|傳回 `deque` 中項目的數目。|
|[交換](#swap)|交換兩個 `deque` 的項目。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator&#91;&#93;](#op_at)|傳回在指定位置上 `deque` 項目的參考。|
|[運算子 =](#op_eq)|用另一個 `deque` 的複本取代 `deque` 的項目。|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

此類型代表 deque 物件的配置器類別。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>備註

`allocator_type` 與樣板參數 `Allocator` 同義。

### <a name="example"></a>範例

請參閱 [get_allocator](#get_allocator) 的範例。

## <a name="assign"></a><a name="assign"></a> 分配

清除 deque 中的元素，並複製一組新的元素至目標 deque。

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>參數

*第一*\
要從引數 deque 複製的元素範圍中，第一個元素的位置。

*最後*\
要從引數 deque 複製之元素範圍中，超出範圍的第一個元素位置。

*計數*\
插入 deque 的元素複本數目。

*瓦爾*\
插入 deque 的元素值。

*IList*\
插入 deque 的 initializer_list。

### <a name="remarks"></a>備註

將目標 deque 中任何現有的元素清除之後，`assign` 會從原始 deque 或從其他 deque 中將指定的元素範圍插入目標 deque ，或是將指定值的新元素複本插入到目標 deque。

### <a name="example"></a>範例

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;
}
```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a><a name="at"></a> 在

傳回 deque 中指定位置的元素參考。

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>參數

*Pos*\
deque 中要參考之元素的註標 (或位置編號)。

### <a name="return-value"></a>傳回值

如果 *pos* 大於 deque 的大小，則會擲回 `at` 例外狀況。

### <a name="return-value"></a>傳回值

如果 `at` 的傳回值已指派給 `const_reference`，則無法修改 deque 物件。 如果 `at` 的傳回值已指派給 `reference`，則可以修改 deque 物件。

### <a name="example"></a>範例

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> 返回

傳回 deque 的最後一個元素參考。

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>傳回值

deque 的最後一個元素。 如果 deque 是空的，傳回值為未定義。

### <a name="remarks"></a>備註

如果 `back` 的傳回值已指派給 `const_reference`，則無法修改 deque 物件。 如果 `back` 的傳回值已指派給 `reference`，則可以修改 deque 物件。

在您使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空 deque 中的元素，則會發生執行階段錯誤。  如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

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

## <a name="begin"></a><a name="begin"></a> 開始

傳回迭代器，定址對象是 deque 中的第一個元素。

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>傳回值

隨機存取迭代器，定址對象是 deque 中的第一個元素，或空 deque 之後的位置。

### <a name="remarks"></a>備註

如果 `begin` 的傳回值已指派給 `const_iterator`，則無法修改 deque 物件。 如果的傳回值已 `begin` 指派給 `iterator` ，則可以修改 deque 物件。

### <a name="example"></a>範例

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

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

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

傳回 **`const`** 反覆運算器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

**`const`** 隨機存取反覆運算器，指向範圍的第一個元素，或指向空白範圍結尾以外的位置 (空白範圍， `cbegin() == cend()`) 。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮 `Container` 將任何支援和的非) 容器 (不是可修改的 **`const`** `begin()` `cbegin()` 。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

傳回 **`const`** 反覆運算器，定址範圍中最後一個元素之外的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

指向範圍結尾之外的隨機存取迭代器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮 `Container` 將任何支援和的非) 容器 (不是可修改的 **`const`** `end()` `cend()` 。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="clear"></a><a name="clear"></a> 清楚

清除 deque 的所有元素。

```cpp
void clear();
```

### <a name="example"></a>範例

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

一種類型，提供可以存取和讀取 deque 中元素的隨機存取反覆運算器 **`const`** 。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

類型 `const_iterator` 無法用來修改元素的值。

### <a name="example"></a>範例

請參閱 [back](#back) 的範例。

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

提供 **`const`** deque 中元素的指標。

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

類型 `const_pointer` 無法用來修改元素的值。 [迭代器](#iterator)通常用來存取 deque 元素。

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

一種類型，提供 **`const`** 儲存在 deque 中以讀取和執行作業之專案的參考 **`const`** 。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>備註

類型 `const_reference` 無法用來修改元素的值。

### <a name="example"></a>範例

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

一種類型，提供可讀取 deque 中任何元素的隨機存取反覆運算器 **`const`** 。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `const_reverse_iterator` 無法修改元素的值，而是用來以反向逐一查看 deque。

### <a name="example"></a>範例

如需如何宣告及使用迭代器的範例，請參閱 [rbegin](#rbegin) 的範例。

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

將 const 迭代器傳回給反向 deque 中的第一個項目。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

const 反向隨機存取迭代器，其定址對象為反向 [deque](../standard-library/deque-class.md) 中的第一個元素，或未反向 `deque` 中的最後一個項目。

### <a name="remarks"></a>備註

有 `crbegin` 的傳回值時，無法修改 `deque` 物件。

### <a name="example"></a>範例

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a><a name="crend"></a> crend

傳回 const 迭代器，其定址對象為反向 deque 中最後一個元素的下一個位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

const 反向隨機存取迭代器，其定址對象為反向 [deque](../standard-library/deque-class.md) 中最後一個元素的下一個位置 (此位置優先於未反向 deque 中的第一個元素)。

### <a name="remarks"></a>備註

`crend` 搭配反向 `deque` 使用，就如同 [array::cend](../standard-library/array-class-stl.md#cend) 搭配 `deque` 使用。

有 `crend` 的傳回值時 (適當遞減)，無法修改 `deque` 物件。

`crend` 可以用來測試反向迭代器是否已到達其 deque 的結尾。

`crend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="deque"></a><a name="deque"></a> deque

建構特定大小的 deque、使用特定值的元素或特定配置器來建構 deque，或將其建構為其他一些 deque 的所有或部分複本。

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>參數

*鋁*\
搭配這個物件使用的配置器類別。

*計數*\
已建構 deque 中的元素數。

*瓦爾*\
已建構 deque 中的元素值。

*對*\
將已建構 deque 作為複本的 deque。

*第一*\
項目範圍中要複製的第一個項目位置。

*最後*\
項目範圍之外要複製的第一個項目位置。

*IList*\
要複製的 initializer_list。

### <a name="remarks"></a>備註

所有的函式都會將配置器物件儲存 (*Al*) ，並將 deque 初始化。

前兩個函式會指定空的初始 deque;第二個也會指定要使用的配置器類型 (`_Al`) 。

第三個建構函式會指定類別 `count` 之指定數目 (`Type`) 的項目重複預設值。

第四個和第五個的函式會指定值的 (*計數* 重複) 元素 `val` 。

第六個函式會指定 deque *許可權*的複本。

第七個和第八個建構函式會複製 deque 的範圍 `[First, Last)`。

第七個函式會移動 deque *許可權*。

第八個建構函式會複製 initializer_list 的內容。

沒有建構函式會執行任何暫時重新配置。

### <a name="example"></a>範例

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

此類型可提供兩個迭代器 (其參考相同 deque 內的元素) 之間的差異。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 也可以兩個指標之間的項目數來描述。

### <a name="example"></a>範例

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a><a name="emplace"></a> emplace

將就地建構的元素插入 deque 的指定位置。

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>參數

*_Where*\
第一個元素插入 [deque](../standard-library/deque-class.md) 的位置。

*瓦爾*\
插入 `deque` 的項目值。

### <a name="return-value"></a>傳回值

函式會傳回迭代器，此迭代器指向新元素在 deque 中的插入位置。

### <a name="remarks"></a>備註

任何插入作業都可能高度耗費資源，請參閱 `deque` 中有關 `deque` 效能的討論。

### <a name="example"></a>範例

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a><a name="emplace_back"></a> emplace_back

將就地建構的元素新增至 deque 的結尾。

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
新增至 [deque](../standard-library/deque-class.md) 結尾的元素。

### <a name="example"></a>範例

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

將就地建構的元素新增至 deque 的結尾。

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
加入至 [deque](../standard-library/deque-class.md)開頭的元素。

### <a name="example"></a>範例

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a><a name="empty"></a> 空

測試 deque 是否為空白。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 deque 是空的，則為。 **`false`** 如果 deque 不是空的，則為。

### <a name="example"></a>範例

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a><a name="end"></a> 結束

傳回迭代器，其定址對象為 deque 中最後一個元素的下一個位置。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>傳回值

隨機存取迭代器，其定址對象為 deque 中最後一個元素的下一個位置。 如果 deque 是空的，則 deque::end == deque::begin。

### <a name="remarks"></a>備註

`end` 用來測試反覆運算器是否已到達其 deque 的結尾。

### <a name="example"></a>範例

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
   *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> 擦 除

從指定位置移除 deque 中的元素或某個範圍內的元素。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>參數

*_Where*\
要從 deque 中移除之元素的位置。

*第一*\
從 deque 中移除之第一個元素的位置。

*最後*\
從 deque 中移除之最後一個元素以外的位置。

### <a name="return-value"></a>傳回值

隨機存取迭代器，指定所有移除的元素以外的第一個剩餘元素；或者，如果沒有這類元素存在，則為 deque 結尾的指標。

### <a name="remarks"></a>備註

`erase` 絕不會擲回例外狀況。

### <a name="example"></a>範例

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a><a name="front"></a> 前面

傳回 deque 中第一個元素的參考。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>傳回值

如果 deque 是空的，傳回值為未定義。

### <a name="remarks"></a>備註

如果 `front` 的傳回值已指派給 `const_reference`，則無法修改 deque 物件。 如果 `front` 的傳回值已指派給 `reference`，則可以修改 deque 物件。

在您使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空 deque 中的元素，則會發生執行階段錯誤。  如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

傳回一份用來建構 deque 的配置器物件複本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>傳回值

deque 使用的配置器。

### <a name="remarks"></a>備註

deque 類別的配置器會指定此類別管理儲存體的方式。 C++ 標準程式庫容器類別隨附的預設配置器即足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是進階 C++ 主題。

### <a name="example"></a>範例

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> 插入

將一或多個元素或範圍內的元素，插入 deque 的指定位置。

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>參數

*：*\
第一個元素插入 deque 的位置。

*瓦爾*\
插入 deque 的元素值。

*計數*\
插入 deque 的元素數目。

*第一*\
要複製之引數 deque 的元素範圍中，第一個元素的位置。

*最後*\
要複製之引數 deque 的元素範圍中，超出範圍的第一個元素位置。

*IList*\
要插入的 initializer_list 元素。

### <a name="return-value"></a>傳回值

前兩個 insert 函式會傳回迭代器，此迭代器指向新元素的 deque 插入位置。

### <a name="remarks"></a>備註

任何插入作業都可能相當耗費資源。

## <a name="iterator"></a><a name="iterator"></a> 迭 代

此類型提供可讀取或修改 deque 中任何元素的隨機存取迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>備註

類型 `iterator` 可以用來修改元素的值。

### <a name="example"></a>範例

請參閱 [begin](#begin) 的範例。

## <a name="max_size"></a><a name="max_size"></a> max_size

傳回 deque 的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

deque 的最大可能長度。

### <a name="example"></a>範例

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> operator []

傳回在指定位置上 deque 元素的參考。

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>參數

*Pos*\
要參考之 deque 元素的位置。

### <a name="return-value"></a>傳回值

元素的參考，引數中有指定它的位置。 如果指定的位置大於 deque 大小，則結果為未定義。

### <a name="remarks"></a>備註

如果 `operator[]` 的傳回值已指派給 `const_reference`，則無法修改 deque 物件。 如果 `operator[]` 的傳回值已指派給 `reference`，則可以修改 deque 物件。

當使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 編譯之後，如果您嘗試存取的元素超出 deque 界限，則會發生執行階段錯誤。  如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="operator"></a><a name="op_eq"></a> 運算子 =

將此 deque 的元素以另一個 deque 的元素取代。

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>參數

*對*\
此 deque 可提供新的內容。

### <a name="remarks"></a>備註

第一個覆寫 *會從指定的來源將*元素複製到這個 deque。 第二個覆寫會將元素從 *右邊*移至此 deque。

如果元素在運算子執行之前就已包含在這個 deque 中，即會遭到移除。

### <a name="example"></a>範例

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
}
```

## <a name="pointer"></a><a name="pointer"></a> 指標

提供指向 [deque](../standard-library/deque-class.md) 中的元素指標。

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>備註

類型 `pointer` 可以用來修改元素的值。 [迭代器](#iterator)通常用來存取 deque 元素。

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

刪除 deque 結尾的元素。

```cpp
void pop_back();
```

### <a name="remarks"></a>備註

最後一個項目不能是空的。 `pop_back` 絕不會擲回例外狀況。

### <a name="example"></a>範例

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

刪除 deque 開頭的元素。

```cpp
void pop_front();
```

### <a name="remarks"></a>備註

第一個元素不能是空的。 `pop_front` 絕不會擲回例外狀況。

### <a name="example"></a>範例

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> push_back

將元素新增至 deque 結尾。

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
新增至 deque 結尾的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，deque 會保持不變，並重新擲回例外狀況。

## <a name="push_front"></a><a name="push_front"></a> push_front

將元素新增至 deque 的開頭。

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
新增至 deque 開頭的元素。

### <a name="remarks"></a>備註

如果擲回例外狀況，deque 會保持不變，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
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

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

將迭代器傳回給反向 deque 中的第一個項目。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>傳回值

反向隨機存取迭代器，其定址對象為反向 deque 中的第一個項目，或未反向 deque 中的最後一個項目。

### <a name="remarks"></a>備註

`rbegin` 是與反向 deque 搭配使用，就如同 [begin](#begin) 是與 deque 搭配使用一樣。

如果 `rbegin` 的傳回值已指派給 `const_reverse_iterator`，則無法修改 deque 物件。 如果 `rbegin` 的傳回值已指派給 `reverse_iterator`，則可以修改 deque 物件。

`rbegin` 可用來向後逐一查看 deque。

### <a name="example"></a>範例

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
   *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a><a name="reference"></a> 參考

此類型可提供儲存在 deque 中之元素的參考。

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>範例

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a><a name="rend"></a> 撕裂

傳回迭代器，其定址對象是反向 deque 中最後一個元素的下一個位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反向隨機存取迭代器，其定址對象為反向 deque 中最後一個元素的下一個位置 (此位置優先於未反向 deque 中的第一個元素)。

### <a name="remarks"></a>備註

`rend` 是與反向 deque 搭配使用，就如同 [end](#end) 是與 deque 搭配使用一樣。

如果 `rend` 的傳回值已指派給 `const_reverse_iterator`，則無法修改 deque 物件。 如果 `rend` 的傳回值已指派給 `reverse_iterator`，則可以修改 deque 物件。

`rend` 可以用來測試反向迭代器是否已到達其 deque 的結尾。

`rend` 所傳回的值不應該取值。

### <a name="example"></a>範例

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
   *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> 調整

指定 deque 的新大小。

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>參數

*_Newsize*\
deque 的新大小。

*瓦爾*\
如果新大小超過原始大小，則會將新元素的值新增至 deque。 如果省略此值，就會為新元素指派類別的預設值。

### <a name="remarks"></a>備註

如果 deque 的大小小於所要求的大小， *_Newsize*，則會將元素新增至 deque，直到達到所要求的大小為止。

如果 deque 的大小大於所要求的大小，則會刪除最接近 deque 結尾的元素，直到 deque 達到 *_Newsize*的大小為止。

如果 deque 現在的大小與所要求的大小相同，則不會採取任何動作。

[size](#size) 會反映 deque 目前的大小。

### <a name="example"></a>範例

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

此類型提供的隨機存取迭代器，可讀取或修改反向 deque 中的元素。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 是用來反向逐一查看 deque。

### <a name="example"></a>範例

請參閱 rbegin 的範例。

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> shrink_to_fit

捨棄多餘的容量。

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>備註

目前並沒有最適合的方式，可判斷 `shrink_to_fit` 是否會減少 [deque](../standard-library/deque-class.md) 使用的儲存體。

### <a name="example"></a>範例

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a><a name="size"></a> 大小

傳回 deque 中的元素數目。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

deque 目前的長度。

### <a name="example"></a>範例

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

此類型可計算 deque 中元素的數目。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>範例

請參閱 [size](#size) 的範例。

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個 deque 的項目。

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
提供要交換元素的 deque，或要與 deque `left` 交換元素的 deque。

*離開*\
Deque，其元素要與 deque *許可權*交換。

### <a name="example"></a>範例

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a><a name="value_type"></a> value_type

此類型表示儲存在 deque 中的資料類型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>備註

`value_type` 與樣板參數 `Type` 同義。

### <a name="example"></a>範例

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
