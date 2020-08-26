---
title: vector 類別
description: 適用于 Microsoft c + + 標準程式庫實作為類別向量的參考。
ms.date: 02/07/2020
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
ms.openlocfilehash: 6cc8378fee72304bb909c3baacc305d446474bfa
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840033"
---
# <a name="vector-class"></a>vector 類別

C + + 標準程式庫向量類別是適用于順序容器的類別範本。 向量會以線性相片順序儲存指定類型的專案，並允許快速隨機存取任何元素。 當隨機存取效能是 premium 時，向量是慣用的序列容器。

## <a name="syntax"></a>語法

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>參數

*類型*\
要儲存在向量中的項目資料類型

*分配器*\
代表預存配置器物件的類型，封裝有關向量之記憶體配置和解除配置的詳細資料。 這個引數是選擇性的，而且預設值是 `allocator<Type>`。

## <a name="remarks"></a>備註

向量可在序列結尾處插入和刪除常數時間。 在向量中間插入或刪除項目需要線性時間。 在序列的開頭和結尾處插入和刪除時， [deque 類別](../standard-library/deque-class.md) 容器的速度較快。 在序列內的任何位置插入和刪除時， [list 類別](../standard-library/list-class.md) 容器的速度會更快。

當成員函式必須將向量物件中包含的序列增加到超過其目前的儲存容量時，就會發生向量重新配置。 其他的插入和清除可能會改變序列中的各種儲存空間位址。 在這些情況下，指向改變之序列位置的迭代器或參考會變成無效。 如果沒有發生重新配置，只有插入/刪除點之前的迭代器和參考仍有效。

[Vector \<bool> 類別](../standard-library/vector-bool-class.md)是類型元素之類別樣板向量的完整特製化 **`bool`** 。 它具有特製化所使用之基礎類型的配置器。

[Vector \<bool> 參考類別](../standard-library/vector-bool-class.md#reference_class)是一種嵌套類別，其物件可提供向量物件內 (單一位) 的元素參考 \<bool> 。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[向量](#vector)|建構特定大小、具有特定值項目或具有特定 `allocator` 的向量，或將向量建構為其他一些向量的複本。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|代表向量物件之 `allocator` 類別的類型。|
|[const_iterator](#const_iterator)|一種類型，提供可讀取向量中之元素的隨機存取反覆運算器 **`const`** 。|
|[const_pointer](#const_pointer)|一種類型，提供 **`const`** 向量中元素的指標。|
|[const_reference](#const_reference)|一種類型，提供 **`const`** 儲存在向量中之元素的參考。 它是用來讀取和執行 **`const`** 作業。|
|[const_reverse_iterator](#const_reverse_iterator)|一種類型，提供可讀取向量中任何元素的隨機存取反覆運算器 **`const`** 。|
|[difference_type](#difference_type)|提供向量中兩個項目位址之間差異的類型。|
|[迭 代](#iterator)|提供可讀取或修改向量中任何項目之隨機存取迭代器的類型。|
|[指標](#pointer)|提供向量中某個項目指標的類型。|
|[reference](#reference)|提供儲存在向量中之項目參考的類型。|
|[reverse_iterator](#reverse_iterator)|提供可讀取或修改反向向量中任何項目之隨機存取迭代器的類型。|
|[size_type](#size_type)|計算向量中項目數的類型。|
|[value_type](#value_type)|代表儲存在向量中之資料類型的類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[assign](#assign)|清除向量，並將指定的項目複製到空向量。|
|[at](#at)|傳回向量中指定位置的項目參考。|
|[返回](#back)|傳回向量的最後一個項目參考。|
|[開始](#begin)|傳回向量中第一個項目的隨機存取迭代器。|
|[能力](#capacity)|傳回向量可包含而不需要配置更多儲存空間的項目數。|
|[cbegin](#cbegin)|傳回向量中第一個項目的隨機存取常數迭代器。|
|[cend](#cend)|傳回隨機存取常數迭代器，指向向量結尾的後一個項目。|
|[crbegin](#crbegin)|將常數迭代器傳回至反向向量中的第一個項目。|
|[crend](#crend)|將常數迭代器傳回至反向向量的結尾。|
|[清楚](#clear)|清除向量的項目。|
|[data](#data)|傳回向量中第一個項目的指標。|
|[emplace](#emplace)|將就地建構的項目插入向量的指定位置。|
|[emplace_back](#emplace_back)|將就地建構的項目加入向量的結尾。|
|[empty](#empty)|測試向量容器是否空白。|
|[結束](#end)|傳回隨機存取迭代器，指向向量的結尾。|
|[erase](#erase)|從向量的指定位置移除一個項目或一定範圍的項目。|
|[前面](#front)|傳回向量中第一個項目的參考。|
|[get_allocator](#get_allocator)|將物件傳回至向量所使用的 `allocator` 類別。|
|[insert](#insert)|將就地建構的一個或多個項目插入向量的指定位置。|
|[max_size](#max_size)|傳回向量的最大長度。|
|[pop_back](#pop_back)|刪除向量結尾的元素。|
|[push_back](#push_back)|將項目加入向量的結尾。|
|[rbegin](#rbegin)|傳回反向向量中第一個項目的迭代器。|
|[rend](#rend)|將迭代器傳回至反向向量的結尾。|
|[儲備](#reserve)|為向量物件保留最小儲存空間長度。|
|[調整](#resize)|指定向量的新大小。|
|[shrink_to_fit](#shrink_to_fit)|捨棄多餘的容量。|
|[size](#size)|傳回向量中的項目數。|
|[交換](#swap)|交換兩個向量的項目。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator&#91;&#93;](#op_at)|傳回在指定位置上 vector 項目的參考。|
|[運算子 =](#op_eq)|以另一個向量的複本取代向量的項目。|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

代表向量物件之配置器類別的類型。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>備註

`allocator_type` 與樣板參數 `Allocator` 同義。

### <a name="example"></a>範例

如需使用 `allocator_type` 的範例，請參閱 [get_allocator](#get_allocator) 的範例。

## <a name="assign"></a><a name="assign"></a> 分配

清除向量，並將指定的項目複製到空向量。

```cpp
void assign(size_type count, const Type& value);
void assign(initializer_list<Type> init_list);

template <class InputIterator>
void assign(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>參數

*第一*\
項目範圍中要複製的第一個項目位置。

*最後*\
項目範圍之外要複製的第一個項目位置。

*count*\
插入向量的項目複本數目。

*value*\
插入向量之項目的值。

*init_list*\
包含要插入之項目的 initializer_list。

### <a name="remarks"></a>備註

首先， `assign` 清除向量中任何現有的元素。 然後，將 `assign` 原始向量中指定範圍的專案插入向量中，或將新指定之值元素的複本插入向量中。

### <a name="example"></a>範例

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}
```

## <a name="at"></a><a name="at"></a> 在

傳回向量中指定位置的項目參考。

```cpp
reference at(size_type position);

const_reference at(size_type position) const;
```

### <a name="parameters"></a>參數

*位置*\
向量中要參考之項目的註標或位置編號。

### <a name="return-value"></a>傳回值

引數中加上註標的項目參考。 如果 *位置* 大於向量的大小，則會擲回 `at` 例外狀況。

### <a name="remarks"></a>備註

如果的傳回值 `at` 已指派給 `const_reference` ，則無法修改向量物件。 如果 `at` 的傳回值指派給 `reference`，則可以修改向量物件。

### <a name="example"></a>範例

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> 返回

傳回向量的最後一個項目參考。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>傳回值

向量的最後一個項目。 如果向量是空的，則傳回值不明。

### <a name="remarks"></a>備註

如果的傳回值 `back` 已指派給 `const_reference` ，則無法修改向量物件。 如果 `back` 的傳回值指派給 `reference`，則可以修改向量物件。

在您使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空向量中的元素，則會發生執行階段錯誤。 如需詳細資訊，請參閱 [已檢查的反覆運算](../standard-library/checked-iterators.md)器。

### <a name="example"></a>範例

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a><a name="begin"></a> 開始

傳回向量中第一個項目的隨機存取迭代器。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>傳回值

隨機存取迭代器，定址對象是 `vector` 中的第一個元素，或空 `vector` 後的位置。 請一律比較傳回的值與 [vector：： end](#end) ，以確保它是有效的。

### <a name="remarks"></a>備註

如果的傳回值 `begin` 已指派給 [vector：： const_iterator](#const_iterator)，則 `vector` 無法修改物件。 如果 `begin` 的傳回值指派給 [vector::iterator](#iterator)，則可以修改 `vector` 物件。

### <a name="example"></a>範例

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a><a name="capacity"></a> 能力

傳回向量可包含而不需要配置更多儲存空間的項目數。

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>傳回值

目前配置給向量的儲存空間長度。

### <a name="remarks"></a>備註

如果配置足以容納的記憶體，成員函式 [resize](#resize) 會更有效率。 請使用成員函式 [reserve](#reserve) 指定配置的記憶體數量。

### <a name="example"></a>範例

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

傳回 **`const`** 反覆運算器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

**`const`** 隨機存取反覆運算器，指向範圍的第一個元素，或指向空白範圍結尾以外的位置 (空白範圍， `cbegin() == cend()`) 。

### <a name="remarks"></a>備註

如果傳回的值為 `cbegin` ，則無法修改範圍中的元素。

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

**`const`** 指向範圍結尾之外的隨機存取反覆運算器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮 `Container` 將任何支援和的非) 容器 (不是可修改的 **`const`** `end()` `cend()` 。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

傳回的值不應取值 `cend` 。 只使用它進行比較。

## <a name="clear"></a><a name="clear"></a> 清楚

清除向量的項目。

```cpp
void clear();
```

### <a name="example"></a>範例

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

一種類型，提供可讀取向量中之元素的隨機存取反覆運算器 **`const`** 。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>備註

型別 `const_iterator` 不能用來修改元素的值。

### <a name="example"></a>範例

如需使用 `const_iterator` 的範例，請參閱 [back](#back) 的範例。

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

一種類型，提供 **`const`** 向量中元素的指標。

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

型別 `const_pointer` 不能用來修改元素的值。

[迭代器](#iterator)通常可用來存取向量項目。

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

一種類型，提供 **`const`** 儲存在向量中之元素的參考。 它是用來讀取和執行 **`const`** 作業。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>備註

型別 `const_reference` 不能用來修改元素的值。

### <a name="example"></a>範例

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

一種類型，提供可讀取向量中任何元素的隨機存取反覆運算器 **`const`** 。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>備註

型別 `const_reverse_iterator` 無法修改元素的值，而是用來反向逐一查看向量。

### <a name="example"></a>範例

如需如何宣告及使用迭代器的範例，請參閱 [rbegin](#rbegin)。

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

將常數迭代器傳回至反向向量中的第一個項目。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

const 反向隨機存取迭代器，其定址反向[向量](../standard-library/vector-class.md)中的第一個項目，或定址未反向 `vector` 中的最後一個項目。

### <a name="remarks"></a>備註

如果傳回的值為 `crbegin` ，則 `vector` 無法修改物件。

### <a name="example"></a>範例

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a><a name="crend"></a> crend

傳回常數迭代器，為反向向量中最後一個項目的下一個位置定址。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

const 反向隨機存取迭代器，其定址反向[向量](../standard-library/vector-class.md)中最後一個元素的下一個位置 (此位置在未反向 `vector` 中優先於第一個元素)。

### <a name="remarks"></a>備註

`crend` 搭配反向 `vector` 使用，就如同 [vector::cend](#cend) 搭配 `vector` 使用。

若傳回值為 `crend` (適當遞減) ， `vector` 就無法修改物件。

`crend` 可以用來測試反轉迭代器是否已到達其 `vector` 的結尾。

傳回的值不應取值 `crend` 。 只使用它進行比較。

### <a name="example"></a>範例

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

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

## <a name="data"></a><a name="data"></a> 資料

傳回向量中第一個項目的指標。

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>傳回值

[向量](../standard-library/vector-class.md)中第一個項目的指標，或空的 `vector` 之後的位置指標。

### <a name="example"></a>範例

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1_ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_ptr = c1.data();
    *c1_ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1_ptr++)
    {
        cout << " " << *c1_ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

提供參考相同向量中項目之兩個迭代器間差異的類型。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>備註

`difference_type` 也可以描述為兩個指標之間的項目數，因為項目的指標包含其位址。

[迭代器](#iterator)通常可用來存取向量項目。

### <a name="example"></a>範例

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

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

將就地建構的項目插入向量的指定位置。

```cpp
template <class... Types>
iterator emplace(
    const_iterator position,
    Types&&... args);
```

### <a name="parameters"></a>參數

*位置*\
第一個項目插入[向量](../standard-library/vector-class.md)中的位置。

*參數*\
建構函式引數。 函式會根據所提供的引數推斷要叫用的建構函式多載。

### <a name="return-value"></a>傳回值

函式會傳回迭代器，指向新項目插入 `vector` 的位置。

### <a name="remarks"></a>備註

任何插入作業都可能很耗費資源，請參閱 [vector 類別](../standard-library/vector-class.md) 以取得效能的討論 `vector` 。

### <a name="example"></a>範例

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

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

將就地建構的項目加入向量的結尾。

```cpp
template <class... Types>
void emplace_back(Types&&... args);
```

### <a name="parameters"></a>參數

*參數*\
建構函式引數。 函式會根據所提供的引數推斷要叫用的建構函式多載。

### <a name="example"></a>範例

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}
```

## <a name="empty"></a><a name="empty"></a> 空

測試是否為空的向量。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果向量是空的，則為。 **`false`** 如果向量不是空的。

### <a name="example"></a>範例

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a><a name="end"></a> 結束

傳回超出結尾 (past-the-end) 迭代器。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>傳回值

向量的超出結尾迭代器。 如果向量是空的，則為 `vector::end() == vector::begin()` 。

### <a name="remarks"></a>備註

如果的傳回值 `end` 已指派給類型的變數 `const_iterator` ，則無法修改 vector 物件。 如果的傳回值 `end` 已指派給類型的變數 `iterator` ，則可以修改向量物件。

### <a name="example"></a>範例

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a><a name="erase"></a> 擦 除

從向量的指定位置移除一個項目或一定範圍的項目。

```cpp
iterator erase(
    const_iterator position);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>參數

*位置*\
要從向量中移除之項目的位置。

*第一*\
從向量中移除之第一個項目的位置。

*最後*\
從向量中移除的最後一個項目之後的位置。

### <a name="return-value"></a>傳回值

迭代器，指定任何移除的項目之後的第一個剩餘項目；如果沒有這個項目，則為向量結尾的指標。

### <a name="example"></a>範例

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a><a name="front"></a> 前面

傳回向量中第一個項目的參考。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>傳回值

向量物件中第一個項目的參考。 如果向量是空的，則傳回不明。

### <a name="remarks"></a>備註

如果的傳回值 `front` 已指派給 `const_reference` ，則無法修改向量物件。 如果 `front` 的傳回值指派給 **reference**，則可以修改向量物件。

在您使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 進行編譯之後，如果嘗試存取空向量中的元素，則會發生執行階段錯誤。 如需詳細資訊，請參閱 [已檢查的反覆運算](../standard-library/checked-iterators.md)器。

### <a name="example"></a>範例

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

傳回一份用來建構向量的配置器物件複本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>傳回值

向量所使用的配置器。

### <a name="remarks"></a>備註

供 vector 類別用於指定類別如何管理儲存的配置器。 C++ 標準程式庫容器類別隨附的預設配置器即足以滿足大多數程式設計需求。 撰寫和使用您自己的配置器類別是 advanced c + + 功能。

### <a name="example"></a>範例

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a><a name="insert"></a> 插入

將專案、數個元素或某個範圍的專案插入向量的指定位置。

```cpp
iterator insert(
    const_iterator position,
    const Type& value);

iterator insert(
    const_iterator position,
    Type&& value);

void insert(
    const_iterator position,
    size_type count,
    const Type& value);

template <class InputIterator>
void insert(
    const_iterator position,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>參數

*位置*\
第一個項目插入向量中的位置。

*value*\
插入向量之項目的值。

*count*\
插入向量的項目數。

*第一*\
要複製的元素範圍中第一個元素的位置。

*最後*\
超出要複製之元素範圍的第一個元素的位置。

### <a name="return-value"></a>傳回值

前兩個 `insert` 函式會傳回迭代器，指向新項目插入向量的位置。

### <a name="remarks"></a>備註

作為前置條件， *first* 和 *last* 都不能是反覆運算器進入向量，或行為未定義。 任何插入作業都可能很耗費資源，請參閱 [vector 類別](../standard-library/vector-class.md) 以取得效能的討論 `vector` 。

### <a name="example"></a>範例

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   const auto v2 = v1;
   v1.insert( v1.begin( )+1, v2.begin( )+2, v2.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
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
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a><a name="iterator"></a> 迭 代

提供可讀取或修改向量中任何項目之隨機存取迭代器的類型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>備註

類型 **iterator** 可用來修改元素的值。

### <a name="example"></a>範例

請參閱 [begin](#begin) 的範例。

## <a name="max_size"></a><a name="max_size"></a> max_size

傳回向量的最大長度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

向量的最大可能長度。

### <a name="example"></a>範例

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> operator []

傳回在指定位置上 vector 項目的參考。

```cpp
reference operator[](size_type position);

const_reference operator[](size_type position) const;
```

### <a name="parameters"></a>參數

*位置*\
vector 項目的位置。

### <a name="return-value"></a>傳回值

如果指定的位置大於或等於容器大小，則結果是未定義。

### <a name="remarks"></a>備註

如果的傳回值 `operator[]` 已指派給 `const_reference` ，則無法修改向量物件。 如果 `operator[]` 的傳回值已指派給參考，則可以修改向量物件。

當使用定義為 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 編譯之後，如果您嘗試存取的項目超出向量界限，則會發生執行階段錯誤。 如需詳細資訊，請參閱 [已檢查的反覆運算](../standard-library/checked-iterators.md)器。

### <a name="example"></a>範例

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> 運算子 =

以另一個向量的複本取代向量的項目。

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>參數

*對*\
複製到 `vector` 的[向量](../standard-library/vector-class.md)。

### <a name="remarks"></a>備註

清除中的任何現有元素之後 `vector` ，會 `operator=` 將 *右邊* 的內容複寫或移動到 `vector` 。

### <a name="example"></a>範例

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

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
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a> 指標

提供向量中某個項目指標的類型。

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>備註

類型 **pointer** 可用來修改元素的值。

### <a name="example"></a>範例

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

刪除向量結尾的元素。

```cpp
void pop_back();
```

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [vector::push_back()](#push_back)。

## <a name="push_back"></a><a name="push_back"></a> push_back

將元素加入至向量結尾。

```cpp
void push_back(const T& value);

void push_back(T&& value);
```

### <a name="parameters"></a>參數

*value*\
要指派給加入到向量結尾之元素的值。

### <a name="example"></a>範例

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

傳回反向向量中第一個項目的迭代器。

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>傳回值

反向隨機存取迭代器，其定址反向向量中的第一個項目，或定址未反向向量中的最後一個項目。

### <a name="remarks"></a>備註

如果的傳回值 `rbegin` 已指派給 `const_reverse_iterator` ，則無法修改向量物件。 如果 `rbegin` 的傳回值指派給 `reverse_iterator`，則可以修改向量物件。

### <a name="example"></a>範例

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a><a name="reference"></a> 參考

提供儲存在向量中之項目參考的類型。

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>範例

如需如何在向量類別中使用 **reference** 的範例，請參閱 [at](#at)。

## <a name="rend"></a><a name="rend"></a> 撕裂

傳回迭代器，為反向向量中最後一個項目的下一個位置定址。

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>傳回值

反向隨機存取迭代器，其定址反向向量中最後一個元素的下一個位置 (此位置在未反向向量中優先於第一個元素)。

### <a name="remarks"></a>備註

`rend` 搭配反向向量使用，就如同 [end](#end) 搭配向量使用。

如果的傳回值 `rend` 已指派給，則 `const_reverse_iterator` 無法修改向量物件。 如果 `rend` 的傳回值指派給 `reverse_iterator`，則可以修改向量物件。

`rend` 可以用來測試反轉迭代器是否已到達其陣列的結尾。

傳回的值不應取值 `rend` 。 只使用它進行比較。

### <a name="example"></a>範例

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

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

## <a name="reserve"></a><a name="reserve"></a> 儲備

為向量物件保留最小儲存空間長度，並在必要時配置空間。

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>參數

*count*\
配置給向量的最小儲存空間長度。

### <a name="example"></a>範例

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a><a name="resize"></a> 調整

指定向量的新大小。

```cpp
void resize(size_type new_size);
void resize(size_type new_size, Type value);
```

### <a name="parameters"></a>參數

*new_size*\
向量的新大小。

*value*\
如果新的大小大於原始大小，則已將新元素的初始化值加入至向量。 如果省略此值，則新的物件會使用其預設建構函式。

### <a name="remarks"></a>備註

如果容器的大小小於所要求的大小， *new_size*，則會 `resize` 將元素加入至向量，直到達到所要求的大小為止。 當容器的大小大於所要求的大小時， `resize` 會刪除最接近容器結尾的元素，直到達到 *new_size*的大小為止。 如果容器的目前大小與所要求的大小相同，則不會採取任何動作。

[size](#size) 會反映向量的目前大小。

### <a name="example"></a>範例

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }
    cout << endl;
}

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

提供可讀取或修改反向向量中任何項目之隨機存取迭代器的類型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>備註

類型 `reverse_iterator` 可用來反向逐一查看向量。

### <a name="example"></a>範例

請參閱 [rbegin](#rbegin) 的範例。

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> shrink_to_fit

捨棄多餘的容量。

```cpp
void shrink_to_fit();
```

### <a name="example"></a>範例

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a><a name="size"></a> 大小

傳回向量中的項目數。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

向量的目前長度。

### <a name="example"></a>範例

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

計算向量中項目數的類型。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>範例

請參閱 [capacity](#capacity) 的範例。

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個向量的項目。

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
提供要交換之元素的向量。 或者，其元素要與向量中的元素交換的*向量。*

*離開*\
向量，其元素要與向量 *右邊*的元素交換。

### <a name="example"></a>範例

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a><a name="value_type"></a> value_type

代表儲存在向量中之資料類型的類型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>備註

`value_type` 與樣板參數 `Type` 同義。

### <a name="example"></a>範例

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a><a name="vector"></a> 向量

結構向量。 多載會建立特定大小的向量，或具有特定值的元素。 或者，做為部分其他向量的所有或部分複本。 某些多載也可讓您指定要使用的配置器。

```cpp
vector();
explicit vector(const Allocator& allocator);
explicit vector(size_type count);
vector(size_type count, const Type& value);
vector(size_type count, const Type& value, const Allocator& allocator);

vector(const vector& source);
vector(vector&& source);
vector(initializer_list<Type> init_list, const Allocator& allocator);

template <class InputIterator>
vector(InputIterator first, InputIterator last);
template <class InputIterator>
vector(InputIterator first, InputIterator last, const Allocator& allocator);
```

### <a name="parameters"></a>參數

*分配器*\
搭配這個物件使用的配置器類別。 [get_allocator](#get_allocator) 會傳回物件的配置器類別。

*count*\
已建構向量中的項目數。

*value*\
已建構向量中的項目值。

*源*\
已建構向量為其複本的向量。

*第一*\
項目範圍中要複製的第一個項目位置。

*最後*\
項目範圍之外要複製的第一個項目位置。

*init_list*\
， `initializer_list` 包含要複製的元素。

### <a name="remarks"></a>備註

所有的函式都會將配置器物件 *儲存 (配置* 器) 並初始化向量。

前兩個建構函式會指定空的初始向量。 第二個函式會明確指定要使用的配置器 *類型 (配置* 器) 。

第三個函式會針對類別的預設值 (*count*) 的元素，指定重複的指定數目 `Type` 。

第四個和第五個函式會指定 *) 值元素*的 (*計數*重複。

第六個函式會指定向量 *來源*的複本。

第七個函式會移動向量 *來源*。

第八個建構函式使用 initializer_list 來指定元素。

第九個和第十個建構函式會複製向量的範圍 [`first`, `last`)。

### <a name="example"></a>範例

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}
```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
